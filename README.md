# docker-images

Collection of docker containers I frequently need.

## nodejs
- 14.15.4-alpine
- 14.18.3-alpine
- 14.19.0-alpine
- 16.13.0-alpine
- 16.14.0-alpine

## How to build and push new images

```
$ docker build -t adikari/docker-images:<tagname> nodejs --platform linux/amd64
$ docker push adikari/docker-images:<tagname>
```
