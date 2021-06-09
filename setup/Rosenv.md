# ROS Environment
## prerequisite
- Docker desktop for windows and WSL2 are installed adequately.

#### <font color="red">Checkpoint(ROS prerequisite)</font>
- Start Windows Terminal (or powershell), and execute the following command.
- Please confirm the Docker version (maybe version 20 or over).
```sh
PS C:\Users\????\ipbl> docker --version
Docker version 20.10.5, build 55c4c88
```

## Set up ROS Environment
### Get the ROS container
- Download this repository by clicking the following url.
  - https://github.com/oit-ipbl/portal/archive/refs/heads/main.zip
- Unzip portal-main.zip file.
- Open portal-main directory on windows terminal (or powershell).
- Next, `cd melodicvnc`
 - <font color="red">All the following commands must be executed in the melodicvnc directory.</font>
<image src="../image/powershell_melodicvnc.jpg">
- You can see the file `docker-compose.yml` in the melodicvnc directory.
- Get the Ros container.
  - You type the following command after `>` (In this case, `docker-compose pull`).
- This command downloads a ROS container(about 3GB) from Docker Hub.
```sh
PS C:\Users\????\melodicvnc> docker-compose pull
Pulling melodicvnc ... downloading (?.?%)
```
- Finally, the command shows `done`.
```sh
PS C:\Users\????\melodicvnc> docker-compose pull
Pulling melodicvnc ... done
PS C:\Users\????\melodicvnc>
```

#### <font color="red">Checkpoint(ROS image)</font>
- Please confirm the ROS container image was downloaded.
```sh
PS C:\Users\????\melodicvnc> docker images
REPOSITORY         TAG       IMAGE ID       CREATED        SIZE
igaki/melodicvnc   latest    5f4cf41ff1d6   2 months ago   3.06GB
```

### Run the ROS container
- Please run the `igaki/melodicvnc` through the following commands
- 1) You must in the melodicvnc directory by windows terminal (or powershell).
- 2) Confirm the docker-compose.yml in the melodicvnc directory
- 3) Execute `docker-compose up`
  - <font color="red">You must not use docker desktop dashboard to run the container.</font>

```sh
PS C:\Users\????\melodicvnc> docker compose up
Creating network "melodicvnc_default" with the default driver
Creating melodicvnc ... done
Attaching to melodicvnc
melodicvnc    | **Making workspace. Target ros-melodic**
melodicvnc    | File "/catkin_ws/src/CMakeLists.txt" already existsBase path: /home/ubuntu/catkin_ws
:
:
melodicvnc    | 2021-06-09 18:22:16,555 INFO success: x11vnc entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
melodicvnc    | 2021-06-09 18:22:16,556 INFO success: novnc entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
```
- If you want to stop the container, press Ctrl+C.

### Install VNC Client
- Because of its performance and functionality (for ex. copy and paste between windows and linux container), we strongly recommend to use VNC client to access inside the ROS container.
- If you can use vnc client, you can access `localhost:5900` during running the ROS container.
- If you don't have any vnc client, we recommend to install real vnc client(VNC Viewer)
  - https://www.realvnc.com/en/connect/download/viewer/
    - You can download suitable vnc viewer software. We recommend `Standalone EXE x64` for windows 10.
  - Please start the vnc viewer, and select File->New Connection.
  - Input `localhost:5900` in the VNC Server area, and press `OK`.
  - Select and Connect.
<image src="../image/realvnc.jpg">

#### <font color="red">Checkpoint(Access to the ROS container on VNC Viewer)</font>
- You can see ubuntu Desktop in the window of the VNC Viewer.

<image src="../image/ubuntu_vnc.jpg">

#### <font color="red">Checkpoint(Access to the ROS container on browser)</font>
- During running the ROS container, Access `http://localhost:8000/`.
- You can see ubuntu Desktop on the browser.
