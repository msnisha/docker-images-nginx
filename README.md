This is an nginx created on alphine OS exclusively for Raspberry Pi. The entire image size is 5 MB.

<b>Sample docker compose file for using this image.</b>

<code>
<pre>
version: '3.8'

services:
  my_server:
    image: msnisha/pi-nginx:latest
    deploy:
      replicas: 1
    volumes:
      - ./app:/var/www
      - logs:/var/log/nginx
      - ./conf:/etc/nginx/conf.d
    depends_on:
      - "php"
    networks:
      - ninthuweb
      - overlay
  php:
    image: php7:01.01
    volumes:
      - ./app:/var/www
    expose:
      - "9000"
    networks:
      - overlay

networks:
  overlay:
</pre>
</code>


<b>Sample without php</b>
<code>
<pre>
version: '3.8'

services:
  demo_server:
    image: msnisha/pi-nginx:latest
    deploy:
      replicas: 1
    volumes:
      - ./web:/var/www
      - logs:/var/log/nginx
      - ./conf:/etc/nginx/conf.d
    networks:
      - overlay

networks:
  overlay:
</pre>
</code>

<h2>Questions?</h2>
If you have any questions or issues please raise in the github repository at <a href="https://github.com/msnisha/docker-images-nginx">https://github.com/msnisha/docker-images-nginx</a>
