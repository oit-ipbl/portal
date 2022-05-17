# Robot Development Environment for iPBL

## Objectives
- This page explains how to install Docker Desktop and ROS-noetic containers constitute of our robot development environment.
- **Note:** The miner version of Python used in the robot development environment (Ubuntu20 Docker container) is different from that used in the image processing environment (Windows). python3.8.10 is used in the RDE and python3.X is used in the IPE.

<image src="../image/architecture.jpg">

## prerequisite
- Windows10 or 11
  - You may be able to use this development platform for iPBL on OS other than Windows 10(or Windows11), but we cannot provide any support. If you use other OS such as intel Mac, M1 Mac, etc. please set it up at your own risk.
- 8GB Memory or more
- 10GB HDD or more(strongly recommend to use SSD)

## Setup Docker
- Docker Desktop for Windows is Docker designed to run on Windows 10 or 11. This application supports running Linux Docker containers. Our iPBL uses Docker for running ROS application and robot simulator in ubuntu container on windows 10 or 11.

### Setup WSL2(Windows Subsystem for Linux)
- Docker desktop for windows requires WSL2(Windows Subsystem for Linux version2). If you didn't setup WSL2, please install it first.
- English manual: https://docs.microsoft.com/en-us/windows/wsl/install
- Japanese manual: https://docs.microsoft.com/ja-jp/windows/wsl/install
  - 手動インストールの説明を見てセットアップしてください．下記サイトも参考になります．
  - https://chigusa-web.com/blog/wsl2-win11/

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(WSL2)
- It's OK, if `wsl --set-default-version 2` command on powershell is executed normally as follows.

```
PS C:\????> wsl --set-default-version 2
For information on key differences with WSL2 please visit https:..aka.ms/wsl2
```

### Install Docker Desktop for Windows
- See the following instructions.
  - Download Docker Desktop for Windows and Install
  - https://docs.docker.com/desktop/windows/install/

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Docker on WSL)
- After installation of Docker, you must start Docker Desktop and confirm `Use the WSL2 based engine` is checked in the settings of the Docker.
<image src="../image/dockersetting.jpg">

### (Optional) Install Windows Terminal
- Windows Terminal is teminal application on windows10 by Microsoft. We strongly recommend to install this terminal application for controlling docker.
  - https://github.com/microsoft/terminal
- You can install Windows Terminal through Microsoft Store
  - https://aka.ms/terminal

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Docker version)
- Start Windows Terminal (or powershell), and execute the following command.
- Please confirm the Docker version (maybe version 20 or over).
```sh
PS C:\Users\????\ipbl> docker --version
Docker version 20.10.14, build a224086
```

## Set up ROS Environment
### Get the ROS container
- Download this repository by clicking the following url.
  - https://github.com/oit-ipbl/portal/archive/refs/heads/main.zip
- Unzip portal-main.zip file.
- Open portal-main directory on windows terminal (or powershell).
- Next, execute `cd noeticvnc`
 - All the following commands must be executed in the noeticvnc directory.
<image src="../image/powershell_melodicvnc.jpg">
  
- You can see the file `docker-compose.yml` in the noeticvnc directory.
- Get the Ros container.
  - You type the following command after `>` (In this case, type `docker-compose pull`).
- This command downloads a ROS container(about 3GB) from Docker Hub.

```sh
PS C:\Users\????\noeticvnc> docker-compose pull
Pulling noeticvnc ... downloading (?.?%)
```

- Finally, the command shows `done`.

```sh
PS C:\Users\????\noeticvnc> docker-compose pull
Pulling noeticvnc ... done
PS C:\Users\????\noeticvnc>
```

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(ROS image)
- Please confirm the ROS container image was downloaded in the windows terminal (or powershell).

```sh
PS C:\Users\????\noeticvnc> docker images
REPOSITORY         TAG       IMAGE ID       CREATED        SIZE
igaki/noeticvnc   latest    5f4cf41ff1d6   2 months ago   3.06GB
```

