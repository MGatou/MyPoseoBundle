MyPoseoBundle
=========================

[![SensioLabsInsight](https://insight.sensiolabs.com/projects/0306c6a7-d7c4-4614-ae25-092137c8e4f7/small.png)](https://insight.sensiolabs.com/projects/0306c6a7-d7c4-4614-ae25-092137c8e4f7)

[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/tristanbes/MyPoseoBundle/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/tristanbes/MyPoseoBundle/?branch=master)

Description:
--------------

This bundle provides a way to communicate with [MyPoseo](http://fr.myposeo.com/) webservices inside your Symfony2 application.

For now, only the _[Search API](http://fr.myposeo.com/nos-api/api-search/)_  has been wired. If you need more, PR are welcome.

The Search API allows you to get the position of an URL by keyword(s) among other features.

Installation:
--------------

Add tristanbes/my-poseo-bundle to your composer.json:
``` bash
php composer.phar require "tristanbes/my-poseo-bundle": "2.*"
```

Register the bundle in the kernel:

``` php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Tristanbes\MyPoseoBundle\MyPoseoBundle()
    );
}
```

How to use it:
--------------
You can configure the bundle with:

``` yml
my_poseo:
    api:
        key: "YOUR_API_KEY"
        cache_service_id: ~
        http_client: 'name_of_your_http_adapter'
        type:
            search:
                base_url: "http://api.myposeo.com/m/apiv2"
```

Your API key can be found on [this page](http://account.myposeo.com/account/configuration/api).

**Be careful, the given API key is already url encoded !** You need to decode it since guzzle re-encode automatically all parameters

Choose HTTP client
------------------
MyPoseoBundle 2.0 is no longer coupled to Guzzle3. Thanks to [Httplug](http://docs.php-http.org/en/latest/index.html) you can now use any
library to transport HTTP messages. You can rely on [discovery](http://docs.php-http.org/en/latest/discovery.html) to automatically
find an installed client or you can provide a client service name to the configuration (see [HttplugBundle](https://github.com/php-http/HttplugBundle)). 

