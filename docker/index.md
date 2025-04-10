# Docker

## Create a Ruby on Rails project

1. Create a folder with the project name

```bash
mkdir myapp
cd myapp
```

2. Create a Docker file `Dockerfile`

```dockerfile
FROM ruby:3.3.1

# Install dependencies
RUN apt-get update -qq && apt-get install -y build-essential nodejs postgresql-client

# Create app directory
WORKDIR /myapp

# Copy dependenci files
COPY Gemfile Gemfile.lock ./

# Install bundler and gems
RUN gem install bundler && bundle install

# Copy all files
COPY . .

# Add permission and set entry script
COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]

# Default port
EXPOSE 3000

# Default start
CMD ["rails", "server", "-b", "0.0.0.0"]
```

3. Create an entrypoint script `entrypoint.sh`

```bash
#!/bin/bash
set -e

# Remove the server PID file if it exists
rm -f /myapp/tmp/pids/server.pid

# Execute the passed command (e.g., rails server)
exec "$@"
```

4. Create a docker-compose file `docker-compose.yml`

```yaml
services:
  app:
    build: .
    volumes:
      - .:/myapp
    ports:
      - '3000:3000'
    depends_on:
      - db
    environment:
      DATABASE_HOST: db
      DATABASE_USERNAME: postgres
      DATABASE_PASSWORD: postgres

  db:
    image: postgres
    volumes:
      - db-data:/var/lib/postgresql/data # Store data outside of postgres container
    ports:
      - '5432:5432'
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres

volumes:
  db-data:
```

5. Create `Gemfile` and `Gemfile.lock`

```gemfile
source "https://rubygems.org"

gem "rails", "~> 7.2.2"
```

6. Create rails project

```bash
docker-compose run app rails new . --force --no-deps --database=postgresql --skip-keeps --skip-test
```

7. Build the containers

```bash
docker-compose build
```

8. Change database.yml

```yml
development:
  adapter: postgresql
  encoding: unicode
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  database: myapp_development
  host: <%= ENV["DATABASE_HOST"] %>
  username: <%= ENV["DATABASE_USERNAME"] %>
  password: <%= ENV["DATABASE_PASSWORD"] %>
```

9. Create database

```bash
docker-compose run app rails db:create
```

10. Run project

```bash
docker-compose up --remove-orphans
```
