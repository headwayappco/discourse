FROM ruby:2.6.2

ENV APP_UID=1000 \
  EDITOR=vim.tiny \
  NODE_ENV=development \
  RAILS_ENV=development \
  BUNDLE_GEMFILE=Gemfile \
  BUNDLE_PATH=/home/app/bundle \
  GEM_PATH=$BUNDLE_PATH \
  GEM_HOME=$BUNDLE_PATH \
  BUNDLE_APP_CONFIG=$BUNDLE_PATH

RUN groupadd --gid $APP_UID app \
  && useradd --uid $APP_UID --gid app --shell /bin/bash --create-home app

RUN apt-get update --fix-missing \
  && apt-get upgrade -y \
  && apt-get install -y \
    build-essential \
    git \
    libpq-dev \
    imagemagick \
    file \
    curl \
    postgresql-client \
    ${EDITOR%% *} \
  && apt-get autoremove \
  && apt-get clean

USER app

RUN gem install bundler
