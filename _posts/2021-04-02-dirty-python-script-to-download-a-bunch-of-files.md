It's widely known that Python is perfect (among other things) for writing a one-off disposable scripts for doing dirty tasks.

Today I found myself in need of downloading a bunch of files (sever hundreds) from the internet and saving them locally. I had a two columns table in google docs which I copy-pasted into a `txt` file (column delimiter turned into a `\t` symbol).

Instead of doing it manually, I chose to write a short script. 

In its entirety (including parsing command line args, logging setup), the script turned out to be 32 lines long and it illustrates the following concepts:

- handling command line args
- setting up and using built-in logging
- line-wise reading of the file
- some string operations (split, trim, replace)
- downloading stuff (using `urllib` package)

This is the script:

```python
import logging
import sys
import urllib.request
from time import sleep

[download_list, target_dir] = sys.argv[1:]
logging.basicConfig(format='%(levelname)s:%(message)s', level=logging.DEBUG)

logging.info("download_list: " + download_list)
logging.info("target_dir: " + target_dir)


def convert_doc_name_to_file_name(doc_name: str) -> str:
    res = doc_name.strip()
    res = res.replace(' ', '_')
    return res + ".docx"


def download(link: str, target_path: str):
    logging.info(f"downloading {link} to {target_path}")
    urllib.request.urlretrieve(link, target_path)
    logging.info("done")


with open(download_list) as f:
    lines = list(f)

for line in lines:
    [download_link, doc_name] = line.split("\t")
    file_name = convert_doc_name_to_file_name(doc_name)
    download(download_link, target_dir + '/' + file_name)
    sleep(1)  # not to overwhelm the server too much
```


