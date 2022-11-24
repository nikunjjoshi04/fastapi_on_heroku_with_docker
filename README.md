# fastapi_on_heroku_with_docker
fastapi on heroku with docker

**Set**: DOCKER_DEFAULT_PLATFORM <br>
we want to create a x86 linux/amd64 compatible image <br>
The DOCKER_DEFAULT_PLATFORM environment variable permits to set the default platform for the commands that take the --platform flag.

```
docker buildx build --platform linux/amd64 -t myapp .
# tag image to match Heroku naming conventions
docker tag myapp registry.heroku.com/<heroku app name>/web
# push
docker push registry.heroku.com/<heroku app name>/web
```
**OR**
```
export DOCKER_DEFAULT_PLATFORM=linux/amd64
```
build and push the image to heroku
```
heroku container:push web --app <heroku app name>
```
release image on heroku
```
heroku container:release web --app <heroku app name>
```
heroku logs 
```
heroku logs --app <heroku app name> --tail
```
if restart required
```
heroku restart --app <heroku app name>
```

