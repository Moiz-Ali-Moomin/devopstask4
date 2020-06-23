FROM ubuntu
RUN apt-get update \
 && apt-get install apache2 -y \
 && apt-get install apache2-utils -y \
 && apt-get clean
COPY /root/devopstask3/webserver/index.html /var/www/html/
CMD ["apache2ctl", "-D", "FOREGROUND"]
EXPOSE 80