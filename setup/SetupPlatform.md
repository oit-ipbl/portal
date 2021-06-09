# Development Platform for iPBL
## prerequisite
- Windows10
  - Macでも実施できる可能性はありますが，スタッフがサポートできません．自己責任でセットアップしてください．
- 8GB Memory

## Setup Docker
- Docker Desktop for Windows is Docker designed to run on Windows 10. This application supports running Linux Docker containers. Our iPBL uses Docker for running ROS application and robot simulator in ubuntu container on windows 10.

### Setup WSL2(Windows Subsystem for Linux)
- Docker desktop for windows requires WSL2(Windows Subsystem for Linux version2). If you didn't setup WSL2, please install it first.
- English manual: https://docs.microsoft.com/en-us/windows/wsl/install-win10
  - Almost all students should select manual install.
- Japanese manual: https://docs.microsoft.com/ja-jp/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package
  - 手動インストールの説明を見てセットアップしてください．下記サイトも参考になります．
  - https://www.kkaneko.jp/tools/wsl/wsl2.html

#### <font color="red">Checkpoint(WSL2)</font>
- It's OK, if `wsl --set-default-version 2` command on powershell is executed normally.

### Install Docker Desktop for Windows
- See the following instructions.
  - English manual: https://docs.docker.com/docker-for-windows/install/
  - Japanese manual: https://docs.docker.jp/docker-for-windows/install.html

#### <font color="red">Checkpoint(Docker on WSL)</font>
- After installation of Docker, you must start Docker Desktop and confirm `User the WSL2 based engine` is checked in the settings of the Docker.
<image src="../image/dockersetting.jpg">

### (Optional) Install Windows Terminal
- Windows Terminal is teminal application on windows10 by Microsoft. We strongly recommend to install this terminal application for controlling docker.
  - https://github.com/microsoft/terminal
- You can install Windows Terminal through Microsoft Store
  - https://aka.ms/terminal
