# Amazon Web Services IoT MQTT Subscribe/Publish Example

This project shows an example of subcribing and publishing to AWS IoT with the MQTT protocol.

## Download the project 
```
git clone https://github.com/xinwenfu/platformio-espidf-aws-iot.git
```
## Load the project into VS Code

Load the project into VS Code: *File* -> *Open Folder ...*

## Things to configure

Run memuconfig to configure WiFi and AWS IoT end point: *PlatformIO Icon* -> *Project Tasks* -> *Platform* -> *Run Menoconfig*
- Example configuration
  - WiFi SSID
  - WiFi Password
- Component config 
  - Amazon web services IoT Platofrm
    - AWS IoT Endpoint Hostname

## Create policy at AWS IoT console
1. Log into AWS IoT console
2. Search and use *IoT Core* service
3. Secure
   - Policies -> Create policy
     - Policy name
     - Policy document. Use the following policy
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iot:Connect",
        "iot:Receive",
        "iot:Publish",
        "iot:Subscribe"
      ],
      "Resource": "*"
    }
  ]
}
```

## Create certificate at AWS IoT console
1. (Optional if already in AWS IoT console) Log into AWS IoT console
2. (Optional if already using IoT Core) Search and use *IoT Core* service
3. Secure
   - Certificate -> Add certificate -> Create certificate
     - Certificate -> Auto-generate new certificate (recommended)
     - Certificate status -> Active
       - Download certificates and keys. Download all certificates and keys. In particular, we need *Device certificate* and *Private key file*.
     - Click the created certificate and attach the created policy

## Change device certificate and key file within VS code
When the project is loaded into VS Code, there are three files under src->certs 
1. aws-root-ca.pem. No need to change
2. certificate.pem.crt. Replace its content with the content of downloaded *Device certificate*
3. private.pem.key. Replace its content with the content of downloaded *Private key file*

## Build, upload and serial monitor
Now build the project, and upload the firmware into ESP32. Use serial monitor to monitor the output from ESP32.

Within the IoT core console, use the Test -> MQTT test client. The project code publishes MQTT data to the topic *test_topic/esp32*. The MQTT test client can be used to publish and subscribe to *test_topic/esp32*.
