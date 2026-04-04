FROM node:20
WORKDIR /app
COPY package.json .
COPY server.js .
ENV REDIS_HOST="redi" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
CMD [ "node", "server.js" ]