# Use Ubuntu (proviously Google Cloud SDK) container as the base image
FROM ubuntu:20.04

# Specify the maintainer of the container image
MAINTAINER Caspar "cchilds@pdx.edu"

# Copy the contents of the current directory into the container directory /app
COPY . /app

# Set the working directory of the container to /app
WORKDIR /app

# Install the Python packages specified by requirements.txt into the container
RUN apt-get update -y \
        && apt-get install -y python3-pip git vim python3.8-venv

RUN python3 -m venv venv \
        && venv/bin/pip install -r requirements.txt

EXPOSE 80

# Set the parameters to the program
CMD ["venv/bin/python", "app.py"]

