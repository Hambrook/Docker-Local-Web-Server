#Docker Local Web Server

###Nginx or Apache? PHP 7 or 5? How about every permutation at once?

This is a set of containers that let you host multiple websites with different server configurations. Choose between Nginx or Apache, PHP7 or PHP5. There's also MySQL and phpMyAdmin in there too.

##Requirements

You need Docker and Docker Compose. These installation instructions differ depending on your platform, but can be found [here for Docker](https://docs.docker.com/engine/installation/) and [here for Docker Compose](https://docs.docker.com/compose/install/).

##Installation and Configuration

* Clone this repo (`git clone https://github.com/Hambrook/Docker-Local-Web-Server.git`)
* Then enter the directory and open the `docker-compose.yml` file. Update the "/data" paths to your local web root.
* Open up your terminal, navigate to the directory containing the `docker-compose.yml` file and run `sudo docker-compose up -d`

##Configuring Vhosts

There are 4 vhosts already configured (though you'll have to add entries to your hosts file):

* localhost-n5 = Nginx, PHP5
* localhost-n7 = Nginx, PHP7
* localhost-a5 = Apache, PHP5
* localhost-a7 = Apache, PHP7

To create a new website, just copy either one of the files in `nginx/vhosts/` that matches what you're setting up (eg localhost-n7 is Nginx with PHP7), rename and update it to match the hostname you're setting up.

Creating a new Apache website also involves creating an Apache vhost. Go into either `php5-apache/vhosts/` or `php7-apache/vhosts/` and create your vhost there.

Restart the servers by running `sudo docker-compose up -d` and your new sites should work.

##Database
The MySQl instance uses a username/password of root/root. All containers have access to the MySQL container via `mysql:3306`. The host can also access this same mysql instance via `localhost:3306`.

You can also use phpMyAdmin via http://localhost:1234/ and logging in with mysql/root/root.

##Installed Modules
A number of modules are already installed, and this list may expand.

###PHP7

* bcMath
* mbstring
* mcrypt
* mysqli

###PHP5

* bz2
* curl
* gd
* iconv
* imap
* mbstring
* mysqli
* pdo_mysql

###Apache

* rewrite

##FAQ
###Why?
Because I need to develop for modern servers while also maintaining legacy systems. I did have each configuration as a separate Docker Composer config so I could stop the Nginx/PHP7 server and start the Apache/PHP5 one, but this is easier.

###Does data get lost when the containers are stopped or rebuilt?
Your website files and database will be retained, but any logs will be lost. Feel free to pipe them to specific outputs if you wish.

##Feedback
Tell me if you loved it. Tell me if you hated it. Tell me if you used it and thought "meh". I'm keen to hear your feedback.

##Contributing
Feel free to fork this project and submit pull requests, or even just request features via the issue tracker. Please be descriptive with pull requests and match the existing code style.

##Roadmap
* Add MariaDB
* Add xDebug
* Add GD/Imagick for PHP7
* Make it easier to customise web roots
* Update to use one Apache container that references the PHP FPM containers
* Rename this package to something better
* _If you have an idea, [let me know](https://github.com/Hambrook/Docker-Local-Web-Server/issues)._

##License
Copyright © 2016 Rick Hambrook

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.