# Dremel 3D40 Hacking
Notes on the Dremel 3D45.   
**I have no idea if any of this violates terms of use, law or warranty. Use this information at your own risk.**

## OS
OS details: Linux 2.6.32 - 3.5

## Open Port Scan:
PORT      STATE SERVICE VERSION  
23/tcp    open  telnet  utelnetd  
80/tcp    open  http  
10123/tcp open  unknown  
10124/tcp open  unknown  

## Port 23
A telnet service. Username and password unknown at this time.

##Port 80:
Webserver runnning an HTTP API  
  
###Endpoints
  **/command**     
  `POST /command HTTP/1.1  
  Accept: application/json, text/javascript, */*; q=0.01  
  Content-Type: application/x-www-form-urlencoded  
  Cache-Control: no-cache  
  
  GETPRINTERSTATUS=`
 
  return value: Current printer status  
  example return:  
 `{  
  "buildPlate_target_temperature":80,
  "chamber_temperature":38,
  "door_open":0,
  "elaspedtime":7617,
  "error_code":200,
  "extruder_target_temperature":255,
  "fanSpeed":0,
  "filament_type":"NYLON",
  "firmware_version":"v3.0_R02.03.04",
  "jobname":"",
  "jobstatus":"building",
  "layer":50,
  "message":"success",
  "networkBuild":1,
  "platform_temperature":80,
  "progress":41.799999999999997,
  "remaining":5338,
  "status":"busy",
  "temperature":252,
  "totalTime":10090
  }`
 
## Port 10123
The video HTTP JPEG stream using MJPG-Streamer [https://github.com/jacksonliam/mjpg-streamer]

### Endpoints
  **/**  
  add the querystring ?action=stream for the live stream. example: http://10.10.10.10:10123/?action=stream  
  
  **/index.html**  
  information about the streamer applet and links
  
  **/control.html**
  Change video settings including quality and exposure
  
  **/stream.html**
  Control and view the stream
  
  
  
