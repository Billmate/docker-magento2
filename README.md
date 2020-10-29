# Docker image for Magento 2

This is based upon the repo [Docker Magento 2](https://github.com/rhinos-dubai/docker-magento2/).

## Installation

For more information about the [setup](https://github.com/rhinos-dubai/docker-magento2/blob/master/README.md)

The easiest way to start Magento 2 with MySQL is using [Docker Compose](https://docs.docker.com/compose/). Just clone this repo and run following command in the root directory. The default `docker-compose.yml` uses MySQL and phpMyAdmin.

~~~
$ docker-compose up -d
~~~

For admin username and password, please refer to the file `env`. You can also change the file `env` to update those configurations. Below are the default configurations.

~~~
MYSQL_HOST=db
MYSQL_ROOT_PASSWORD=myrootpassword
MYSQL_USER=magento
MYSQL_PASSWORD=magento
MYSQL_DATABASE=magento

MAGENTO_LANGUAGE=en_GB
MAGENTO_TIMEZONE=Pacific/Auckland
MAGENTO_DEFAULT_CURRENCY=NZD
MAGENTO_URL=http://local.magento
MAGENTO_BACKEND_FRONTNAME=admin
MAGENTO_USE_SECURE=0
MAGENTO_BASE_URL_SECURE=0
MAGENTO_USE_SECURE_ADMIN=0

MAGENTO_ADMIN_FIRSTNAME=Admin
MAGENTO_ADMIN_LASTNAME=MyStore
MAGENTO_ADMIN_EMAIL=amdin@example.com
MAGENTO_ADMIN_USERNAME=admin
MAGENTO_ADMIN_PASSWORD=magentorocks1
~~~

After starting the container, you'll see the setup page of Magento 2. You can use the script `install-magento` to quickly install Magento 2. The installation script uses the variables in the `env` file.

For more information about how to install on the [Docker setup instead](https://magento.stackexchange.com/questions/268094/how-to-setup-development-environment-for-magento-2-with-docker)

### Install Magento 

~~~
$ docker exec -it <container_name> install-magento
~~~

or just use the bin commands 

~~~
bin/cli install-magento
~~~

### Sample data

~~~
$ docker exec -it <container_name> install-sampledata
~~~

or just use the bin commands 

~~~
bin/cli install-sampledata
~~~

### Create a DNS host entry for the site:

~~~
echo "127.0.0.1 local.magento" | sudo tee -a /etc/hosts
~~~

### URL(s)

To access the frontend:
~~~
local.magento
~~~

To access the admin part:
~~~
local.magento/admin
~~~

**User:** admin
**Password:** magentorocks1

### Working with Billmate Checkout Magento 2 Module

First of all clone the [repo](https://github.com/Billmate/magento-2-billmate-checkout) down to the path:
~~~
src/app/code
~~~

From the Docker will sync all the files. 

Next step is then to follow the [installation instructions of the Module](https://github.com/Billmate/magento-2-billmate-checkout/blob/master/README.md#code-package).

You are now ready to start testing/development! 

## Magento commands cli 
you can run all mangeto CLi from this bin 

~~~
bin/magento
bin/magento cache:clean 
bin/magento config:show 
bin/magento sampledata:remove
~~~