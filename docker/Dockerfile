FROM alpine/bundle:2.7.2
WORKDIR /site
RUN gem install bundler jekyll
COPY Gemfile /site
RUN bundle install
COPY . /site
CMD [ "bundle", "exec", "jekyll", "serve", "--host", "0.0.0.0" ]