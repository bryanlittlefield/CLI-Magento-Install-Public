CLI-Magento-Install-Public
==========================
###Use this to install Magento entirely from the command line

####Setup Database
```php
mysql -u root -p 
CREATE DATABASE [database name];
SHOW DATABASES;
```

####Setup Database User
```php
GRANT ALL PRIVILEGES
ON [database name].*
TO '[database user]'@'localhost' IDENTIFIED BY '[password]';
FLUSH PRIVILEGES;
```
####Install Script
```php
wget http://www.magentocommerce.com/downloads/assets/1.7.0.2/magento-1.7.0.2.tar.gz
tar -zxvf magento-1.7.0.2.tar.gz 
mv magento/* magento/.htaccess . 
chmod -R o+w media var 
chmod o+w app/etc
rm -rf magento/ magento-1.7.0.2.tar.gz
php install.php -- \
--license_agreement_accepted "yes" \
--locale "en_US" \
--timezone "America/Los_Angeles" \
--default_currency "USD" \
--db_host "DB_HOST" \
--db_name "DB_NAME" \
--db_user "DB_USER" \
--db_pass "DB_PASS" \
--url "SITE_URL" \
--use_rewrites "yes" \
--skip_url_validation "yes"
--use_secure "no" \
--secure_base_url "" \
--use_secure_admin "no" \
--admin_firstname "FIRST_NAME" \
--admin_lastname "LAST_NAME" \
--admin_email "EMAIL_ADDRESS" \
--admin_username "USERNAME" \
--admin_password "PASSWORD" \;
find . -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;
```

