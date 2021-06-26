# Robot Development Environment for iPBL

## Objectives
- This page explains how to install Docker Desktop and ROS-melodic containers constitute of our robot development environment.

<image src="../image/architecture.jpg">

## prerequisite
- Windows10
  - You may be able to use this development platform for iPBL on OS other than Windows 10, but we cannot provide any support. If you use other OS such as intel Mac, M1 Mac, etc. please set it up at your own risk.
- 8GB Memory
- 10GB HDD(strongly recommend to use SSD)

## Setup Docker
- Docker Desktop for Windows is Docker designed to run on Windows 10. This application supports running Linux Docker containers. Our iPBL uses Docker for running ROS application and robot simulator in ubuntu container on windows 10.

### Setup WSL2(Windows Subsystem for Linux)
- Docker desktop for windows requires WSL2(Windows Subsystem for Linux version2). If you didn't setup WSL2, please install it first.
- English manual: https://docs.microsoft.com/en-us/windows/wsl/install-win10
  - Almost all students should select manual install.
- Japanese manual: https://docs.microsoft.com/ja-jp/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package
  - 手動インストールの説明を見てセットアップしてください．下記サイトも参考になります．
  - https://www.kkaneko.jp/tools/wsl/wsl2.html

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(WSL2)
- It's OK, if `wsl --set-default-version 2` command on powershell is executed normally.

### Install Docker Desktop for Windows
- See the following instructions.
  - English manual: https://docs.docker.com/docker-for-windows/install/
  - Japanese manual: https://docs.docker.jp/docker-for-windows/install.html

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
Docker version 20.10.5, build 55c4c88
```

## Set up ROS Environment
### Get the ROS container
- Download this repository by clicking the following url.
  - https://github.com/oit-ipbl/portal/archive/refs/heads/main.zip
- Unzip portal-main.zip file.
- Open portal-main directory on windows terminal (or powershell).
- Next, execute `cd melodicvnc`
 - All the following commands must be executed in the melodicvnc directory.
<image src="../image/powershell_melodicvnc.jpg">
  
- You can see the file `docker-compose.yml` in the melodicvnc directory.
- Get the Ros container.
  - You type the following command after `>` (In this case, type `docker-compose pull`).
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

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(ROS image)
- Please confirm the ROS container image was downloaded in the windows terminal (or powershell).

```sh
PS C:\Users\????\melodicvnc> docker images
REPOSITORY         TAG       IMAGE ID       CREATED        SIZE
igaki/melodicvnc   latest    5f4cf41ff1d6   2 months ago   3.06GB
```

### Run the ROS container
- Please run the `igaki/melodicvnc` container by the following commands
- 1) You must be in the melodicvnc directory by windows terminal (or powershell).
- 2) Confirm the docker-compose.yml in the melodicvnc directory
- 3) Execute `docker-compose up`
  - You **must not use docker desktop dashboard** to run the container.

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

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Access to the ROS container on browser)
- During running the ROS container, Access `http://localhost:8000/`.
- You can see ubuntu Desktop on the browser.
- When you enter the ROS container first, you should select window panel setting. We recommend to select `Use Default Config`.

<image src="../image/ubuntu_panel.jpg" width=300>

### Install VNC Client
- Because of its performance and functionality (for ex. copy and paste between windows and linux container), we strongly recommend to use VNC client to access inside the ROS container.
- If you can use vnc client, you can access `localhost:5900` during running the ROS container.
- If you don't have any vnc client, we recommend to install real vnc client(VNC Viewer)
  - https://www.realvnc.com/en/connect/download/viewer/
    - You can download suitable vnc viewer software. We recommend `Standalone EXE x64` for windows 10.
  - Please start the vnc viewer, and select File->New Connection.
  - Input `localhost:5900` in the VNC Server area, and press `OK`.
  - Select and Connect.
    - When you connect to the ros-container, VNC viewer shows the message `Unencrypted Connection`. You don't need to worry about it because the connection is within your computer.

<image src="../image/realvnc.jpg">

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Access to the ROS container on VNC Viewer)
- You can see ubuntu Desktop in the window of the VNC Viewer.
  - When you enter the ROS container first, you should select window panel setting. We recommend to select `Use Default Config`.

<image src="../image/ubuntu_panel.jpg" width=300>

<image src="../image/ubuntu_vnc.jpg">

## How to use ros container.
- In the following, we explain usage of the container.

### Use terminal Emulator in the ROS Container
- In the ROS container, you can use the terminal emulator to control ROS programs.
- As follows, click the icon of the terminal in the ros container, and execute `cd ~/catkin_ws` to run various ros programs.

<image src="../image/ubuntu_terminal.jpg">

### Copy and paste between windows and ubuntu(ROS container)

- Basically, you can paste strings that you copied in Windows into the container (and vice versa).
- However, the string you copied in Windows cannot be pasted directly into the terminal emulator in the container (probably due to the specification of the container and the VNC client).
- In that case, you can copy strings in the following two ways.
  1. Open the educational material in the container's web browser (Chrome) and copy the strings in the container. You can paste the strings to the terminal emulator.
  2. Paste strings you copied on Windows once into the editor or address bar of the browser in the container. You can paste the strings that you copied again in the container into the terminal emulator.

### Direct access directory and files inside the ROS container 
- Some directories in the container can be accessed directly from Windows without using the VNC client.
- For example, you can copy image files, etc. from windows into the ROS container in the following way.
  - ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Note: It is strongly recommended that you access program files such as python only from within the container or from the remote container plugin of vscode. This may cause problems with permissions and other issues.

#### How to access files and directories in the ROS container
- Access `\\wsl$\docker-desktop-data\version-pack-data\community\docker\volumes` on the windows explorer as follows.
- You can see two directiries `melodicvnc_catkin_ws` and `melodicvnc_ubuntu` in the `volumes` directory.
- These directoryies correspond to `/catkin_ws` and `/home/ubuntu/` directories in the ROS container, respectively.

<image src="../image/explorer.jpg">


### Change Timezone of the ROS Container
- First, stop the container with `Ctrl+C` command on the powershell.
- Open the file `docker-compose.yml` in the melodicvnc directory.
- In the following `docker-compose.yml`, `TZ=Asia/Tokyo` means the ros container is set as japan standard time(UTC+9).
- If you want to set thai timezone (UTC+7), you should change `TZ=Asia/Tokyo` to `TZ=Asia/Bangkok`.
- Change timezone setting and start the container with `docker-compose up`.

```yml
version: '3'
services:
  melodicvnc:
    container_name: melodicvnc
    image: igaki/melodicvnc:v1.1.0
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
