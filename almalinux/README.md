# Creez une image Almalinux avec supervisord et sshd
```shell
docker build -t puppet-agent-almalinux .   # build the image
docker run -d --name alma  puppet-agent-almalinux  # container alma created
docker ps # check 
docker logs alma # see container logs
# sshd doit avoir un pid
```