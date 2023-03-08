FROM python:3

WORKDIR /home

RUN apt update
RUN apt install -y python3-dev \
  libopenjp2-7 \
  python3-libgpiod \
  curl \
  libcurl4-openssl-dev \
  libssl-dev \
  liblmdb-dev \
  libsodium-dev \
  zlib1g-dev \
  libjpeg-dev

RUN git clone https://github.com/Arksine/moonraker.git
RUN pip install -r ./moonraker/scripts/moonraker-requirements.txt

COPY config/ ./klipper_config/

CMD ["python", "/home/moonraker/moonraker/moonraker.py", \
  "-c", "/home/klipper_config/moonraker.conf", \
  "-l", "/home/klipper_logs/moonraker.log"]
