PhantomJsEnv
===========

This is a Docker Image with PhantomJS headless browser installed. PhantomJsEnv was created to run Selenium tests on PhantomJs wihtout installing NodeJS and PhantomJS. PhantomJs is executed inside a container in ghostrdirver mode and connected from a host machine.

## Installation

Grab prepacked [image from a Docker Hub](https://registry.hub.docker.com/u/davert/phantomjs-env/)

```
docker pull davert/phantomjs-env
```


Or build image by yourself. Just clone this repo and run

```
docker build -t phantomjs-env .
```

## Usage

PhantomJsEnv is able to connect to local or remote web sites. 

### Accessing Remote Website

Run the container and bind it to default Webdriver port `4444` 

```
docker run -i -t -p 4444:4444 davert/phantomjs-env 
```

### Accessing Local Website by Port

In case you want to access local website from container you can do the following:
if application is run on localhost (`0.0.0.0`) on a specific port, you can pass `APP_PORT` environment variable into it:

```
php -S 0.0.0.0:8000 & 
docker run -i -t -p 4444:4444 -e APP_PORT=8000 davert/phantomjs-env 
```

### Accessing Local Website by Host

In case local web site is served by nginx or Apache, and is configured for a specific host, you can pass host name as environment variable:

```
docker run -i -t -p 4444:4444 -e APP_HOST=myapp davert/phantomjs-env 
```