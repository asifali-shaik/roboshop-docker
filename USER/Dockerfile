FROM node:20
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install
ENV MONGO="true" \
    MONGO_URL="mongodb://<MONGODB-SERVER-IP-ADDRESS>:27017/users" \
    REDIS_URL="redis://<REDIS-IP-ADDRESS>:6379"
CMD [ "nodejs","service.js" ]