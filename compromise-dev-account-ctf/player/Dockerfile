FROM ubuntu:24.10

RUN set -xe \
    && apt-get update -y \
    && apt-get install -y python3-pip git vim nano build-essential 
RUN git clone https://github.com/vanhauser-thc/thc-hydra.git
RUN cd thc-hydra && ./configure && make && make install

RUN useradd --create-home user

WORKDIR /home/user
COPY ./malicious_script.py /home/user/
COPY ./rockyou.txt /home/user/
COPY ./README.md /home/user/
RUN chmod a+x /home/user/malicious_script.py
RUN chown -R user:user /home/user

USER user
