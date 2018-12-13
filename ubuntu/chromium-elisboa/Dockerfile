FROM ubuntu:18.04

#COPY sysctl.conf /etc/sysctl.conf
#COPY alsa.conf /usr/share/alsa/alsa.conf

RUN apt-get update
RUN apt-get install -y libgl1-mesa-glx libgl1-mesa-dri
RUN apt-get install -y xdg-utils libxss1 alsa-base pulseaudio fonts-noto
RUN apt-get install -y chromium-browser
RUN rm -rf /var/lib/apt/lists/*

RUN echo enable-shm=no >> /etc/pulse/client.conf

# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/elisboa && \
    echo "elisboa:x:${uid}:${gid}:Developer,,,:/home/elisboa:/bin/bash" >> /etc/passwd && \
    echo "elisboa:x:${uid}:" >> /etc/group && \
    chown ${uid}:${gid} -R /home/elisboa && \
    adduser elisboa audio && \
    adduser elisboa video && \
    adduser elisboa pulse && \
    adduser elisboa pulse-access

USER elisboa
ENV PULSE_SERVER /run/pulse/native
ENV HOME /home/elisboa

#CMD /usr/bin/chromium-browser --no-sandbox
#CMD sudo /usr/bin/chromium-browser

CMD ["/usr/bin/chromium-browser"]

#CMD /bin/bash
