FROM ubuntu:14.04

RUN apt-get update && apt-get install -y irssi

# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/irssi && \
    echo "irssi:x:${uid}:${gid}:irssi,,,:/home/irssi:/bin/bash" >> /etc/passwd && \
    echo "irssi:x:${uid}:" >> /etc/group && \
    echo "irssi ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/irssi && \
    chmod 0440 /etc/sudoers.d/irssi && \
    chown ${uid}:${gid} -R /home/irssi

USER irssi
ENV HOME /home/irssi
#CMD /usr/bin/chromium-browser --no-sandbox
#CMD sudo /usr/bin/chromium-browser
#CMD /usr/bin/chromium-browser
#CMD /bin/bash
CMD /usr/bin/irssi -c irc.freenode.net -w 9hLLQWQe -n elisboa
#RUN passwd irssi
#CMD su - irssi
