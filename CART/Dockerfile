FROM node:20.20.2-alpine3.23 AS builder 
WORKDIR /app 
COPY package.json .
COPY *.js .
RUN npm install 


FROM node:20.20.2-alpine3.23
WORKDIR /app
EXPOSE 8080
COPY --from=builder /app /app
RUN addgroup -s roboshop && adduser -s roboshop -G roboshop
RUN chowm -R roboshop:roboshop /app
USER roboshop 
CMD [ "node" ] 
ENTRYPOINT [ "server.js" ]


# FROM node:20
# WORKDIR /app
# COPY package.json .
# COPY server.js .
# RUN npm install 
# ENV REDIS_HOST="redis" \
#     CATALOGUE_HOST="catalogue" \
#     CATALOGUE_PORT="8080"
# CMD [ "node", "server.js" ]