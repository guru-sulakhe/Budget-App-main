FROM ruby:3.2
#Install essential packages and dependencies
RUN apt-get update -qq && apt-get install -y \
  build-essential \
  libpq-dev \
  nodejs \
  yarn \
  postgresql-client
# Creating /opt/server directory
RUN mkdir /opt/server
# Seting working directory
WORKDIR /opt/server
# Install gems
COPY Gemfile Gemfile.lock ./
RUN bundle install
# Copy rest of the application
COPY . .
# Expose port 3000
EXPOSE 3000
# Start the Rails server
CMD ["bash", "-c", "rm -f tmp/pids/server.pid && bundle exec rails server -b 0.0.0.0"]

# $ docker login -u <username>
# $ docker login -u guru1188
# $ docker tag trail:v1.0 guru1188/rails:v1.0
# $ docker push guru1188/rails:v1.0