# Image Processing Environment for iPBL

## Objectives
- This page explains how to install both Python and VSCode constitute of our image processing environment.
- This environment does not affect the PC environment in which it is installed.

> **Note**
> The minor version of Python used in the robot development environment (RDE: Ubuntu20 Docker container) is different from that used in the image processing environment (IPE: Windows). python3.8.10 is used in the RDE and python3.9.11 is used in the IPE.

<image src="../image/architecture.jpg">

#### Details of the installed environment
- Python3.9.11 (embedded)
  - numpy 1.22.4
  - matplotlib 3.5.2
  - opencv-python 4.5.5.64
  - opencv-contrib-python 4.5.5.64
  - mediapipe 0.8.10
  - msvc-runtime 14.29.30133
  - pyttsx3 2.90
- Visual Studio Code 1.67.1 (portable)
  - EvilInspector
  - Jupyter
  - Pylance
  - Python
  - Remote - Containers

## prerequisite
- Windows 10 or 11
- 8GB Memory or more
- 1.5GB HDD (C: drive)
- Webcam
- Uninstalling or stopping antivirus software
  - They may remove our installer and batch files.

## Setup both Python and VSCode with our installer
### procedure
- Download our installer file by clicking the following url.
  - https://oskit-my.sharepoint.com/:u:/g/personal/takao_jinno_oit_ac_jp/ETjlZJd8kyVMneqBBgjIZF4Bvif1w_ETaELJDmA7arJ6Ow?e=t02zsa
    - **PW is written on Slack.** [link to a Slack](https://ipbl2022.slack.com/archives/C03KMU22PCM/p1656481655111249)
    - If you have installed some antivirus software, this executable file and other batch files may not work properly.
- Execute "py22_ipbl_installer2022xxxx.exe" file.
  - This installer is safe.
  - **Even if the following warning pops up, execute it.**<br>
    <image src="../image/warning01.png" width="40%" height="40%"><br>
    <image src="../image/warning02.png" width="40%" height="40%"><br>
    - Please select `More info` and `Run anyway`.
- Choose "Yes".<br>
  <image src="../image/py22_ipbl_installer.png" width="30%" height="30%">
- This installer setup the image processing environment (Python3 + VSCode) into "C:\oit\py22_ipbl", and create link on your Desktop.

> **Note**
> Creating link to folder often fails. In that case, please go directly to "C:\oit\py22_ipbl". It is possible to create the link manually, but DO NOT move the folder!)

#### Installed folder structure
- installed folder "C:\oit\py22_ipbl"
  - **code**: work folder
  - python-3.9.11-embede-amd64: embedded python
  - VSCode-win32-x64-1.67.1:  portable visual studio code
  - **console.bat**: open the command prompt with python-3.9.11 settings
  - **vscode.bat**: open VSCode with python-3.9.11 settings
  - [hidden file] setup.bat: create the link of "py22_ipbl" on your Desktop
  - [hidden file] settings: support files for setup<br>
    <image src="../image/py22_ipbl_folder.png">

### :o:Checkpoint(Python version of Command Prompt)
- Execute "console.bat" file.
- Please confirm the Python version of Command Prompt.
  ```sh
  C:\oit\py22_ipbl\code>python --version
  Python 3.9.11
  ```

### :o:Checkpoint(Python pip command)
- If you have not opened Command Prompt, execute "console.bat" file.
- Please confirm pip command and Python modules.
  ```sh
  C:\oit\py22_ipbl\code>python -m pip list
  Package               Version
  --------------------- -----------
  ...(some module information)...
  matplotlib            3.5.2
  mediapipe             0.8.10
  msvc-runtime          14.29.30133
  numpy                 1.22.4
  opencv-contrib-python 4.5.5.64
  opencv-python         4.5.5.64
  packaging             21.3
  Pillow                9.1.1
  pip                   22.1
  protobuf              3.20.1
  pyparsing             3.0.9
  pypiwin32             223
  python-dateutil       2.8.2
  pyttsx3               2.90
  ...(some module information)...
  ```
- Please confirm pip install command.
  ```sh
  C:\oit\py22_ipbl\code>python -m pip install -U numpy
  Requirement already satisfied: numpy in c:\oit\py22_ipbl\python-3.9.11\lib\site-packages (1.22.4)
  ```
  - Update numpy if a newer version has already been released.

### :o:Checkpoint(Run python code with Command Prompt)
- If you have not opened Command Prompt, execute "console.bat" file.
- Please confirm that the sample python code is executable with command prompt.
  ```sh
  PS C:\oit\py22_ipbl\code>python hands.py
  ```
  - If it works normally, the webcam will start, and the shape of the hand will be recognized as shown below.<br>
    <image src="../image/hands.png" width="25%" height="25%">
  - If you want to stop this program, press "Esc" key while the preview window is active.

### :o:Checkpoint(EXTENSIONS of VScode)
- Execute "vscode.bat" file.
- If the following message is pop-up, please check "Trust the authors of all files in the parent folder 'py22_ipbl'" and choose "Yes, I trust the authors".<br>
  <image src="../image/warning_VSCode[first_time].png" width="50%" height="50%">
- If the following message pops up, please ignore message and close pop-up window **by clicking "x" button**.<br>
  <image src="../image/vscode_error.png" width="50%" height="50%">
  - This error happen when `EXTENSIONS` of VSCode lose the python path, but it works fine.
- Please confirm `EXTENSIONS` of VSCode
  - Click the following button (`EXTENSIONS` Tab button).<br>
    <image src="../image/Extensions_button.png" width="5%" height="5%">
  - Please confirm installed `EXTENSIONS`
    - EvilInspector
    - Jupyter
    - Pylance
    - Python
    - Remote - Containers

### :o:Checkpoint(Python version of VSCode)
- If you have not opened VSCode, execute "vscode.bat" file.
- If the Terminal of VSCode is not opened, open the New Terminal as follows.
  <image src="../image/vscode_new_terminal.png" width="50%" height="50%"><br>
  <image src="../image/vscode_terminal_path.png" width="50%" height="50%"><br>
- Please confirm python version of the Terminal of VSCode
  ```sh
  C:\oit\py22_ipbl\code>python --version
  Python 3.9.11
  ```

### :o:Checkpoint(Run python code with VSCode)
- If you have not opened VSCode, execute "vscode.bat" file.
- Please confirm that the sample python code is executable with VSCode.
  - Double click "hands.py" -> Open "hands.py"<br>
    <image src="../image/vscode_sample.png" width="50%" height="50%">
  - If the Terminal of VSCode is not opened, open the New Terminal as follows.<br>
    <image src="../image/vscode_new_terminal.png" width="50%" height="50%">
  - **At this time, make sure that the terminal path matches the parent directory of the Python code which you want to run.**<br>
    <image src="../image/vscode_terminal_hands.png" width="50%" height="50%"><br>
    - If necessary, move the directory by the `cd` command.
  - Please confirm that the sample python code is executable on the Tarminal of VSCode.
    ```sh
    C:\oit\py22_ipbl\code>python hands.py
    ```
  - If it works normally, the webcam will start, and the shape of the hand will be recognized as shown below.<br>
    <image src="../image/hands.png" width="25%" height="25%"><br>
  - If you want to stop this program, press "Esc" key while the preview window is active.
