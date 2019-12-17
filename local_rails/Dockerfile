FROM ruby:2-alpine

RUN apk add --update --no-cache build-base nodejs tzdata git imagemagick libxml2-dev \
    libxslt-dev postgresql-dev yarn
RUN bundle config build.nokogiri --use-system-libraries

# Clean APK cache
# RUN rm -rf /var/cache/apk/*

# The application will live, and all
# commands you run through Docker will
# run, in /usr/src/app.
ENV APP_HOME /app
RUN mkdir -p $APP_HOME
WORKDIR $APP_HOME

RUN echo "gem: --no-rdoc --no-ri" >> ~/.gemrc

# Allow incoming connections on port
# 3000 to containers created from this
# image.
EXPOSE 3000

# Tell Bundler to install all your gems to /ruby_gems
ENV BUNDLE_PATH /ruby_gems

# specify the default command for this
# container, which starts the Rails
# server listening on all interfaces.
CMD ["bin/rails", "s", "-b", "0.0.0.0"]

##or
##CMD RAILS_ENV=${RAILS_ENV} bundle exec rails db:create db:migrate db:seed && bundle exec rails s -p ${PORT} -b '0.0.0.0'
