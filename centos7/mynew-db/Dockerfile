RUN adduser remote_user && \
    echo "1234" | passwd remote_user --stdin && \
    mkdir /home/remote_user/.ssh && \
    chmod 700 /home/remote_user/.ssh

COPY db-key.pub /home/remote_user/.ssh/authorized_keys

RUN chown remote_user:remote_user -R /home/remote_user  && \
    chmod 600 /home/remote_user/.ssh/authorized_keys

RUN /usr/bin/ssh-keygen -A
EXPOSE 22
RUN rm -rf /run/nologin
#RUN /usr/sbin/sshd-keygen

RUN yum install -y mysql

RUN yum install -y curl

RUN yum -y install epel-release && yum clean all
RUN yum -y install python3-pip && yum clean all

RUN pip3 install awscli

CMD /usr/sbin/sshd -D

