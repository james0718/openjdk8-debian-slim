FROM openjdk:8-jre-slim
MAINTAINER "advantech"<yao.kang@advantech.com.cn>
RUN apt-get update && apt-get install -y apache2 php7.3 php7.3-cli libapache2-mod-php7.3 php7.3-gd php7.3-ldap vim bash
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf
RUN rm -rf /var/www/html/* && mkdir -p /var/www/html
RUN sed -ri "s/upload_max_filesize = 2M/upload_max_filesize = 1000M/g" /etc/php/7.3/apache2/php.ini
RUN sed -ri "s/post_max_size = 8M/post_max_size = 1500M/g" /etc/php/7.3/apache2/php.ini
RUN mkdir -p /root/adv
RUN mkdir -p /root/adv/conf/
RUN mkdir -p /root/adv/models/
RUN mkdir -p /var/www/html/video_player
RUN mkdir -p /var/www/html/power_control
RUN mkdir -p /var/www/html/scan_barcode
RUN mkdir -p /var/www/html/light_control
ADD ./application.properties /root/adv/
ADD ./run.sh /root/adv/
COPY ./astore.jar /root/adv/
COPY ./solutionAppWeb/video_player/ /var/www/html/video_player
COPY ./solutionAppWeb/power_control/ /var/www/html/power_control
COPY ./solutionAppWeb/scan_barcode/ /var/www/html/scan_barcode
COPY ./solutionAppWeb/light_control/ /var/www/html/light_control
EXPOSE 80
ENV LANG='en_US.UTF-8'
ENV LANGUAGE='en_US:en'
CMD java -version
