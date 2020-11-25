# Build a location-aware IoT Ecosystem with HERE and IBM Cloud

How IBMs IoT platform and HERE location services can help you visualize data coming from ioT devices

#### Sign up for IBM Cloud at https://ibm.biz/HERETechnologies
#### Get your Here Maps API Key at https://developer.here.com

## Prerequisites

- Code IDE
- Python 3.X (https://www.python.org/downloads/)
- HERE Developer Account (https://developer.here.com/sign-up?create=Freemium-Basic&keepState=true&step=account)
- IBM Cloud account (https://cloud.ibm.com/login)
- Bring your Coffee/Tea and enjoy the journey 

## Steps

### Step 1: Create IoT platform resource on IBM Cloud

This steps involves creating a virtual device on IBM cloud by selecting IOT Platform service from your IBM Cloud

### Step 2: Create Node-RED application on IBM Cloud

For connecting IoT device with IBM Cloud and send the data forward to user application, we are creating Node-RED application on IBM Cloud

### Step 3: Node flow in Node-RED

![Arch](/imgs/flow.PNG)

You can download the node structure from here - 

### Step 1: Python code for Visual Recognition

install Watson Developer Cloud library -
- pip install --upgrade "ibm-watson>=4.0.1"

```python
import json
from ibm_watson import VisualRecognitionV3
from ibm_cloud_sdk_core.authenticators import IAMAuthenticator

# # Passing API KEY and URL to the Visual Recognition
authenticator = IAMAuthenticator('IBM_API_KEY')

visual_recognition = VisualRecognitionV3(
    version='2018-03-19',
    authenticator=authenticator)

visual_recognition.set_service_url('IBM_URL') 

# Running the Visual Recognition on test.img file
with open('./test.jpg', 'rb') as image: 
    classes = visual_recognition.classify(images_file=image,threshold='0.6',classifier_ids='food').get_result()

#print(json.dumps(classes, indent=2))	
output_query = classes['images'][0]['classifiers'][0]['classes'][1]['class']
print(output_query)  
```
The above code will print "Pizza"

### Step 2: Integrating Flask in Python code

install Flask library -
- pip install flask


### Step 3: Show your location on a map

Create a folder 'templates' and create a file 'map.html' inside it.


### Step 4: Show pizza serving places on Map

Show pizza places around you on a map with a click of a button

An instance of Geocoding and Search Service

