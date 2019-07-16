# Docker

## Remove unused images

`docker image rm $(docker images -f "dangling=true" -q)`
