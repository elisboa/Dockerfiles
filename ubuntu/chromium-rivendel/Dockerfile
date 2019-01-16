FROM ubuntu

#RUN apt-get update && apt-get install -y chromium-browser
RUN apt-get update && apt install -y chromium-browser

COPY Sao_Paulo /etc/localtime

# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
	mkdir -p /etc/sudoers.d && \
    mkdir -p /home/rivendel && \
    echo "rivendel:x:${uid}:${gid}:Developer,,,:/home/rivendel:/bin/bash" >> /etc/passwd && \
    echo "rivendel:x:${uid}:" >> /etc/group && \
    echo "rivendel ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/rivendel && \
    chmod 0440 /etc/sudoers.d/rivendel && \
    chown ${uid}:${gid} -R /home/rivendel && \
    adduser rivendel audio && \
    adduser rivendel video

USER rivendel
ENV HOME /home/rivendel
WORKDIR /home/rivendel
RUN date
#CMD /usr/bin/chromium-browser --no-sandbox
#CMD sudo /usr/bin/chromium-browser
CMD /usr/bin/chromium-browser
#CMD /bin/bash
