
1. docker pull </image/>  {by default pulls with latest tag}
2. docker run </image_name or id/>  {creates a new container from that image and starts it}
3. docker run -it </image_name or id/>  {used for running shells like bash in ubuntu in interactive mode(-i) with tty login(-t)}
4. docker start </container_name or id/>  {starts an existing container}
5. docker stop </container_name or id/>  {stops an existing container}
6. docker ps  {show all running containers}
7. docker ps -a  {show all containers}
8. docker rm </container_name or id/>  {delete container}
9. docker rmi </image or id/>  {delete image. all containers of this image must be deleted first}



### Flags

- -it  {explained above}
- -e  {to set environment variables like root passwd for mysql}
- --name  {to set name of container}
- -d  {detached mode. running container in background}