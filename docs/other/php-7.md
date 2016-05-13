Drupal VM fully supports PHP 7, but currently defaults to 5.6 in order to maximize compatibility with older Drupal 6 and 7 sites. Soon, Drupal VM will change its defaults to install PHP 7.x instead of 5.x, but until then, follow the instructions below to use PHP 7.

## Ubuntu 14.04

Ondřej Surý's PPA for PHP 7.0 is included with Drupal VM, and you can make the following changes/additions to `config.yml` to use it:

```yaml
php_version: "7.0"
php_packages:
  - php7.0-common
  - php7.0-cli
  - php7.0-dev
  - php7.0-fpm
  - libpcre3-dev
  - php7.0-gd
  - php7.0-curl
  - php7.0-imap
  - php7.0-json
  - php7.0-opcache
  - php7.0-xml
  - php7.0-mbstring
php_mysql_package: php7.0-mysql
php_fpm_daemon: php7.0-fpm
php_conf_paths:
  - /etc/php/7.0/fpm
  - /etc/php/7.0/apache2
  - /etc/php/7.0/cli
php_extension_conf_paths:
  - /etc/php/7.0/fpm/conf.d
  - /etc/php/7.0/apache2/conf.d
  - /etc/php/7.0/cli/conf.d
php_fpm_pool_conf_path: "/etc/php/7.0/fpm/pool.d/www.conf"
```

Also, comment out `xhprof`, `redis` and `memcached` from the `installed_extras` list, as these extensions are not yet supported for PHP 7 (as of late 2015).

You can also build from source using the same/included `geerlingguy.php` Ansible role, but that process is a bit more involved and for power users comfortable with the process.

## RedHat/CentOS 7

Remi's RPM repository is included with Drupal VM, and you can make the following changes to use it to install PHP 7:

  1. Make sure you've followed the directions for switching to CentOS 7 in the [use a different base OS](base-os.md) guide.
  2. Change `php_version` inside `config.yml` to `"7.0"`.
  3. Comment out `xhprof`, `xdebug`, `redis` and `memcached` from the `installed_extras` list, as these extensions are not yet supported for PHP 7 (as of early 2016).
