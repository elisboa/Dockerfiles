FROM ubuntu:14.04

#COPY sysctl.conf /etc/sysctl.conf
#COPY alsa.conf /usr/share/alsa/alsa.conf

RUN apt-get update
RUN apt-get install -y libgl1-mesa-glx libgl1-mesa-dri
RUN apt-get install -y xdg-utils libxss1 alsa-base pulseaudio fonts-noto
RUN apt-get install -y audacity
RUN rm -rf /var/lib/apt/lists/*

#RUN echo enable-shm=no >> /etc/pulse/client.conf

# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /etc/sudoers.d && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer && \
    adduser developer audio && \
    adduser developer video && \
    adduser developer pulse && \
    adduser developer pulse-access

USER developer
ENV PULSE_SERVER /run/pulse/native
ENV HOME /home/developer

#CMD /usr/bin/audacity --no-sandbox
#CMD sudo /usr/bin/audacity
CMD ["/usr/bin/audacity"]
#CMD /bin/bash
