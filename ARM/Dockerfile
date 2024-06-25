FROM arm32v7/ubuntu:latest

RUN apt-get update && \
    apt-get install -y \
    git cmake libjpeg8-dev libv4l-dev && \
    rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/jacksonliam/mjpg-streamer.git /opt/mjpg-streamer

WORKDIR /opt/mjpg-streamer/mjpg-streamer-experimental
RUN make

CMD ["./mjpg_streamer", "-i", "input_uvc.so -y -d /dev/video0 -r 1920x1080 -f 30", "-o", "output_http.so -w ./www"]
