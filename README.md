# drupal7-sandbox
Drupal7 Vagrant/Ansible Sandbox

URL: drupal7.local
IP:  192.168.33.52
Ubuntu 14.04 Trusty Tahr

## Notes

- Admin user/pass is admin/admin
- Drush is used to setup the site, but no sample data has been added
    - Composer is used to install Druah 8.x
- create a 'localdev' folder inline with share dir to keep test files
 outside of GIT

 
## Install 

run vagrant up to provision

switch to sudo user 

    $ sudo su

download and install composer to /usr/local/bin/composer

    $ curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer creates=/usr/local/bin/composer
    
go back to vagrant user

    $ exit

install global drush module

    $ composer global require drush/drush:8.1.9

Add path to .profile

    $ PATH="$HOME/.config/composer/vendor/bin/:$PATH"

source terminal

    $ source .profile

run site install

    $ cd /vagrant_data/drupal7-sandbox
    $ drush site-install -y --db-url=mysql://drupal:drupal@localhost:3306/sandbox --account-pass=admin --site-name='Drupal 7 Sandbox'
