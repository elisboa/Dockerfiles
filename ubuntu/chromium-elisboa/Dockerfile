FROM ubuntu:18.10

#COPY sysctl.conf /etc/sysctl.conf
#COPY alsa.conf /usr/share/alsa/alsa.conf

RUN apt-get update
RUN apt-get install -y libgl1-mesa-glx libgl1-mesa-dri
RUN apt-get install -y xdg-utils libxss1 alsa-base pulseaudio fonts-noto gdebi-core wget
RUN apt-get install -y chromium-browser
#RUN apt-get install -y 

RUN wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb -O /tmp/google-chrome-stable.deb
RUN dpkg -i /tmp/google-chrome-stable.deb || apt-get install -y --fix-broken

RUN rm -rf /var/lib/apt/lists/*

#RUN echo enable-shm=no >> /etc/pulse/client.conf

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

#USER root
#CMD ["/bin/bash"]

ENV TZ=America/Sao_Paulo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

USER elisboa
ENV PULSE_SERVER /run/pulse/native
ENV HOME /home/elisboa

#CMD /usr/bin/chromium-browser --no-sandbox
#CMD sudo /usr/bin/chromium-browser

WORKDIR /home/elisboa
CMD ["/usr/bin/google-chrome"]

#CMD /bin/bash
