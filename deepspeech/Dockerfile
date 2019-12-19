FROM balenalib/amd64-ubuntu-python:3.7.5

RUN apt-get update && \
   apt-get install -y git nvidia-cuda-toolkit gcc-6

RUN pip install deepspeech-gpu \
   git+git://github.com/constructorfleet/deepspeech-server.git#egg=deepspeech-server

COPY ./models models

# to run deepspeech:
# CMD deepspeech ./models/output_graph.pb ./audio/8455-210777-0068.wav ./models/alphabet.txt

#to run deepspeech server:
ENV config /models/config.json
CMD ["sh", "-c", "/usr/local/bin/deepspeech-server --config ${config}"]
