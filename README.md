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

- You can download the node structure from here - https://github.com/vidhanbhonsle/Part-3-IBM-Oceania/blob/main/node_flow.txt
- After importing deploy the complete flow.
 
### Step 4: Python code for publishing data to IBM Cloud

With the help of MQTT protocol, data can be easily sent to the cloud. 

```python
#pip install paho-mqtt
import json
import paho.mqtt.client as mqtt
from time import sleep
from random import uniform

latitude = -37.77407606538453
longitude = 145.03173891068369

ORG = "YOUR_ID"
DEVICE_TYPE = "YOUR_TYPE" 
TOKEN = "YOUR_TOKEN"
DEVICE_ID = "UNIQUE_ID"

server = ORG + ".messaging.internetofthings.ibmcloud.com"
topicData = "iot-2/evt/data/fmt/json"
authMethod = "use-token-auth"
token = TOKEN
clientId = "d:" + ORG + ":" + DEVICE_TYPE + ":" + DEVICE_ID

mqttc = mqtt.Client(client_id=clientId)
mqttc.username_pw_set(authMethod, token)
mqttc.connect(server, 1883, 60)

while True:
    temperature = uniform(33.0,43.0)
    payloadData = json.dumps({"temperature":temperature,"latitude":latitude,"longitude":longitude})
    mqttc.publish(topicData, payloadData)
    print ("Published: " + "%s;%s/%s "%(temperature,latitude,longitude))
    sleep(5)
mqttc.loop()
```

### Step 5: Integrating Flask in Python code

install Flask library -
- pip install flask


### Step 3: Show your location on a map

Create a folder 'templates' and create a file 'map.html' inside it.


### Step 4: Show pizza serving places on Map

Show pizza places around you on a map with a click of a button

An instance of Geocoding and Search Service

