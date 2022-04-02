FROM        ghcr.io/parkervcp/yolks:debian

LABEL       author="Torsten Widmann" maintainer="support@goover.de"

RUN         apt update \
            && apt -y upgrade
RUN         sudo apt install apt-transport-https dirmngr gnupg ca-certificates
RUN			sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
RUN 		echo "deb https://download.mono-project.com/repo/debian stable-buster main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
RUN 		sudo apt update
RUN         apt install -y mono-complete lib32gcc-s1

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
