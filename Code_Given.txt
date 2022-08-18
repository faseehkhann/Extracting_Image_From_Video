from matplotlib import pyplot as plt
import numpy as np
import numpy
import cv2
cap = cv2.VideoCapture('C:\\Users\\faseeh khan\\Desktop\\Final Year Project\\Distorted Videos\\Distorted videos\\Compression\\Airport_D9_1.mp4') # Capturing the video from a file by sepcifying it's location
length = int(cap.get(cv2.CAP_PROP_FRAME_COUNT)) # Tell's Us about the Number of frames present in a video
k = []
while True:
    ret, frame = cap.read()
    if ret:
        k.append(frame)
        # print("Printng Values of each frame:",k) 
        # if you want to Print Each Frame Value just uncomment the upper line
        cv2.waitKey(10)
        continue
    else:
        break
for i in range ((len(k))):
    if i==200: #   ***Important*** YOu can give any frame value from which you want to extract Image I gave 200
        print("Printing Value of 200 Frame only",k[i]) # Printing Value of 200 Frame only
        flatten_list = list(numpy.concatenate(k[i]).flat)
        im = np.array(flatten_list, dtype=np.uint8)
        im.resize(1080,1920,3) 
        plt.imshow(im)
        plt.show()  # Ploting Image of that 200 Frame
        break
    else:
        continue
cap.release()
cv2.destroyAllWindows