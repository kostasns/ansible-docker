FROM centos:7

LABEL maintainer="kostas@nuclearshoebox.com" \
	  build-date="2016-02-17" \
	  name="ansible" \
	  com.nuclearshoebox.description="Containerized Ansible" \
	  com.nuclearshoebox.url="https://www.ansible.com/" \
	  com.nuclearshoebox.docker.cmd="docker run -it --rm -v $(pwd):/ansible kostasns/ansible:<tag> <ansible_command>" \
	  license="GPLv3" \
	  vendor="Ansible"

ENV ANSIBLE_DIR /ansible
	
RUN yum install -y epel-release && \ 
    yum install -y \ 
	   ansible \
	   sudo && \
    yum clean all && \
	rm -rf /var/cache/yum/* && \
    mv /etc/ansible/ansible.cfg /etc/ansible/ansible.cfg.org && \
	mkdir -p ${ANSIBLE_DIR}	

COPY ansible.cfg /etc/ansible/
WORKDIR ${ANSIBLE_DIR}
