# Developing inside the ROS container with VSCode

## Objectives
- This page explains how to develop inside the ROS-Melodic Docker Container via VSCode on Windows.

<image src="../image/architecture.jpg">

## Prerequisite
- Robot Development Environment for iPBL has already be installed.
- Image Processing Environment for iPBL has already be installed.

## Setup "Remote Explorer" that is one of VSCode EXTENSIONS 
- Run the ROS container of Robot development environment
  - Execute `docker-compose up` on windows terminal ([more details](dockerros.md))
- Open the VSCode of Image processing environment
  - Execute `vscode.bat` in "C:\oit\py21" ([more details](python+vscode.md))
- Setting EXTENSIONS of VSCode
  - Click the folloing button (Remote Explorer Tab button).  <br>
    <image src="../image/remote_explorer_icon.png">
  - Open a side bar, and then right-click the "melodicvnc".<br>
    <image src="../image/melodicvnc_menu_vscode.png">
  - Click "Attach to Container", and then an new VSCode window is opened.
    - In this VSCode, you can use ubuntu's terminal emulator inside the ROS container.<br>
    <image src="../image/vscode_merodicvnc.png">
  - Click the following button (Explorer Tab button) on the new VSCode window.<br>
    <image src="../image/explorer_icon.png">
  - Enter or Click "catkin_ws" folder.<br>
    <image src="../image/catkin_ws_vscode.png">
  - "catkin_ws" folder inside the ROS container is opened.

### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint("Remote Environment")
- Open "New Terminal" on VSCode.<br>
  <image src="../image/new_terminal_vscode.png">
- Execute `python --version`.
```sh
PS ~/catkin_ws$ python --version
Python 2.7.17
```

### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint("Remote Explorer")
- Open "src/CMakeLists.txt" in "catkin_ws" folder on the ROS container with VSCode.<br>
    <image src="../image/CMakeList_on_vscode.png">
- Open the same file on a VNC Client. ([more details](dockerros.md))<br>
    <image src="../image/CMakeList_on_VNC_client.png">
- Please confirm two texts are the same.
