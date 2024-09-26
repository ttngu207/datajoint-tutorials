ARG PY_VER
ARG DISTRO
FROM mcr.microsoft.com/devcontainers/python:${PY_VER}-${DISTRO}
RUN \
    apt update && \
    apt-get install bash-completion graphviz default-mysql-client -y

COPY ./requirements.txt /tmp/

RUN \
    # tutorial dependencies
    pip install --no-cache-dir black faker ipykernel && \
    pip install --no-cache-dir -r /tmp/requirements.txt --upgrade && \
    rm /tmp/requirements.txt

ENV DJ_HOST fakeservices.datajoint.io
ENV DJ_USER root
ENV DJ_PASS simple

USER vscode
CMD bash -c "sudo rm /var/run/docker.pid; sudo dockerd"
