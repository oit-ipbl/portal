# Developing inside the ROS container with VSCode

## Objectives
- This page explains how to develop inside the ROS-Noetic Docker Container via VSCode on Windows.

<image src="../image/architecture.jpg">

## Prerequisite
- "[Robot Development Environment for iPBL](https://github.com/oit-ipbl/portal/blob/main/setup/dockerros.md)" has already been installed.
- "[Image Processing Environment for iPBL](https://github.com/oit-ipbl/portal/blob/main/setup/python+vscode.md)" has already been installed.

## Setup "Remote Explorer" that is one of VSCode EXTENSIONS
- Run the ROS container of Robot development environment. ([more details](dockerros.md))
  - Run Docker Desktop.
  - Execute `docker-compose up` on windows terminal.
- Open the VSCode of Image processing environment ([more details](python+vscode.md))
  - Execute `vscode.bat` in "C:\oit\py22_ipbl".
- Setting EXTENSIONS of VSCode
  - Click the folloing button (Remote Explorer Tab button).  <br>
    <image src="../image/remote_explorer_icon.png">
  - Open a side bar, and then right-click the "noeticvnc".<br>
    <image src="../image/noeticvnc_menu_vscode.png" width="50%" height="50%">
  - Click "Attach to Container", and then an new VSCode window is opened.
    - If the following message pops up, please click "Got It".<br>
      <image src="../image/warning_attaching.png" width="50%" height="50%"><br>
    - In this VSCode, you can use ubuntu's terminal emulator inside the ROS container.<br>
      <image src="../image/vscode_noeticvnc.png" width="75%"  height="75%">
  - Click the following button (Explorer Tab button) on the new VSCode window.<br>
    <image src="../image/explorer_icon.png">
  - Enter or Click "catkin_ws" folder.<br>
    <image src="../image/catkin_ws_vscode.png">
  - "catkin_ws" folder inside the ROS container is opened.

### :o:Checkpoint("Remote Environment")
- Open "New Terminal" on VSCode.<br>
  <image src="../image/new_terminal_vscode.png" width="75%"  height="75%">
- Execute `python --version`, and please confirm the python version inside the ROS container.
  ```sh
  ubuntu@????:~/catkin_ws$ python --version
  Python 3.8.10
  ```
> **Note**
> The version of Python used in the robot development environment (Ubuntu20 Docker container) is different from that used in the image processing environment (Windows). python3.8 is used in the RDE and python3.9 is used in the IPE.

### :o:Checkpoint("Remote Explorer")
- Open "src/CMakeLists.txt" in "catkin_ws\src" folder inside the ROS container on VSCode.<br>
    <image src="../image/CMakeList_on_vscode.png">
- Open the same file on a VNC Client. ([more details](dockerros.md))<br>
    <image src="../image/CMakeList_on_VNC_client.png">
- Please confirm two texts are the same.
