FROM ubuntu
RUN DEBIAN_FRONTEND="noninteractive"
RUN apt-get update \
 && apt-get install tzdata -y \
 && apt-get install apache2 -y \
 && apt-get install apache2-utils -y \
 && apt-get clean
COPY ./index.html /var/www/html/
CMD ["apache2ctl", "-D", "FOREGROUND"]
EXPOSE 80
