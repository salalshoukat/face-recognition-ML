!pip install face_recognition==1.3.0

# import necessary libraries
from PIL import Image
# PIL : Python imgaging library, image module allows reading and writing images with PIL
from PIL import ImageDraw
# provides simple 2D graphics support for image object
import face_recognition
# Find and manipulate facial features in pictures
(REquires GPU)
from google.colab import files
files.upload()

#loads an image file (.jpg , png, etc ) into a numpy 
arrayimage = face_recognition.load_image_file("pexels-photo-6514796.jpeg") # Return a list of face locations in which each face locate

#find all the faces in an 
imageface_locations= face_recognition.face_locations(image) # Returns a list of face locations in which each face location is a tuple pf pixe 
print(face_locations)

#loop over each face for location in face_locations:
#print the locations of each face in the image 
 Top,right,bottom,left= location  
print("Top: {}, right:{}, bottom:{}, left: {}".format(Top,right,bottom,left))

#number of faces in the image 
numFaces=len(face_locations) 
print(numFaces)

#load the image into a python image library object 
Pil_image=Image.fromarray(image) #convert array to image

#loop over each face 
for location in face_locations: 

Top,right,bottom, left = location  #Draw a box around the face  
draw=ImageDraw.Draw(Pil_image) # Create a Draw object  
draw.rectangle([left, Top, right, bottom], outline='red', width=2) #Use rectangle drawing method

from matplotlib.pyplot import imshow  
imshow(Pil_image) #Display data as an image

#find all the facial features in all the faces in the image
face_landmarks_list=face_recognition.face_landmarks(image) #returns a dict of face feature locations ( eyes,nose,mouth,lips,etc) print(face_landmarks_list)

#loop over each face
for landmark in face_landmarks_list:

#loop over each facial features (eye,nose, mouthm lips etc)  
for landmark_name, list_of_points in landmark.items(): # items(): returns a view object that displays a list of 

#print the location of each facial feature in this image    
print("The {} in this face has the following points: {}".format(landmark_name,list_of_points))

#tace out each facial features in the image with a line
draw.line(list_of_points, fill="blue", width=2) #Draw a line between the coordinates

imshow(Pil_image)

#generate the face encoding
#face encoding: A set of 128 measurements pertaining to facial 
face_encodings = face_recognition.face_encodings(image)
