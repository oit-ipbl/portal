## Python3 Environment
## requirements
- Python3: version 3.8 or more
  - numpy
  - matplotlib
  - opencv-python: version 3.6 or more
  - opencv-contrib-python: version 3.6 or more
  - mediapipe: latest
  - mvsc-runtime: latest version
- [recommend]Visual Studio Code(VSCode)

#### <font color="red">Checkpoint</font>
- If you already have a python3 environment (3.8 or more version)
  - Please confirm requirements
  - This setting is competed, if the following sample code works fine on your python environment (it requires a webcam)
    - sample code: https://github.com/oit-ipbl/portal/blob/main/pythonEnv/hands.py

## Set up Potable Python3 Environment
- Download this repository by clicking the following url.
  - https://oskit-my.sharepoint.com/:u:/g/personal/takao_jinno_oit_ac_jp/EcFXD1YzQypLrUurdhg4gEwBx97nmCg7WyYAQRQQ50Bqng?e=Mw2DDR
    - PW:oit-siit
    - If you have installed some antivirus software, this executable file and other batch files may not work properly.
- Execute "py21_installer.exe" file.
- Choose "Yes".<br>
  <image src="../image/py21_installer.png">
- This installer setup the portable python environment and the portable VSCode into "C:\out\py21", and create link on your Desktop.

## How to use
- installed folder "C:\oit\py21"
  - **code**: work folder
  - python-3.8.7: embedded python
  - VSCode-win32-x64-1.57.0: portable visual studio code
  - **console.bat**: open the command prompt with python-3.8.7 settings
  - **vscode.bat**: open VSCode with python-3.8.7 settings
  - [hidden file]setup.bat: create the link of "py21" on your Desktop
  - [hidden file]settings: support files for setup
  <image src="../image/py21_folder.png">
- Command Prompt
  - Execute "console.bat" file.
  - How to install python modules
  ```sh
  PS C:\oit\py21\code> python -m pip install [module]
  ```
- VSCode
  - Execute "vscode.bat" file.
  - if the following message is pop-up, please choose "Yes, I trust the authors".
  <image src="../image/warning_VSCode[first_time].png">
