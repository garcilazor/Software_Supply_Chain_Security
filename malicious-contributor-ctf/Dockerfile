FROM ubuntu:22.10

WORKDIR /app

COPY requirements.txt /app

RUN set -xe \
    && apt-get update -y \
    && apt-get install -y python3-pip\
    && apt-get install git -y\
    && apt-get install vim -y
RUN pip3 install --upgrade pip
RUN pip3 install -r requirements.txt

RUN rm requirements.txt
