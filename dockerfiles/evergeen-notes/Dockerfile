FROM ubuntu:20.10
SHELL ["/bin/bash", "-c"] 
EXPOSE 1900
RUN apt-get update \
    && apt-get install nodejs --yes \
    && apt-get install npm --yes \
    && apt-get install wget --yes \
    && apt-get install socat --yes \
    && apt-get install git --yes \
    && mkdir hugotools \
    && cd hugotools \
    && wget https://github.com/gohugoio/hugo/releases/download/v0.79.1/hugo_extended_0.79.1_Linux-64bit.deb \
    && yes | dpkg -i hugo*.deb \
    && hugo version \
    && mkdir site \
    && cd site \
    && hugo new site . \
    && rm -rf content \
    && rm -rf config.toml \
    && npm install -D --save autoprefixer \
    && npm install -D --save postcss-cli \
    && git clone --recurse-submodules --depth 1 https://github.com/google/docsy.git themes/docsy \
    && echo -e "socat TCP-LISTEN:1900,fork,reuseaddr TCP:localhost:1313 &\n cd hugotools/site\nhugo server --buildDrafts" >> build_notes.sh
ENTRYPOINT ["sh", "/hugotools/site/build_notes.sh"]