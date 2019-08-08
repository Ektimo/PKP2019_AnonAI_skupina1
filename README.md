# AnonAI-skupina1

This branch contains implementation of an anonymization system for video files. The system automatically detects people's faces in video and blurs them using a filter. Face detection and blurring is supported both for live video feed from a webcam and existing video files in the local filesystem. The code was written in Python 3.6.

## Instructions

1. Clone this repository to your local filesystem
2. Make sure that you have the required dependencies installed (the versions specified below have been verified to be working with our code):
    * numpy v1.14.6
    * OpenCV v4.0.0
    * scikit-learn v0.20.1
    * matplotlib v3.0.2
    * mxnet v1.4.0: for best performance, we recommend running *mxnet* on a dedicated GPU (for the given *mxnet* version, installation of Cuda 9.2 is required). However, if you don't have a GPU, don't worry, all the functionality will still be available to you, but at a lower performance.
    
3. If you are using Insightface for face detection, the pretrained model can be downloaded from https://www.dropbox.com/s/tj96fsm6t6rq8ye/model-r100-arcface-ms1m-refine-v2.zip?dl=0
    * extracting the model should produce a *.json* and *.params* file. Both files should be located in the same directory.

4. Modify *model_path* in paths/paths.py file to point to the pretrained model files, which you have downloaded and extracted in the previous step:
    * relative *model_path* specification is supported from this project's root directory
    * append *'model'* to the model path
    * **example**: the downloaded and exctracted model is in the *models* directory, located on the same level as this project root directory:
        <pre>
        +--anonimizacijaPrvaSkupina
        |  +--paths
        |  |  +--paths.py
        |  +--other project files
        |
        +--models
            +--model-r100-ii
                +--model-0000.params
                +--model-symbol.json
        </pre>
        
        <code>model_path = "../models/model-r100-ii/model"</code>

5. Anonymization of existing video files
    * modify *video_path* in paths/paths.py to point to the video file that you want to anonymize
    * execute the conversion script in the project root directory: <code>python3 edit_video.py</code>
    * the anonymized video will be stored in the same directory as the input video with *'output_'* prepended to its name

6. Anonymization of live video feed from webcam
    * connect the webcam to your device via USB
    * execute the script in the project root directory: <code>python3 webcam_feed.py</code>
