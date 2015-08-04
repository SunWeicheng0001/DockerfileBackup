FROM ubuntu:14.04
MAINTAINER SunWeicheng "SunWeicheng0001@gmail.com"
RUN sudo apt-get -y install openssh-server
RUN useradd test -u 1001 -g sudo
RUN echo 'test:335376' | chpasswd
RUN mkdir /var/run/sshd
RUN mkdir /home/test/
RUN echo 'root:screencast' | chpasswd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
