FROM nginx

RUN rm /usr/share/nginx/html/index.html

RUN apt-get update &&  apt-get install -y wget && rm -rf /var/lib/apt/lists/*
RUN wget https://github.com/szasza576/azplayground/raw/master/nginx/girl/index.html -P /usr/share/nginx/html/
RUN apt-get remove -y wget && apt autoremove -y

EXPOSE 80
