---
title: "PHP"
weight: 13
---

An C extension for PHP. Gives access to commands in PHP code to connect to SiriDB Server and query/insert.

### Installation

#### MacOS and Linux

Make sure you have `libsiridb` and `libqpack` insatalled on your system.
Make sure you have `phpize` available as command

Run:
```
phpize
./configure
make
sudo make install
```

Don't forget to enable the extension via the php.ini file

### Quick usage

When installed, you are able to using the following in your php code.
To connect to a SiriDB server use:
```

$siridb_con = siridb_connect('127.0.0.1', 9000, 'iris', 'siri', 'testdata_1');
if (!$siridb_con) {
    print("Cannot connect with siridb");
}
```

When you want to query something use:
```
$result = siridb_query($siridb_con, "select * from 'serie_name'");
echo $result; //json
```

When you want to insert points use:
```
$result = siridb_insert($siridb_con, array(
    "test_serie" => array(
        array(1582189879, 1.00003),
        array(1582189880, 1.00004)
    ),
    "test_serie2" => array(
        array(1582189879, 1.00003),
        array(1582189880, 1.00004)
    )
));
```

When you want to close the connection, use:
```
siridb_close($siridb_con);
```

### More info

A more complete description of the PHP-connector can be found via the link below.

- https://github.com/SiriDB/php-siridblib#readme
