FROM    wordpress:5.4.0-php7.4-apache

RUN     apt-get -y update && apt-get -y install msmtp && \
        echo '[mail function]' > /usr/local/etc/php/conf.d/mailsetting.ini && \
        echo 'sendmail_path = /usr/bin/msmtp -t -C /var/www/msmtp.conf' >> /usr/local/etc/php/conf.d/mailsetting.ini && \
        echo 'upload_max_filesize = 50M' >> /usr/local/etc/php/conf.d/uploadmax.ini && \
        echo 'post_max_size = 50M' >> /usr/local/etc/php/conf.d/uploadmax.ini && \
        touch /var/www/msmtp.log && \
        chmod 666 /var/www/msmtp.log && \
        echo 'defaults' > /var/www/msmtp.conf && \
        echo 'auth off' >> /var/www/msmtp.conf && \
        echo 'tls off' >> /var/www/msmtp.conf && \
        echo 'logfile /var/www/msmtp.log' >> /var/www/msmtp.conf && \
        echo '' >> /var/www/msmtp.conf && \
        echo 'account default' >> /var/www/msmtp.conf && \
        echo 'host '$(hostname -i|sed -e 's/\.[0-9]*$/.1/') >> /var/www/msmtp.conf && \
        echo 'port 25'  >> /var/www/msmtp.conf  >> /var/www/msmtp.conf && \
        echo 'from root@MAIL_DOMAIN'  >> /var/www/msmtp.conf && \
        sed -i 's/exec/\sed -i s\/MAIL_DOMAIN\/$MAIL_DOMAIN\/ \/var\/www\/msmtp.conf\nexec/g' /usr/local/bin/docker-entrypoint.sh && \
        echo "define('FS_METHOD', 'direct');" >> wp-config.php && \
        cat /usr/local/bin/docker-entrypoint.sh
