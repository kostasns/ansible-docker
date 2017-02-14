FROM alpine:latest
MAINTAINER Kostas <kostas@nuclearshoebox.com>

ENV ANSIBLE_DIR /ansible

RUN apk add --update gcc \ 
		    libffi-dev \ 
	        musl-dev \ 
	        openssl-dev \
		    perl \
			py-pip \
			python \
			python-dev \
			sshpass && \
	rm -rf /var/cache/apk/* && \
	pip install --upgrade pip && pip install ansible && \
	mkdir -p /etc/ansible && mkdir -p ${ANSIBLE_DIR}
	
COPY ansible.cfg /etc/ansible/
WORKDIR ${ANSIBLE_DIR}
