FROM node:8.9.2 AS node

FROM ruby:2.4.2
# Start Node installation
RUN groupadd --gid 1000 node \
  && useradd --uid 1000 --gid node --shell /bin/bash --create-home node

COPY --from=node /usr/local/bin/. /usr/local/bin/
COPY --from=node /usr/local/include/. /usr/local/include/
COPY --from=node /usr/local/lib/. /usr/local/lib/
COPY --from=node /usr/local/share/. /usr/local/share/

RUN npm config set unsafe-perm true -g
RUN npm install foreman -g

CMD ruby -v \
  && node -v \
  && npm -v
