# CMS Example

Based on Apostrophe Boilerplate v2.x, it's just a Node.js cms to use as sample project.

> Apostrophe Boilerplate is a minimal starting point for [Apostrophe 2](https://github.com/punkave/apostrophe) projects.

# TL;DR;

```bash
$ curl -LO https://raw.githubusercontent.com/fjagugar/blog-example/master/docker-compose.yml
$ docker-compose up
```

# How to use run the CMS?

The recommended way to run the CMS is using Docker Compose using the following `docker-compose.yml` template:

```yaml
version: '2'

services:
  mongodb:
    image: 'bitnami/mongodb'

  node:
    tty: true
    image: 'bitnami/node:latest'
    command: sh -c 'npm install && node app.js'
    environment:
      APOS_MONGODB_URI: 'mongodb://mongodb:27017'
    ports:
      - 3000:3000
    volumes:
      - .:/app
    depends_on:
      - mongodb
```

Launch the containers using:

```bash
$ docker-compose up -d
```

Once the CMS is running, you need create an admin user account so you're able to log into it. Run the command below to do so(this will prompt you for a password):

```bash
docker-compose exec node node app.js apostrophe-users:add admin admin
```

# Configuration

- Use the environment variable `APOS_MONGODB_URI` to configure the URI where MongoDB is running.

---------------

For more documentation on Apostrophe, visit the [A2 documentation site](http://apostrophecms.com).
