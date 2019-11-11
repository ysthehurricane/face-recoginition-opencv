1)import cv2
cap = cv2.VideoCapture(0)

while True:
    
    #capture frame by frame 
    check , frame = cap.read()
    
    cv2.imshow('frame',frame)
    
    key = cv2.waitKey(0)
    
    if key == ord('q'):
        break
        
# When everything done , release the capture
cap.release()
cv2.destroyAllWindows()


2)copy  Haar cascades file to your project file

	print(cv2.__file__)
	c:\users\yash\appdata\local\programs\python\python35\lib\site-packages\cv2\
	copy data folder to your project folder
	

3)use face classifier
	face_cascade = cv2.CascadeClassifier('data/haarcascade_frontalface_alt2.xml')

4)convert frame into gray scale image
	    gray = cv2.cvtColor(frame,cv2.COLOR_BGR2GRAY)
		cv2.imshow('frame',gray)
		
		
5)detect face area of entire photograph

	faces = face_cascade.detectMultiScale(gray,scaleFactor=1.5,minNeighbors=5)
    
    for (x,y,w,h) in faces:
        
        print(x,y,w,h)
        #roi = region of interest 
        
		roi_gray = gray[y:y+h,x:x+w]
       roi_color = frame[y:y+h,x:x+w]
	   
		image_item = "my-image.jpg"
        cv2.imwrite(image_item,roi_gray)
		
		
6)make a rectangle on face		
		
		color = (255,0,0) #color 
        stroke = 3 #thickness of rectangle
        cv2.rectangle(frame,(x,y),(x+w,y+h) , color,stroke) #rectange

TRAIN MODEL
		
how to recognize ? deep learned model predict through keras , tensorflow , pytorch , scikit learn		

7)locate the images folder path where the data store
	
	import os

	#location of base directory
	base_dir = os.path.dirname(os.path.abspath('__file__'))
	#base_dir

	#location of image folder directory
	image_dir = os.path.join(base_dir,"images")
	image_dir
		
		
8)enter into image folder
9)put condition to take only jpg , png
10)convert folder name to appropriatly 
	label = os.path.basename(os.path.dirname(path)).replace(" ","-").lower()

11)convert image into grayscale
12)store image value into numpy array 
13)detect face area and store image value into x_train

14)creating labels id

15)store labels into pickle file