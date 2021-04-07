Today I needed to choose a way to serialize some data to be stored in Redis. Being in PHP realm (7.4, to be precise), I naturally had 2 obvious options - built-in serialization or `json_encode`.

The choise was not so obvious which is better so I set up a quick benchmark (code below).

The results are as follows:

```
serialize 0.68451189994812
unserialize 0.55576705932617
json_encode 0.31118392944336
json_decode 1.0347230434418
```

So what does it mean? Json functions are quicker to serialize (more than twice as quick) but are, roughly, twice as slow to deserialize the array.

Well, in my case, the anticipated frequency of serializations by far exceeds the one of deserializations, so I go with `json_encode`/`json_decode`.

In a more balanced or unknown workload, the winner would be less obvious though.

That's it, hope it helps someone.

The code used to obtain those figures:

```php
<?php

$bigArray = [];
$size = 20;

foreach (range(0, $size) as $i) {
    foreach (range(0, $size) as $j) {
        foreach (range(0, $size) as $k) {
            $bigArray[$i][$j][$k] = rand(0, 999);
        }

    }
}

function measure(Callable $callable, string $description) {
    $start_time = microtime(true);
    foreach (range(0, 1000) as $i) {
        $callable();
    }
    $end_time = microtime(true);

    print (PHP_EOL . $description . ' ' . ($end_time - $start_time));
}

$jsonOfBigArray = json_encode($bigArray);
$serializedBigArray = serialize($bigArray);

measure (function() use ($bigArray) {
    serialize($bigArray);
}, "serialize");

measure (function() use ($serializedBigArray) {
    unserialize($serializedBigArray);
}, "unserialize");


measure (function() use ($bigArray) {
    json_encode($bigArray);
}, "json_encode");

measure (function() use ($jsonOfBigArray) {
    json_decode($jsonOfBigArray, true);
}, "json_decode");
```