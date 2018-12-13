FROM ubuntu:14.04

RUN apt-get update && apt-get install -y libxcb1 libnotify4 libnss3 libxkbfile1 libgconf-2-4 libsecret-1-0 libgtk-3-0 libxss1 libx11-xcb-dev

# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer && \
    adduser developer audio

USER developer
ENV HOME /home/developer
#CMD /usr/bin/chromium-browser --no-sandbox
#CMD sudo /usr/bin/chromium-browser
CMD /home/developer/Programs/Telegram/Telegram
#CMD /bin/bash
