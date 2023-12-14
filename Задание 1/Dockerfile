FROM ubuntu:23.10
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y nginx
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
RUN rm -rf /var/www/*

RUN mkdir /var/www/my_project
RUN mkdir /var/www/my_project/img
COPY index.html /var/www/my_project
COPY vaha.jpg /var/www/my_project/img

RUN chmod -R 755 /var/www/my_project
RUN useradd -m ADA
RUN groupadd Laba
RUN usermod -aG Laba ADA
RUN chown -R ADA:Laba /var/www/my_project

RUN sed -i 's/\/var\/www\/html/\/var\/www\/my_project/g' /etc/nginx/sites-enabled/default

RUN sed -i 's/user [^;]\+;/user ADA;/g' /etc/nginx/nginx.conf

CMD ["nginx", "-g", "daemon off;"]