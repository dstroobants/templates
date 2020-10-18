# Rails 6 Application Template

### Buid the project

```
docker-compose run --no-deps web rails new . --force --database=postgresql
sudo chown -R $USER:$USER .
docker-compose build
```

### Connect the DB

Edit `config/database.yml` and replace by the following:

```
default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: postgres
  password: password
  pool: 5

development:
  <<: *default
  database: myapp_development

test:
  <<: *default
  database: myapp_test
```

### Boot the app

`docker-compose up`

### Create the DB

`docker-compose run web rake db:create`

### Connect to the app

`http://localhost:3000`

### Rebuild/Reload

Some changes require only `docker-compose up --build`

But a full rebuild requires a re-run of `docker-compose run web bundle install` to sync changes in the Gemfile.lock to the host, followed by `docker-compose up --build`
