FROM balenalib/amd64-ubuntu-python:3.7.5

RUN apt-get update && \
   apt-get install -y git nvidia-cuda-toolkit gcc-6

RUN pip install deepspeech-gpu \
   git+git://github.com/constructorfleet/deepspeech-server.git#egg=deepspeech-server

COPY ./models models

WORKDIR /models

RUN wget https://github.com/mozilla/DeepSpeech/releases/download/v0.1.1/audio-0.1.1.tar.gz && \
   tar -zxvf audio-0.1.1.tar.gz && \
   rm audio-0.1.1.tar.gz
RUN wget https://github.com/mozilla/DeepSpeech/releases/download/v0.1.1/deepspeech-0.1.1-models.tar.gz && \
   tar -zxvf deepspeech-0.1.1-models.tar.gz && \
   rm deepspeech-0.1.1-models.tar.gz 

# to run deepspeech:
# CMD deepspeech ./models/output_graph.pb ./audio/8455-210777-0068.wav ./models/alphabet.txt

#to run deepspeech server:
ENV config /models/config.json
CMD ["sh", "-c", "/usr/local/bin/deepspeech-server --config ${config}"]
