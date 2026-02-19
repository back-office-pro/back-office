# Getting started

Your back office is delivered in *on-premise* mode. This distribution method allows you to host your application yourself and maintain control over your data. To do this, you need to install your back office on your IT system.

## Server installation

The server installation takes place in a few minutes via [docker](https://www.docker.com/). You can use the following *docker* command to start immediately:

```shell
docker run --name back-office \ 
           -p 3000:3000 \ 
           -v storage:/back-office/storage \ 
           -v credentials:/back-office/config/credentials \ 
           -v clamav:/var/lib/clamav \
           back-office.pro/back-office:latest
```

Or you can also create a `docker-compose.yml` file:

```yaml
services:
  web:
    image: back-office.pro/back-office:latest
    ports:
      - 3000:3000
    volumes:
      - credentials:/back-office/config/credentials
      - storage:/back-office/storage
      - clamav:/var/lib/clamav
volumes:
  credentials:
  storage:
  clamav:
```

You can find more `docker-compose` files, with different image versions, [here](docker).

Then issue the command to create the containers:

```shell
docker-compose up --build
```

> [!WARNING]
> Your back office will be available on port **3000** by default. You can use a *reverse proxy* such as [Traefik](https://traefik.io/traefik/) or [Nginx](https://nginx.org/) to redirect the application to your domain.

## First time login

Once the server is installed, you may connect to the pre-configured account. Here are the credentials:

> [!IMPORTANT]
> **Email**: support@back-office.pro  
> **Password**: &z%4^~+FS0TQxL8

For security reasons, it is strongly advised to change these credentials after the first login.

## Additional configuration

In order to be able to use all the features of your back office, it is recommended to provide a set of API keys that unlock AI, translation, email sending, and cloud file storage features.

It is also recommended to provide the URL of the application that will be used to generate all the links for your back office.

You can find more explanation [in the associated documentation](https://www.back-office.pro/docs/en/reference/configuration).
