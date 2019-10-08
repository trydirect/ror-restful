FROM ruby:2.5
LABEL maintainer="spilchin.serghei@gmail.com"
ENV TZ=America/Los_Angeles
RUN  groupadd -r -g 2000 rails; useradd -r -u 2000 -g 2000 -m -c "app account" -d /home/rails -s /bin/bash rails
RUN apt-get update -y \
    && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y \
        autoconf \
        bison \
        build-essential \
        libssl-dev \
        libyaml-dev \
        libreadline-dev \
        zlib1g-dev \
        libncurses5-dev \
        libffi-dev \
        libgdbm-dev \
        libgmp-dev \
        locales \
        curl \
        git \
        unzip \
        supervisor \
        nodejs

#install “rbenv” nad “ruby-build” plugin  
RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv \
    && git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build

#add “~/.rbenv/bin” to your executable path and let rbenv start automatically
RUN echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc \
    && echo 'eval "$(rbenv init -)"' >> ~/.bashrc

RUN . ~/.bashrc

RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    locale-gen
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

WORKDIR /usr/src/app
COPY src/backend /usr/src/app
RUN gem install bundler -v 1.17.3
# && gem install rdoc-data
RUN bundle install
#RUN bundle update && bundle update json
RUN /usr/bin/supervisord -c /etc/supervisor/supervisord.conf
#CMD ["rails", "server", "--binding", "0.0.0.0", "--port", "3000" ]

