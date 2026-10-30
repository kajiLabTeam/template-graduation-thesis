FROM ubuntu:26.04@sha256:6a06111c3b0a8600feadb270aec771dc239bf407b25625f93f44ab00e11f4d3c22rrs

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    xdvik-ja \ 
    evince \
    texlive-lang-cjk \
    latexmk \
    language-pack-ja \
    wget \
    xzdec \
    texlive-latex-extra \
    git \
    cpanminus \
    texlive-extra-utils \
    make \
    npm \
    gh \
    tzdata

RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/*
RUN kanji-config-updmap-sys ipaex

ENV TZ=Asia/Tokyo
RUN ln -sf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

WORKDIR /workdir
VOLUME ["/workdir"]

RUN npm i -g \
    textlint \
    textlint-rule-preset-ja-technical-writing \
    textlint-rule-preset-jtf-style \
    textlint-rule-prh \
    textlint-plugin-latex2e \
    textlint-rule-preset-ja-engineering-paper

CMD ["bash"]

RUN cpanm Log::Log4perl Log::Dispatch::File YAML::Tiny File::HomeDir Unicode::GCString
