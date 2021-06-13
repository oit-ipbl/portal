# Python3 Environment
## prerequisite
- Windows 10
  - If you develop only the image processing part, there are no restrictions.
- 8GB Memory
- 1.5GB HDD

## requirements for iPBL
- Python3: version 3.8 or more
  - numpy
  - matplotlib
  - opencv-python: version 3.6 or more
  - opencv-contrib-python: version 3.6 or more
  - mediapipe: latest
  - msvc-runtime: latest version
  ```sh
  python -m pip install numpy opencv-python opencv-contrib-python mediapipe msvc-runtime
  ```
- **[recommend]** Visual Studio Code(VSCode)

#### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Mac user / students who are already completed to setup the python3 environment
- If you already have a python3 environment (3.8 or more version)
  - Please confirm requirements
  - This setting is competed, if the following sample code works fine on your python environment (it requires a webcam)
    - sample code: https://github.com/oit-ipbl/portal/blob/main/pythonEnv/hands.py
    ```python:hands.py
    import cv2
    import mediapipe as mp
    mp_drawing = mp.solutions.drawing_utils
    mp_hands = mp.solutions.hands
    
    # For webcam input:
    cap = cv2.VideoCapture(0)
    cv2.namedWindow('MediaPipe Hands', cv2.WINDOW_NORMAL)
    with mp_hands.Hands(
        min_detection_confidence=0.5,
        min_tracking_confidence=0.5) as hands:
        while cap.isOpened():
            success, image = cap.read()
            if not success:
                print("Ignoring empty camera frame.")
                # If loading a video, use 'break' instead of 'continue'.
                continue

            # Flip the image horizontally for a later selfie-view display, and convert
            # the BGR image to RGB.
            image = cv2.cvtColor(cv2.flip(image, 1), cv2.COLOR_BGR2RGB)
            # To improve performance, optionally mark the image as not writeable to
            # pass by reference.
            image.flags.writeable = False
            results = hands.process(image)

            # Draw the hand annotations on the image.
            image.flags.writeable = True
            image = cv2.cvtColor(image, cv2.COLOR_RGB2BGR)
            if results.multi_hand_landmarks:
                for hand_landmarks in results.multi_hand_landmarks:
                    mp_drawing.draw_landmarks(
                        image, hand_landmarks, mp_hands.HAND_CONNECTIONS)
            cv2.imshow('MediaPipe Hands', image)
            if cv2.waitKey(5) & 0xFF == 27:
                break
    cap.release()    
    ```
    - If it works normally, the webcam will start and the shape of the hand will be recognized as shown below.
      <image src="../image/hands.png" width="25%" height="25%">

## Setup Potable Python3 Environment
### prerequisite for this potable python3 environment
- Windows 10
- 8GB Memory
- 1.5GB HDD(C: dirve)

### procedure
- Download this installer file by clicking the following url.
  - https://oskit-my.sharepoint.com/:u:/g/personal/takao_jinno_oit_ac_jp/EcFXD1YzQypLrUurdhg4gEwBx97nmCg7WyYAQRQQ50Bqng?e=Mw2DDR
    - PW:**oit-siit**
    - If you have installed some antivirus software, this executable file and other batch files may not work properly.
- Execute "py21_installer.exe" file.
- Choose "Yes".<br>
  <image src="../image/py21_installer.png" width="30%" height="30%">
- This installer setup the portable python environment and the portable VSCode into "C:\out\py21", and create link on your Desktop.

### How to start
- installed folder "C:\oit\py21"
  - **code**: work folder
  - python-3.8.7: embedded python
  - VSCode-win32-x64-1.57.0:  portable visual studio code
  - **console.bat**:  open the command prompt with python-3.8.7 settings
  - **vscode.bat**: open VSCode with python-3.8.7 settings
  - [hidden file] setup.bat: create the link of "py21" on your Desktop
  - [hidden file] settings:  support files for setup<br>
    <image src="../image/py21_folder.png">
- **Command Prompt**
  - Execute "console.bat" file.
  - **How to install python modules**
  ```sh
  PS C:\oit\py21\code> python -m pip install [module]
  ```
- **VSCode**
  - Execute "vscode.bat" file.
  - if the following message is pop-up, please choose "Yes, I trust the authors".<br>
    <image src="../image/warning_VSCode[first_time].png" width="50%" height="50%">

### Let's execute sample python code!
- **Command Prompt**
  - Execute "console.bat" file.
  - Execute sample python code.
  ```sh
  PS C:\oit\py21\code> python hands.py
  ```
  - If it works normally, the webcam will start and the shape of the hand will be recognized as shown below.<br>
    <image src="../image/hands.png" width="25%" height="25%">
- **VSCode**
  - Execute "vscode.bat" file.
  - Double click "hands.py" -> Open "hands.py"<br>
    <image src="../image/vscode_sample.png" width="50%" height="50%">
  - If the Terminal of VSCode is not opened, open the New Terminal as follows.
    <image src="../image/vscode_new_terminal.png" width="50%" height="50%">
  - **At this time, make sure that the terminal path matches the parent directory of the Python code which you want to run.**<br>
    <image src="../image/vscode_terminal_path.png" width="50%" height="50%"><br>
    - If necessary, move the directory by the cd command.
  - Execute "hands.py" by clicking the following execution button.<br>
    <image src="../image/vscode_execute_button.png"><br>
  - If it works normally, the webcam will start and the shape of the hand will be recognized as shown below.<br>
    <image src="../image/hands.png" width="25%" height="25%">
