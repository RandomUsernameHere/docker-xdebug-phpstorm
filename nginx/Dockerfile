FROM nginx:1.17.9-alpine

ARG UID
ARG GID

RUN addgroup -g $GID -S web-app \
  && adduser -u $UID -S -G web-app web-app
