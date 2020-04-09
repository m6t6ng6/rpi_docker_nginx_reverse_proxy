primer archivo

--o--

CONFIG

HTML webportal paths:

web1:
- /home/pi/git/docker/docker-share/html1/production:/usr/share/nginx/html:ro    # PRODUCTION
#- /home/pi/git/docker/docker-share/html1/maintenance:/usr/share/nginx/html:ro  # MAINTENANCE

web2:
- /home/pi/git/docker/docker-share/html2/production:/usr/share/nginx/html:ro    # PRODUCTION
#- /home/pi/git/docker/docker-share/html2/maintenance:/usr/share/nginx/html:ro  # MAINTENANCE

webN:

- /home/pi/git/docker/docker-share/htmlN/production:/usr/share/nginx/html:ro    # PRODUCTION
#- /home/pi/git/docker/docker-share/htmlN/maintenance:/usr/share/nginx/html:ro  # MAINTENANCE

DOCKER-COMPOSE volumes:

www1:
  image: nginx
  restart: always
  expose:
    - "80"
  volumes:
    # siempre elegir una de las dos (maintenance o production)
    - /home/pi/git/docker/docker-share/html1/production:/usr/share/nginx/html:ro    # PRODUCCION
      #- /home/pi/git/docker/docker-share/html1/maintenance:/usr/share/nginx/html:ro   # MAINTENANCE
  environment:
    - VIRTUAL_HOST=ecommerce-dev
    - LETSENCRYPT_HOST=ecommerce-dev
    - LETSENCRYPT_EMAIL=ferna2909@hotmail.com

www2:
  image: nginx
  restart: always
  expose:
    - "80"
  volumes:
    - /home/pi/git/docker/docker-share/html1/production:/usr/share/nginx/html:ro    # PRODUCCION
      #- /home/pi/git/docker/docker-share/html1/maintenance:/usr/share/nginx/html:ro   # MAINTENANCE
  environment:
    - VIRTUAL_HOST=dolarhoy-dev
    - LETSENCRYPT_HOST=dolarhoy-dev
    - LETSENCRYPT_EMAIL=ferna2909@hotmail.com

wwwN:
  image: nginx
  restart: always
  expose:
    - "80"
  volumes:
    - /home/pi/git/docker/docker-share/htmlN/production:/usr/share/nginx/html:ro    # PRODUCCION
      #- /home/pi/git/docker/docker-share/htmlN/maintenance:/usr/share/nginx/html:ro   # MAINTENANCE
  environment:
    - VIRTUAL_HOST=<dns_hostname_N>
    - LETSENCRYPT_HOST=<dns_hostname_N>
    - LETSENCRYPT_EMAIL=<contacto>