### Run the ROS container
- Please run the `igaki/noeticvnc` container by the following commands
- 1) You must be in the noeticvnc directory by windows terminal (or powershell).
- 2) Confirm the docker-compose.yml in the noeticvnc directory
- 3) Execute `docker-compose up`
  - You **must not use docker desktop dashboard** to run the container.

```sh
PS C:\Users\????\noeticvnc> docker-compose up
Creating network "noeticvnc_default" with the default driver
Creating noeticvnc ... done
Attaching to noeticvnc
noeticvnc    | **Making workspace. Target ros-noetic**
noeticvnc    | File "/catkin_ws/src/CMakeLists.txt" already existsBase path: /home/ubuntu/catkin_ws
:
:
noeticvnc    | 2021-06-09 18:22:16,555 INFO success: x11vnc entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
noeticvnc    | 2021-06-09 18:22:16,556 INFO success: novnc entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
```
- If you want to stop the container, press Ctrl+C.

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Access to the ROS container on browser)
- During running the ROS container, Access `http://localhost:8000/`.
- You can see ubuntu Desktop on the browser.

### Install VNC Client
- Because of its performance and functionality (for ex. copy and paste between windows and linux container), we strongly recommend to use VNC client to access inside the ROS container.
- If you can use vnc client, you can access `localhost:5900` during running the ROS container.
- If you don't have any vnc client, we recommend to install real vnc client(VNC Viewer)
  - https://www.realvnc.com/en/connect/download/viewer/
    - You can download suitable vnc viewer software. We recommend `Standalone EXE x64` for windows 10 or 11.
  - Please start the vnc viewer, and select File->New Connection.
  - Input `localhost:5900` in the VNC Server area, and press `OK`.
  - Select and Connect.
    - When you connect to the ros-container, VNC viewer shows the message `Unencrypted Connection`. You don't need to worry about it because the connection is within your computer.

<image src="../image/realvnc.jpg">

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Access to the ROS container on VNC Viewer)
- You can see ubuntu Desktop in the window of the VNC Viewer.

<image src="../image/ubuntu_vnc.jpg">

## How to use ros container.
- In the following, we explain usage of the container.

### Use terminal Emulator in the ROS Container
- In the ROS container, you can use the terminal emulator to control ROS programs.
- As follows, click the icon of the terminal in the ros container, and execute `cd ~/catkin_ws` to run various ros programs.

<image src="../image/ubuntu_terminal.jpg">

### Direct access directory and files inside the ROS container 
- Some directories in the container can be accessed directly from Windows without using the VNC client.
- For example, you can copy image files, etc. from windows into the ROS container in the following way.
  - ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Note: It is strongly recommended that you access program files such as python only from within the container or from the remote container plugin of vscode. This may cause problems with permissions and other issues.

#### How to access files and directories in the ROS container
- Access `\\wsl$\docker-desktop-data\version-pack-data\community\docker\volumes` on the windows explorer as follows.
- You can see two directiries `noeticvnc_catkin_ws` and `noeticvnc_ubuntu` in the `volumes` directory.
- These directoryies correspond to `/catkin_ws` and `/home/ubuntu/` directories in the ROS container, respectively.

<image src="../image/explorer.jpg">


### Change Timezone of the ROS Container
- First, stop the container with `Ctrl+C` command on the powershell.
- Open the file `docker-compose.yml` in the noeticvnc directory.
- In the following `docker-compose.yml`, `TZ=Asia/Tokyo` means the ros container is set as japan standard time(UTC+9).
- If you want to set thai timezone (UTC+7), you should change `TZ=Asia/Tokyo` to `TZ=Asia/Bangkok`.
- Change timezone setting and start the container with `docker-compose up`.

```yml
version: '3'
services:
  noeticvnc:
    container_name: noeticvnc
    image: igaki/noeticvnc:latest
    volumes:
      - catkin_ws:/catkin_ws
      - ubuntu:/home/ubuntu
    ports:
      - "8000:8080"
      - "5900:5900"
      - "9090:9090" 
      - "50001:50001"
    environment:
      - USER=ubuntu
      - RESOLUTION=1024x768
      - TZ=Asia/Tokyo
    tty: true

volumes:
  catkin_ws:
  ubuntu:
```
