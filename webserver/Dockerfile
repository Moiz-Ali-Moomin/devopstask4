FROM ubuntu
RUN echo "Asia/Kolkata" > /etc/timezone
RUN rm -f /etc/localtime
RUN dpkg-reconfigure -f noninteractive tzdata
RUN apt-get update \
 && apt-get install apache2 -y \
 && apt-get install apache2-utils -y \
 && apt-get clean
COPY ./index.html /var/www/html/
CMD ["apache2ctl", "-D", "FOREGROUND"]
EXPOSE 80