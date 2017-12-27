FROM debian:stretch

WORKDIR /opt

RUN apt-get update
RUN apt-get install -y python sudo lsb-release gnupg2
COPY bootstrap.py .
COPY requirements.txt .
RUN python bootstrap.py -v
COPY requirements-dev.txt .
RUN .venv/bin/pip install -r requirements-dev.txt
COPY . .
