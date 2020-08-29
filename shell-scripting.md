### Bash scripts
ls -lh

### Docker
  #### start mongodb with docker
- docker run -it -p 27017:27017 --name mongodb -d mongo
- docker ps
- docker stop {container id}
- docker build -t {tag-name} .  // is "." or directory
