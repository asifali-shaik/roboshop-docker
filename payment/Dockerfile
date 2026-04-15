# im using a alpine image so it does not have any build dependencies so we are going to install python dependencies 
# we have to install some requried dependenices we are using alpine base image so ..build-base linux-headers pcre-dev 

FROM python:3.9.25-alpine3.22 AS builder
WORKDIR /app
RUN apk add --no-cache build-base linux-headers pcre-dev
COPY requirements.txt .
RUN RUN pip3 install --prefix=/install -r requirements.txt


FROM python:3.9.25-alpine3.22
EXPOSE 8080
WORKDIR /app
RUN apk add --no-cache pcre
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
RUN chown -R roboshop:roboshop /app
COPY --from=builder /install /usr/local
COPY --chown=roboshop:roboshop payment.ini *.py requirements.txt /app/
USER roboshop
CMD [ "uwsgi", "--ini" ,"payment.ini"]










# FROM python:3.9
# EXPOSE 8080
# WORKDIR /app
# COPY payment.ini .
# COPY *.py .
# COPY requirements.txt .
# RUN pip3 install -r requirements.txt
# CMD [ "uwsgi", "--ini" ,"payment.ini"]