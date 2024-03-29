Dashboard - Socialize US - Install
========================

Welcome to our school group project. 
Here is how to install the dashboard that will allow you to list/add/edit and delete each of our events.

The events will display on a specific view, reachable on another repository -- https://github.com/mdrick/socialize-us. The separation in two repository beetween our main site and this dashboard has for main purpose to keep clear, and to help you, install this without any issue.

Install
--------------
Clone the repository, then go to the project cd MyPathToTheFolder and do
```
composer install

php bin/console doctrine:database:create

php bin/console assets:install --symlink

php bin/console doctrine:schema:update --dump-sql --force

php bin/console server:run
```
If you want to create an admin user directly from the CLI :
```
php bin/console fos:user:create adminuser --super-admin
```
Otherwhise just go to ```/register```
Finnaly, in order to access to the dashboard simply add ```/dashboard``` in the url parameter. 


Note that in order to work properly it will create a database. Make sure your mandatory information to connect SQL server are correct in the parameters.yml
```
SocializeUS/
├── app/
│   ├── config
│   │   ├── parameters.yml
```
Here is a sample of what this file should look like with a connexion in localhost
```
parameters:
    database_host: localhost # 127.0.0.1
    database_port: null
    database_name: socializeus # the name that will have your database
    database_user: root
    database_password: root 
    mailer_transport: smtp
    mailer_host: 127.0.0.1
    mailer_user: null
    mailer_password: null
    secret: # your personal token 

```

What is included
--------------

```
SocializeUS/
├── app/
│   ├── config
│   │   ├── config_dev.yml
│   │   ├── config_prod.yml
│   │   ├── config_test.yml
│   │   ├── config.yml
│   │   ├── parameters.yml
│   │   ├── parameters.yml.dist
│   │   ├── routing_dev.yml
│   │   ├── routing.yml
│   │   ├── security.yml
│   │   ├── services.yml
│   ├── ressources
│   │   ├── views
├── AppCache.php
├── AppKernel.php
├── autoload.php
├── bin/
│   ├── console
│   └── symfony_requirements
└── src/
    ├── AppBundle
    │   │   ├── AppBundle.php
    │   │   ├── Controller
    │   │   ├── Entity
    │   │   │   │   ├── User.php
    │   │   │   │   ├── Event.php
└── tests
└── var
└── vendor
└── web
```

Route
--------------
```
  ----------------------------------- ---------- -------- ------ ------------------------------------------------
  Name                                Method     Scheme   Host   Path
 ----------------------------------- ---------- -------- ------ ------------------------------------------------
  _wdt                                ANY        ANY      ANY    /_wdt/{token}
  _profiler_home                      ANY        ANY      ANY    /_profiler/
  _profiler_search                    ANY        ANY      ANY    /_profiler/search
  _profiler_search_bar                ANY        ANY      ANY    /_profiler/search_bar
  _profiler_info                      ANY        ANY      ANY    /_profiler/info/{about}
  _profiler_phpinfo                   ANY        ANY      ANY    /_profiler/phpinfo
  _profiler_search_results            ANY        ANY      ANY    /_profiler/{token}/search/results
  _profiler_open_file                 ANY        ANY      ANY    /_profiler/open
  _profiler                           ANY        ANY      ANY    /_profiler/{token}
  _profiler_router                    ANY        ANY      ANY    /_profiler/{token}/router
  _profiler_exception                 ANY        ANY      ANY    /_profiler/{token}/exception
  _profiler_exception_css             ANY        ANY      ANY    /_profiler/{token}/exception.css
  _twig_error_test                    ANY        ANY      ANY    /_error/{code}.{_format}
  homepage                            ANY        ANY      ANY    /
  fos_user_security_login             GET|POST   ANY      ANY    /login
  fos_user_security_check             POST       ANY      ANY    /login_check
  fos_user_security_logout            GET|POST   ANY      ANY    /logout
  fos_user_profile_show               GET        ANY      ANY    /profile/
  fos_user_profile_edit               GET|POST   ANY      ANY    /profile/edit
  fos_user_registration_register      GET|POST   ANY      ANY    /register/
  fos_user_registration_check_email   GET        ANY      ANY    /register/check-email
  fos_user_registration_confirm       GET        ANY      ANY    /register/confirm/{token}
  fos_user_registration_confirmed     GET        ANY      ANY    /register/confirmed
  fos_user_resetting_request          GET        ANY      ANY    /resetting/request
  fos_user_resetting_send_email       POST       ANY      ANY    /resetting/send-email
  fos_user_resetting_check_email      GET        ANY      ANY    /resetting/check-email
  fos_user_resetting_reset            GET|POST   ANY      ANY    /resetting/reset/{token}
  fos_user_change_password            GET|POST   ANY      ANY    /profile/change-password
  easyadmin                           ANY        ANY      ANY    /dashboard/
  admin                               ANY        ANY      ANY    /dashboard/
  liip_imagine_filter_runtime         GET        ANY      ANY    /media/cache/resolve/{filter}/rc/{hash}/{path}
  liip_imagine_filter                 GET        ANY      ANY    /media/cache/resolve/{filter}/{path}
 ----------------------------------- ---------- -------- ------ ------------------------------------------------
```
