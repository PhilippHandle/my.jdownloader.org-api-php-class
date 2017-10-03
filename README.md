Copyright (c) 2014 Anatoliy Kultenko "tofik".
Modified by Dominik Schwarzbauer "R3DST0RM".

A PHP wrapper class for My.JDownloader.org API.

# Improvements

This API is now able to queue packages to the download list.

New method "moveToDownloadList":

```php
<?php
    require_once 'myjdapi_class.php';

    $jd = new MYJDAPI( "EMAIL", "PASSWORD", "DEVICENAME");

    // get all packages in queue
    $packages = $jd->queryPackages();
    // get json from response
    $packagesEncoded = json_decode($packages);

    // iterate over every package and queue it using it's UUID
    for ($i = 0; $i < count($packagesEncoded->{"data"}); $i++){
        $jd->moveToDownloadList((float)($packagesEncoded->{"data"}[$i])->{"uuid"});
    }
?>
```

Many more improvements to come...

# Initial usage based on "tofik" version

Using my.jdownloader.org-api-php-class

First, you need JDownloader 2 Beta installed on your PC or other hardware,
visit http://jdownloader.org/download/offline.

Setup JDownloader for my.jdownloader.org in Settings/My.JDownloader.

If you already registered at my.jdownloader.org than simply fill fields
Username/Email, Password and Device Name, otherwise press button "Go to My.JDownloader.org"
and complete registration.

Now you can initialize the class

```php
<?php
    require_once 'myjdapi_class.php';

    $j = new MYJDAPI();
?>
```

Connect to my.jdownloader.org

```php
<?php
    require_once 'myjdapi_class.php';

    $j = new MYJDAPI();
    $j -> connect( "EMAIL", "PASSWORD");
    $j -> setDeviceName("YOUR_DEVICE_NAME");
?>
```

or use this method to initialize the class

```php
<?php
    require_once 'myjdapi_class.php';

    $j = new MYJDAPI( "EMAIL", "PASSWORD", "YOUR_DEVICE_NAME");
?>
```

Available methods:  connect, reconnect, disconnect, enumerateDevices,
getDirectConnectionInfos, callAction, addLinks, queryLinks and more maybe later.

Add links to jdownloader and start it

```php
<?php
    require_once 'myjdapi_class.php';

    $j = new MYJDAPI( "EMAIL", "PASSWORD", "YOUR_DEVICE_NAME");
    $j -> addLinks("LINKS", "PACKAGE_NAME");
?>
```

```php
<?php
    require_once 'myjdapi_class.php';

    $j = new MYJDAPI( "EMAIL", "PASSWORD", "YOUR_DEVICE_NAME");
    $j -> queryLinks();
?>
```
Copyright (c) 2014 Anatoliy Kultenko "tofik".

Released under the BSD License, see http://opensource.org/licenses/BSD-3-Clause
