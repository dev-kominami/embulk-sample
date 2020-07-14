FROM ruby:2.7.1-alpine3.12

RUN apk update && \
    apk upgrade && \
    apk add --no-cache \
    curl \
    bash \
    openjdk8

WORKDIR /root/

# embulk install
RUN curl --create-dirs -o ~/.embulk/bin/embulk -L "https://dl.embulk.org/embulk-latest.jar"
RUN chmod +x ~/.embulk/bin/embulk
RUN echo 'export PATH="$HOME/.embulk/bin:$PATH"' >> ~/.bashrc
RUN source ~/.bashrc

# input plugin install 
RUN apk add --no-cache libc6-compat \
  && .embulk/bin/embulk gem install 'embulk-input-mysql' \
  && .embulk/bin/embulk gem install 'embulk-output-command'

#参考：https://techlog.voyagegroup.com/entry/2017/07/31/173839
