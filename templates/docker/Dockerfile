ARG NGINX_VERSION
FROM nginx:${NGINX_VERSION}

ARG TZ
ENV TZ=${TZ}

ARG APP_BASE_PATH=/

COPY dist/ /usr/share/nginx/html
COPY nginx.conf.template /tmp/nginx.conf.template
RUN envsubst '$APP_BASE_PATH' < /tmp/nginx.conf.template > /etc/nginx/conf.d/default.conf

EXPOSE 80

HEALTHCHECK --interval=30s --timeout=3s \
  CMD wget -qO- http://localhost/health || exit 1
