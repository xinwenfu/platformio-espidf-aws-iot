# Amazon Web Services IoT MQTT Subscribe/Publish Example

This project shows an example of subcribing and publishing to AWS IoT with the MQTT protocol.

## Download the project and load it into VS Code
```
git clone https://github.com/xinwenfu/platformio-espidf-aws-iot.git
```

Load the project into VS Code: *File* -> *Open Folder ...*

## Things to configure

Run memuconfig to configure WiFi and AWS IoT end point: *PlatformIO Icon* -> *Project Tasks* -> *Platform* -> *Run Menoconfig*
- Example configuration
  - WiFi SSID
  - WiFi Password
- Component config 
  - Amazon web services IoT Platofrm
    - AWS IoT Endpoint Hostname

## Create certificate, policy at AWS IoT

## Replace local certificate and key file
1. certificate.pem.crt
2. private.pem.key
