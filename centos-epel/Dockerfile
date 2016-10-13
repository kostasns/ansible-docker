FROM centos:7
MAINTAINER Kostas <kostas@nuclearshoebox.com>

ENV ANSIBLE_DIR /ansible
ENV TINI_VERSION v0.10.0

ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /bin/tini
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini.asc /bin/tini.asc
RUN gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 595E85A6B1B4779EA4DAAEC70B588DFF0527A9B7 && \
    gpg --verify /bin/tini.asc
	
RUN yum install -y epel-release && \ 
    yum install -y \ 
	   ansible \
	   sudo && \
    yum clean all && \
	rm -rf /var/cache/yum/* && \
    mv /etc/ansible/ansible.cfg /etc/ansible/ansible.cfg.org && \
	mkdir -p ${ANSIBLE_DIR} && \
	chmod +x /bin/tini

COPY ansible.cfg /etc/ansible/
WORKDIR ${ANSIBLE_DIR}

ENTRYPOINT ["/bin/tini", "--"]