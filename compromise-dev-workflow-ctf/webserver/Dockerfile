FROM python:3.13.0b1-slim as base

# Setup env
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONFAULTHANDLER 1

# Install required commands
RUN apt-get update && apt-get install -y --no-install-recommends gcc openssh-server sudo vim nano
RUN service ssh restart

RUN pip install pipenv

# Install Python dependencies.
COPY Pipfile .
COPY Pipfile.lock .
RUN pipenv install --deploy --system --ignore-pipfile


# Create and switch to a new user
RUN useradd --create-home appuser --shell /bin/bash --password $(perl -e "print crypt('qwerty', 'sa');")
WORKDIR /home/appuser

# Install application into container
COPY ./ ./webserver
RUN mv webserver/docker /var/
RUN chown -R appuser:appuser webserver
RUN chmod o-rwx /var/docker
RUN chmod u+x /var/docker/start.sh

# Run the application
EXPOSE 80
CMD /var/docker/start.sh