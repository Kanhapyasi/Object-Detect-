## Work Flow
 
#### <img width="452" alt="image" src="https://github.com/user-attachments/assets/37f5bd35-e83e-499d-a157-70441100cfa0" />


## Step 1: Setting Up the AI Backend (FastAPI)
The AI backend is built using FastAPI, which is responsible for handling object detection requests. Here’s how implemented it:
##### 1.Loaded a lightweight object detection model (YOLOv8)
##### 2.Created an API endpoint (/detect) to accept image files
##### 3.Processed the image using OpenCV and YOLO model
##### 4.Returned JSON response with detected object labels and confidence scores
The backend was containerized using Docker, making it portable and easy to deploy.

## Step 2: Implementing Object Detection in AI Backend
Use the YOLOv8 model from Ultralytics for object detection. The image is read, converted into an array, and passed through the model for prediction.
Code Snippet in main.py:
## Step 3: Creating the Frontend UI (Flask)
The UI is built using Flask, which provides a user-friendly interface for uploading images.
Once an image is uploaded, it is sent to the AI backend for processing, and the response is displayed in the UI.
 Features of the Flask Frontend
•	Users can upload an image
•	The image is sent to FastAPI backend for processing
•	Bounding box results are displayed on the UI
•	JSON results are parsed and displayed in a readable format
 Code Snippet in app.py:

## Step 4: Displaying Results on UI
Modify the result.html template to display the original along with detected object names and JSON scores.
Code Snippet in result.html:

## Step 5: Running the Application
Containerize the FastAPI backend and Flask frontend using Docker so that the system can run on any machine without additional dependencies.
### Commands to Run the Project
#### 1. Start the AI backend:
uvicorn main:app --reload 
#### 2. Start the UI frontend:
python app.py
#### 3. Open a browser and go to:
http://127.0.0.1:5000


 
## Step 6: Dockerizing the Application
Create separate Dockerfile configurations for both the backend and frontend, then orchestrated them using docker-compose.yml.

## Step 7: Testing API via CURL
You can also test the backend API using curl to check if the AI detection service is working properly.
 

#### CURL Command
Bash
CopyEdit
curl -X POST "http://127.0.0.1:8000/detect" \
     -H "accept: application/json" \
     -H "Content-Type: multipart/form-data" \
     -F "file=@/path/to/test_image.jpg


   
