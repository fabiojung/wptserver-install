$ sudo yum update

$ sudo vi /etc/security/limits.conf

	from repo/configs-rhel/system/limits.conf

$ sudo vi /usr/lib/sysctl.d/00-system.conf

	from repo/configs-rhel/system/00-system.conf

$ sudo reboot


$ sudo subscription-manager repos --enable rhel-7-server-extras-rpms  
$ sudo subscription-manager repos --enable rhel-7-server-optional-rpms  
$ sudo subscription-manager repos --enable rhel-server-rhscl-7-rpms  

$ sudo yum install git screen rh-nginx18 zip unzip curl ImageMagick libjpeg-turbo-utils psmisc rh-php73-php-fpm rh-php73-php-pecl-apcu rh-php73-php-pdo rh-php73-php-common rh-php73-php-gd rh-php73-php-zip rh-php73-php-mbstring rh-php73-php-xml  

$ sudo yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm  
$ sudo yum install https://download1.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm  
$ sudo yum install ffmpeg beanstalkd perl-Image-ExifTool  

$ sudo useradd www  
$ sudo chown -R www:www /var/www  

$ sudo su - www  
$ cd /var/www  

$ git clone --branch=rhel7 https://github.com/fabiojung/wptserver-install.git  
$ git clone --branch=prod https://github.com/fabiojung/webpagetest.git  
$ mkdir -p /var/www/webpagetest/www/tmp  

$ exit 

$ sudo chcon -Rt httpd_sys_content_rw_t /var/www/webpagetest/www

$ sudo vi /etc/fstab

	from repo/configs-rhel/system/fstab

$sudo mount -a


$ sudo vi /etc/default/beanstalkd

	from repo/configs-rhel/default/beanstalkd


$ sudo systemctl enable beanstalkd.service  
$ sudo systemctl start beanstalkd  

$ sudo vi /etc/opt/rh/rh-php73/php.ini 

	from repo/configs-rhel/php/php.ini

$ sudo vi /etc/opt/rh/rh-php73/php-fpm.d/www.conf 

	from repo/configs-rhel/php/pool.www.conf


#### the PHP-FPM config might need some adusts 

$ sudo systemctl enable rh-php73-php-fpm.service  
$ sudo systemctl start rh-php73-php-fpm  


$ sudo vi /etc/opt/rh/rh-nginx18/nginx/fastcgi.conf

	from repo/configs-rhel/nginx/fastcgi.conf

$ sudo vi /etc/opt/rh/rh-nginx18/nginx/fastcgi_params  
$ sudo vi /etc/opt/rh/rh-nginx18/nginx/nginx.conf  
$ sudo vi /etc/opt/rh/rh-nginx18/nginx/sites-enabled/sites.default  


$ sudo systemctl enable rh-nginx18-nginx.service  
$ sudo systemctl start rh-nginx18-nginx  
