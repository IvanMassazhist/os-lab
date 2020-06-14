FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p ivanevstigneev.com/img && \
    chmod -R 754 /var/www/ivanevstigneev.com/ && \
    useradd ivan && groupadd evstigneev && usermod -aG evstigneev ivan && \
    chown -R ivan:evstigneev /var/www/ivanevstigneev.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/ivanevstigneev.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user ivan/g' /etc/nginx/nginx.conf
ADD index.html /var/www/ivanevstigneev.com/
ADD img.jpg /var/www/ivanevstigneev.com/img/
CMD ["nginx", "-g", "daemon off;"]
