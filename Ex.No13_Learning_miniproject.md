# Ex.No: 10 Learning – Use Supervised Learning  
### DATE:  08-05-2024                                                                          
### REGISTER NUMBER : 212221060070
### AIM: 
To create virtual mouse
###  Algorithm:

### Program:
~~~
import cv2
import mediapipe as mp
import pyautogui
cam = cv2.VideoCapture(0)
face_mesh = mp.solutions.face_mesh.FaceMesh(refine_landmarks=True)
screen_w , screen_h = pygautogui.size()
while True:
    _, frame = cam.read()
    frame = cv2.flip(frame, 1)
    rgb_frame = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
    output = face_mesh.process(rgb_frame)
    landmark_points = output.multi_face_landmarks
    frame_h, frame_w, _ = frame.shape
    if landmark_points:
        landmarks = landmark_points[0].landmark
        for id, landmark in enumerate(landmarks[474:478]):
            x = int(landmark.x * frame_w)
            y = int(landmark.y * frame_h)
            cv2.circle(frame, (x,y), 3,(0,255,0))
            if id == 1:
                            screen_x = screen_w / frame_w * x
                            screen_y = screen_h  / frame_h*y
                            pyautogui.moveTo(screen_x , scren_y)
             left = [landmarks[145],  landmarks[159]]
             for landmark in left:
                              x = int(landmark.x * frame_w)
                              y = int(landmark.y * frame_h)
                              cv2.circle(frame, (x,y), 3,(0,255,255))
                     if(left[0].y - left[1].y) <0.004:
                               pyautogui.click()
                               pyautogui.sleep(1)
    cv2.imshow('Virtual Mouse',frame)
    cv2.waitKey(1)
~~~

### Output:
![image](https://github.com/Gowtz07/AI_Lab_2023-24/assets/115936520/5ef0982c-703a-47bb-a23b-54cbce00cdaa)

### Result:
Thus the system was trained successfully and the prediction was carried out.
