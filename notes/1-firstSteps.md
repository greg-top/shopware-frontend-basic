# Installation
- one file installer - https://en-community.shopware.com/_detail_1993.html?_ga=2.47173479.1124345779.1541502916-515785597.1539944978
- github - https://github.com/shopware/shopware

# Configuring Shopware for Development
- set cache configuration <br><br>
Configuration > Cache/Performance:
    - set development mode (in **Start** tab)
    - deactive HTTP cache (in **Settings** tab)
- set configuration for theme development <br><br>
Configuration > Theme manager > settings button:
    - disable compression of js, CSS
    - enable CSS source mapping
    - set 'Disable compiler caching' to yes
    - enable force snippet reload
- file configuration <br><br>
file: /config.php <br>
<pre>
<?php return [
  'db' => 
  [
    'host' => 'localhost',
    'port' => '3306',
    'username' => 'root',
    'password' => 'root',
    'dbname' => 'shopware',
  ],

    'front' => [
        'throwExceptions' => true,
        'showException' => true
    ],

    'phpsettings' => [
        'display_errors' => 1
    ],

    'template' => [
        'forceCompile' => true
    ],

    'httpcache' => [
        'debug' => true
    ]
];
</pre>
example configuration settings: https://developers.shopware.com/developers-guide/shopware-config/#example-development-config

# IDE configuration (PHPStorm)
- install symfony plugin / enable plugin / restart IDE
- install shopware plugin / enable plugin / restart IDE

source: https://plugins.jetbrains.com/plugin/7410-shopware-plugin