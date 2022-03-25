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

## Create certificate at AWS IoT Console
1. Log into AWS IoT console
2. Search and use *IoT Core* service
3. Secure
   - Certificate -> Add certificate -> Create certificate
     - Certificate -> Auto-generate new certificate (recommended)
     - Certificate status -> Active
       - Download certificates and keys. Download all certificates and keys. In particular, we need *Device certificate* and *Private key file*.

## Create policy at AWS IoT Console
1. (Optional if already in AWS IoT console) Log into AWS IoT console
2. (Optional if already using IoT Core) Search and use *IoT Core* service
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
## Replace local certificate and key file
1. certificate.pem.crt
2. private.pem.key
