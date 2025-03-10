[![Logo](https://seepossible.github.io/docs/assets/gitbook/images/apple-touch-icon-precomposed-152.png)](https://seepossible.github.io/docs)

## Common code and commands for genetal use.

Log

```php
# core

error_log(print_r($queryString, 1)."\n", 3,BP."/var/log/test.log");

$writer = new \Zend_Log_Writer_Stream(BP . '/var/log/test.log');
$logger = new \Zend_Log();
$logger->addWriter($writer);
$logger->info(__FILE__."::".__LINE__);

# Default magento

# Place logs in var/log/debug.log 
$logger = \Magento\Framework\App\ObjectManager::getInstance()->get(\Psr\Log\LoggerInterface::class);
$logger->info('Price');
$logger->log(100,print_r($items->getData(),true));

```

PHP debugging

```php

ini_set('display_errors', 1);
ini_set('display_startup_errors', 1);
ini_set('memory_limit', -1);
error_reporting(E_ALL);

```

MySql commands to export and import db

```bash
 mysqldump -u magento2_user -p magento2_db | gzip > magento2_db-20201110.sql.gz
 gunzip < magento2_db-20201110.sql.gz | mysql -u root -p db1
```

Findout running port on mac os

```bash
sudo lsof -i -P | grep LISTEN | grep :$PORT
lsof -i :9000
```

Findout the config value 

```bash
mage  config:show  "web/secure/base_url"
```

Generate i18n file for specific module.

```bash
mage i18n:collect-phrases -o vendor/seepossible/spmodule-book-appointment/i18n/en_US.csv vendor/seepossible/spmodule-book-appointment
```

Core magento installation

```bash
mage setup:install --base-url="https://magento-latest.px.seepossible.link/" --db-host="127.0.0.1" --db-name="magento_latest" --db-user="root" --db-password="rootroot" --admin-firstname="Bhavesh" --admin-lastname="Prajapati" --admin-email="bhavesh@seepossible.com" --admin-user="admin" --admin-password="admin123" --language="en_US" --currency="USD" --timezone="America/Chicago" --use-rewrites="1" --backend-frontname="admin"
```

get firebear module after replace vendor directory

```bash
composer2 require firebear/configurableproducts:1.5.3-alpha.4 --ignore-platform-reqs
```

Install specific php version on mac using brew

```bash
brew tap shivammathur/php
brew install shivammathur/extensions/mcrypt@7.4
brew install mcrypt@7.4
brew services restart php@7.4
brew services restart nginx
```

Magento 2 direcory vise permission

```bash
find . -type f -exec chmod 644 {} \;
find app/code/ -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;
find ./var -type d -exec chmod 777 {} \;
find ./pub/media -type d -exec chmod 777 {} \;
find ./pub/static -type d -exec chmod 777 {} \;
chmod 777 ./app/etc
chmod 644 ./app/etc/*.xml
```

Usefull code for js debugging

```javascript
# debug js

var getStackTrace = function() {
  var obj = {};
  Error.captureStackTrace(obj, getStackTrace);
  return obj.stack;
};
console.log(getStackTrace());

-----------------
# jq set attribute value
elem.setAttribute( name, value + "" );

-----------------
# get object method list
function getMethods(object) {
    var methodList = [];
    for (var property in object) {
        if (typeof object[property] === 'function') {
            methodList.push(property);
        }
    }
    return methodList;
}

-----------------
# reload customer data
require([
    'jquery',
    'Magento_Customer/js/customer-data'
], function ($, customerData) {
  customerData.reload(['gtm']);
  var data = customerData.get('gtm');
  console.log(data());
});
-----------------

# debug knockout
require('ko').contextFor($0);

-----------------
# magento file uploader uses dispersion param

window.matchMedia('(min-width: 768px)')

-----------------
# timer
var myCustomTimerFlag=1,hour=0,minute=0,second=0,count=0;
function myCustomTimer(){
if(myCustomTimerFlag){count++;
if(count==100){second++;count=0;}
if(second==60){minute++;second=0;}
if(minute==60){hour++;minute=0;second=0;}
let hrString=hour,minString=minute,secString=second,countString=count;
if(hour<10){hrString="0"+hrString;}
if(minute<10){minString="0"+minString;}
if(second<10){secString="0"+secString;}
if(count<10){countString="0"+countString;}
console.log(minString+":"+secString+":"+countString);
setTimeout(myCustomTimer,10);}}myCustomTimer();
myCustomTimerFlag=0
```
