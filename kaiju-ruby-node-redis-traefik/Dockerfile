FROM redis:3.2 AS redis

FROM traefik:1.4.4 AS traefik

FROM cerner/kaiju-ruby-node:2.4.2-8.4.0

# Start redis installation
COPY --from=redis /usr/local/bin/redis-server /usr/local/bin/redis-server
COPY --from=redis /usr/local/bin/redis-cli /usr/local/bin/redis-cli

# Start traefik installation
COPY --from=traefik /traefik /usr/local/bin/

CMD ruby -v \
  && node -v \
  && npm -v \
  && redis-server -v \
  && traefik version
