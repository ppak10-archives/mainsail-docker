FROM python:2

ARG KLIPPER_CONFIG
ARG KLIPPER_LOG
ARG KLIPPER_SOCKET

WORKDIR /home

RUN apt update
RUN apt install -y \
  python-dev \
  libffi-dev \
  build-essential \
  libncurses-dev \
  libusb-dev \
  avrdude \
  gcc-avr \
  binutils-avr \
  avr-libc \
  stm32flash \
  dfu-util \
  libnewlib-arm-none-eabi \
  gcc-arm-none-eabi \
  binutils-arm-none-eabi \
  libusb-1.0-0 

RUN git clone https://github.com/KevinOConnor/klipper
RUN pip install -r ./klipper/scripts/klippy-requirements.txt


# Don't run service inside docker container.
# COPY ./klipper.service /etc/systemd/system/klipper.service
# RUN systemctl enable klipper.service

RUN mkdir klipper_config
RUN mkdir klipper_logs
RUN mkdir gcode_files
RUN touch klipper_config/printer.cfg

CMD ["python", "/home/klipper/klippy/klippy.py", \
  "/home/klipper_config/printer.cfg", \
  "-l", "/home/klipper_logs/klippy.log", \
  "-a", "/tmp/klippy_uds"]
