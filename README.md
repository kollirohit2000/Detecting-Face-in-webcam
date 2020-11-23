# Detecting-Face-in-webcam
Face detection uses computer vision to extract information from images to recognize human faces. In this project, we will learn how to create a face detection system using python in easy steps.The input to the system will be in real-time via the webcam of the computer.
Libraries to be installed
1.OpenCV (Open Source Computer Vision) library: It is built to help developers carry out tasks related to computer vision.
pip install opencv-python
2. dlib library: dlib is built through pre-trained models to locate the facial landmarks.
pip install dlib
3. face_recognition library: face_recognition is an open-source project, which is also known as the most straightforwardAPI for facial recognition.
pip install face_recognition

Import the libraries
import cv2
import face_recognition

Reference your system’s webcam
video_capture = cv2.VideoCapture(0)

We divide our video (real-time) into different frames. In each frame, we detect the location of the face using the APIs which we have imported above. For each face detected, we locate the coordinates and draw a rectangle around it and release the video to the viewer.
while True:
 # Grab a single frame of video
 ret, frame = video_capture.read()
# Convert the image from BGR color (which OpenCV uses) to RGB color (which face_recognition uses)
 rgb_frame = frame[:, :, ::-1]
# Find all the faces in the current frame of video
 face_locations = face_recognition.face_locations(rgb_frame)
# Display the results
 for top, right, bottom, left in face_locations:
 # Draw a box around the face
 cv2.rectangle(frame, (left, top), (right, bottom), (0, 0, 255), 2)
# Display the resulting image
 cv2.imshow(‘Video’, frame)
# Hit ‘q’ on the keyboard to quit!
 if cv2.waitKey(1) & 0xFF == ord(‘q’):
 break
 
 # Grab a single frame of video
 ret, frame = video_capture.read()
# Convert the image from BGR color (which OpenCV uses) to RGB color (which face_recognition uses)
 rgb_frame = frame[:, :, ::-1]
Here, we process one frame at a time. The frame is extracted using cv2 library which captures the frame in BGR (Blue-Green-Red) colors, while the face recognition library uses RGB (Red-Green-Blue) format. Hence we flip the color code of the frame.

face_locations = face_recognition.face_locations(rgb_frame)
Here, we locate the coordinates of the faces present in the frame. The list face_locations is populated with the x, y coordinates, and the width and height of the faces detected.

for top, right, bottom, left in face_locations:
# Draw a box around the face
cv2.rectangle(frame, (left, top), (right, bottom), (0, 0, 255), 2)
Here, we draw a rectangle around each of the faces captured. The rectangle starts at the x and y coordinates (left and top in this case), and extend up to the width and height of the face detected (right and bottom in this case). The codes (0, 0, 255) represent the color codes in B-G-R sequence.

 cv2.imshow(‘Video’, frame)
 if cv2.waitKey(1) & 0xFF == ord(‘q’):
 break
The resulting image (frame) is released to the viewer and the loop continues to run until the user hits the q key on the keyboard.

All captured videos must be released.
video_capture.release()
cv2.destroyAllWindows()
