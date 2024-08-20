# Docker-Cheatsheet

## Docker
List Docker container(s)
```
docker ps -a
```

Check container(s) log(s)
```
docker-compose logs
```

Check container build status
```
docker logs <container-id>
```

Auto scroll logs
```
docker logs -f --tail <container-id>
```

Get interactive shell after container has started
```
docker exec -it <container-id> /bin/bash
```

Start docker container after host restart
```
docker container start <container-id>
```

Delete all container(s) including its volume(s) use
```
docker rm -vf $(docker ps -aq)
```

Delete all image(s)
```
docker rmi -f $(docker images -aq)
```

Remove:
  - all stopped containers
  - all networks not used by at least one container
  - all volumes not used by at least one container
  - all images without at least one container associated to them
  - all build cache
```
docker system prune -a --volumes
```

List volume(s)
```
docker volume ls
```

## Docker-compose
Build the Docker image(s):
```
docker-compose build
```

Run image(s)
```
docker-compose up -d
```

## Common Issue(s):
### Error: 
> docker: Got permission denied while trying to connect to the Docker daemon socket at ...

### Solution:
1. Add current user to docker group
```
sudo usermod -aG docker $USER
```
2. Verify docker can be ran
```
docker ps -a
```
3. Reboot if error persist
```
sudo reboot
```

### Error:
> docker: Error response from daemon: Container command '/EXAMPLE.sh' not found or does not exist..

### Solution (1):
Shell scripts (.sh files) may need modification for different operating systems due to differences in how these systems interpret end-of-line (EOL) characters. The primary reason for modifying .sh files across different operating systems is to ensure compatibility and correct execution of the scripts. 
1. Download and open [Notepad++](https://notepad-plus-plus.org/downloads/):

2. Go to File > Open and select the .sh file you want to modify.

3. Check Current EOL Format:

> Look at the status bar at the bottom of the Notepad++ window. It will show the current EOL format, such as Windows (CR LF), Unix (LF), or Macintosh (CR).
Convert EOL Characters:

4. Go to Edit > EOL Conversion in the menu bar.

5. Choose the appropriate EOL format for your target environment:
>     Windows (CR LF): Converts EOL characters to \r\n.
>     Unix (LF): Converts EOL characters to \n.
>     Macintosh (CR): Converts EOL characters to \r.

6. Save the File

### Solution (2):
Convert the file using the `convert_eol.py` script.
