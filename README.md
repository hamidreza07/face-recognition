# Face Recognition using OpenCV

This is a Python script that performs face recognition using the OpenCV library with the FaceDetectorYN and FaceRecognizerSF modules. The script detects faces in a given image or through your webcam and compares them with a reference face to determine if they match.

## Prerequisites

Make sure you have the following libraries installed:

- NumPy
- OpenCV (with the FaceDetectorYN and FaceRecognizerSF modules)

You can install these libraries using `pip`:

```bash
pip install numpy opencv-python opencv-contrib-python
```

## How to use

1. Ensure you have the required models:

   - Download the face detection model ("face_detection_yunet_2022mar.onnx") and the face recognition model ("face_recognition_sface_2021dec.onnx").
   - Place the downloaded models in the same directory as the script or provide the correct paths in the script.

2. Update the image path (if you want to perform face recognition on a specific image):

   ```python
   image1 = cv2.imread("path/to/image")
   ```

3. Run the script:

   ```bash
   python face_recognition.py
   ```

   The script will use your webcam to capture real-time video and perform face recognition on detected faces.

## How it works

1. The script loads the face detection model ("face_detection_yunet_2022mar.onnx") using the `cv2.FaceDetectorYN.create` function.

2. If an image path is provided, the script reads the image and resizes it to a fixed size.

3. The script detects faces in the image using the loaded face detection model.

4. The script loads the face recognition model ("face_recognition_sface_2021dec.onnx") using the `cv2.FaceRecognizerSF.create` function.

5. It aligns and crops the detected face in the reference image to extract facial features.

6. The script opens your webcam and starts processing real-time video frames.

7. For each video frame, it detects faces using the face detection model and aligns and crops the detected face to extract features.

8. It then compares the features of the detected face with the features of the reference face using the L2 (Euclidean) similarity metric.

9. If the L2 score is less than or equal to a threshold, it considers the faces as a match and draws a green bounding box around the detected face. Otherwise, it draws a red bounding box.

10. The processed frame is displayed in a window until you press the 'Esc' key to exit.

Note: Face recognition using a single reference face may not be accurate and is intended for demonstration purposes. In real-world applications, you would typically use a larger dataset of reference faces and more sophisticated face recognition algorithms to achieve better accuracy.