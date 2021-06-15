# Image Processing Environment for iPBL

## Objectives
- This page explains how to install both Python and VSCode constitute of our image processing environment.
- This environment does not affect the PC environment in which it is installed.

<image src="../image/architecture.jpg">

#### Details of the installed environment
- Python3.8.7 (embedded)
  - numpy 1.20.3
  - matplotlib 3.4.2
  - opencv-python 4.5.2.54
  - opencv-contrib-python 4.5.2.54
  - mediapipe 0.8.5
  - msvc-runtime 14.29.30036
- Visual Studio Code 1.57.0 (portable)   (*)拡張機能については要整理
  - EvilInspector
  - Japanese Language Pack for Visual Studio Code
  - Jupyter
  - Pylance
  - Python
  - Python for VSCode
  - Remote - Containers

## prerequisite
- Windows 10
- 8GB Memory
- 1.5GB HDD (C: drive)
- Webcam
- Uninstalling or stopping antivirus software
  - They may remove our installer and batch files.


## Setup both Python and VSCode with installer
### procedure
- Download this installer file by clicking the following url.
  - https://oskit-my.sharepoint.com/:u:/g/personal/takao_jinno_oit_ac_jp/EcFXD1YzQypLrUurdhg4gEwBx97nmCg7WyYAQRQQ50Bqng?e=Mw2DDR
    - **PW is written on Slack.**
    - If you have installed some antivirus software, this executable file and other batch files may not work properly.
- Execute "py21_installer.exe" file.
  - This installer is safe.
  - **Even if the warning pops up, execute it.**
- Choose "Yes".<br>
  <image src="../image/py21_installer.png" width="30%" height="30%">
- This installer setup the image processing environment (Python3 + VSCode) into "C:\out\py21", and create link on your Desktop.

### Installed folder structure
- installed folder "C:\oit\py21"
  - **code**: work folder
  - python-3.8.7: embedded python
  - VSCode-win32-x64-1.57.0:  portable visual studio code
  - **console.bat**:  open the command prompt with python-3.8.7 settings
  - **vscode.bat**: open VSCode with python-3.8.7 settings
  - [hidden file] setup.bat: create the link of "py21" on your Desktop
  - [hidden file] settings:  support files for setup<br>
    <image src="../image/py21_folder.png">

### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Python version of Command Prompt)
- Execute "console.bat" file.
- Please confirm the Python version of Command Prompt.
  ```sh
  PS C:\oit\py21\code> python --version
  Python 3.8.7
  ```

### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Python pip command)
- If you have not opened Command Prompt, execute "console.bat" file.
- Please confirm pip command and Python modules.
  ```sh
  PS C:\oit\py21\code> python -m pip list
  Package               Version
  --------------------- -----------
  ...(some module information)...
  matplotlib            3.4.2
  mediapipe             0.8.5
  msvc-runtime          14.29.30036
  numpy                 1.20.3
  opencv-contrib-python 4.5.2.54
  opencv-python         4.5.2.54
  Pillow                8.2.0
  pip                   21.1.2
  ...(some module information)...
  ```
- Please confirm pip install command.
  ```sh
  PS C:\oit\py21\code> python -m pip install -U numpy
  Requirement already satisfied: numpy in c:\oit\py21\python-3.8.7\lib\site-packages (1.20.3)
  ```

### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Run python code with Command Prompt)
- If you have not opened Command Prompt, execute "console.bat" file.
- Please confirm that the sample python code is executable with command prompt.
  ```sh
  PS C:\oit\py21\code> python hands.py
  ```
  - If it works normally, the webcam will start, and the shape of the hand will be recognized as shown below.<br>
    <image src="../image/hands.png" width="25%" height="25%">

### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(EXTENSIONS of VScode)
- Execute "vscode.bat" file.
- If the following message is pop-up, please check "Trust the authors of all files in the parent folder 'py21'" and choose "Yes, I trust the authors".<br>
  <image src="../image/warning_VSCode[first_time].png" width="50%" height="50%">
- Please confirm EXTENSIONS of VSCode
  - Click the following button (EXTENSIONS Tab button).<br>
    <image src="../image/Extensions_button.png" width="5%" height="5%">
  - Please confirm installed EXTENSIONS  (*)拡張機能については要整理
    - EvilInspector
    - Japanese Language Pack for Visual Studio Code
    - Jupyter
    - Pylance
    - Python
    - Python for VSCode
    - Remote - Containers      

### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Python version of VSCode)
- If you have not opened VSCode, execute "vscode.bat" file.
  - If the Terminal of VSCode is not opened, open the New Terminal as follows.
    <image src="../image/vscode_new_terminal.png" width="50%" height="50%"><br>
    <image src="../image/vscode_terminal_path.png" width="50%" height="50%"><br>
  - Please confirm python version of the Terminal of VSCode
    ```sh
    PS C:\oit\py21\code> python --version
    Python 3.8.7
    ```

### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Checkpoint(Run python code with VSCode)
- If you have not opened VSCode, execute "vscode.bat" file.
- Please confirm that the sample python code is executable with VSCode.
  - Double click "hands.py" -> Open "hands.py"<br>
    <image src="../image/vscode_sample.png" width="50%" height="50%">
  - If the Terminal of VSCode is not opened, open the New Terminal as follows.
    <image src="../image/vscode_new_terminal.png" width="50%" height="50%">
  - **At this time, make sure that the terminal path matches the parent directory of the Python code which you want to run.**<br>
    <image src="../image/vscode_terminal_path.png" width="50%" height="50%"><br>
    - If necessary, move the directory by the cd command.
  - Execute "hands.py" by clicking the following execution button.<br>
    <image src="../image/vscode_execute_button.png"><br>
  - If it works normally, the webcam will start, and the shape of the hand will be recognized as shown below.<br>
    <image src="../image/hands.png" width="25%" height="25%">
