
# Docker Commands Cheat Sheet

## Check if Docker is Installed
```bash
docker
```

## Pull an Image from Docker Hub
```bash
docker pull <image_name>
```
Example:
```bash
docker pull ubuntu:22.04
```

## Create & Run a New Container
```bash
docker run -it <image_name>
```

With access to a serial port:
```bash
docker run -it --device=/dev/ttyUSB0 <image_name>
```

Privileged mode (access all devices - less secure):
```bash
docker run -it --privileged <image_name>
```

With custom name:
```bash
docker run -it --name my_container ubuntu:22.04
```

## Start an Existing Container
```bash
docker start <container_id_or_name>
```

## Attach to a Running Container
```bash
docker attach <container_id_or_name>
```

Note: This attaches to the container’s main process.

## If You want to open a new terminal rather than main process (Just how you open new terminal in ubuntu)
```bash
docker exec -it <container_id_or_name> bash
```

## Code in Docker Container
Mostly coding can be done through host PC's by Extension
1. Docker
2. Remote/ Dev-Containers

In vs Code Open Cmd Pallet (ctrl + shift + p / f1)
Type
```bash
Remote-Containers: Attach to Running Container
```

Make sure to run the Docker Container before doing this otherwise vs code will not detect this

Then a new tab of vs code will open and go to that directory and start coding

### Make sure You made the directory Before You start coding in vs code


## Exit from Container without Stopping It
Use the keyboard shortcut:
```
Ctrl + P + Q
```

## List Containers
All containers:
```bash
docker ps -a
```
Running containers:
```bash
docker ps
```

## Remove a Container
```bash
docker rm <container_id_or_name>
```

## Commit a Container as a New Image
```bash
docker commit <container_id_or_name> <new_image_name>
```
Example:
```bash
docker commit my_ros2_container ros2_image_with_ros_installed
```

## View Container History
```bash
docker history <image_name>
```



## Show Docker Image List
```bash
docker images
```

## ROS 2 Related
Sourcing the ROS 2 environment inside the container:
```bash
source /opt/ros/humble/setup.bash
```

Running ROS 2 help:
```bash
ros2 --help
```

Running a ROS 2 talker node (after installing packages):
```bash
ros2 run demo_nodes_cpp talker
```

---

## Troubleshooting

### Docker Daemon Not Running
```bash
sudo service docker start
```

### dpkg Interrupted Error
```bash
sudo dpkg --configure -a
```

---

## Extra: Access Host Serial Ports from Container
Make sure container is created with:
```bash
--device=/dev/ttyUSB0
```
Or use all devices (insecure but easy):
```bash
--privileged
```

