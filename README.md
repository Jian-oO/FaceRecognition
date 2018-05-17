# FaceRecognition
人脸识别活体检测


# CGIs list for JVT face camera

## History

| Version | Author | Date       | Description                   |
| ------- | ------ | ---------- | ----------------------------- |
| v0.1    | Qi Yao | 2018/04/11 | Create cgis document          |
| v0.2    | Qi Yao | 2018/04/20 | Update the IR mode parameters |
| v0.3    |Jian Zhu | 2018/05/09 | Update the Basic CTB,OSD Settings and Face Parameters |



##  Introduction

This document introduce some cgis command of JVT face camera and show how to use these cgis to adjust the video quality, IR cut.

## 1. Focus Cgis

Manually control Focus.

**Syntax**

```http
http://<server ipaddr>/cgi-bin/ptz_cgi?action=FocusAdd&<parameter>=<value>[&<parameter>=<value>…]
http://<server ipaddr>/cgi-bin/ptz_cgi?action=FocusSub&<parameter>=<value>[&<parameter>=<value>…]
```

| **Parameter** | Value     | Description                    |
| ------------- | --------- | ------------------------------ |
| steps         | 0-100     | The steps of controlling focus |
| user          | SnApAdm1n | user name                      |
| pwd           | XXXXXXXX  | password                       |

**Example**

```shell
#FocusAdd
http://192.168.55.88/cgi-bin/ptz_cgi?action=FocusAdd&steps=50&user=SnApAdm1n&pwd=SCARYSLRADLE

# FocusSub
http://192.168.55.88/cgi-bin/ptz_cgi?action=FocusSub&steps=50&user=SnApAdm1n&pwd=SCARYSLRADLE
```

**Return**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```



## 2. Zoom Cgis

Manually control zoom

**Syntax**

```http
http://<server ipaddr>/cgi-bin/ptz_cgi?action=<value>&user=<value>
&pwd=<value>
```

| **Parameter** | Value                | Description                              |
| ------------- | -------------------- | ---------------------------------------- |
| action        | ZoomAdd<br />ZoomSub | ZoomAdd：Zoom Up.<br /> ZoomSub：Zoom Down |
| user          | SnApAdm1n            | user name                                |
| pwd           | XXXXXXXX             | password                                 |

**example**

```http
http://<server ipaddr>/cgi-bin/ptz_cgi?action=ZoomAdd&user=SnApAdm1n&pwd=SCARYSLRADLE
http://<server ipaddr>/cgi-bin/ptz_cgi?action=ZoomSub&user=SnApAdm1n&pwd=SCARYSLRADLE
```

**return**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```



## 3.  Control IR detection mode

**syntax**

```http
http://<server ipaddr>/cgi-bin/camerasetting_cgi?action=set&InfraredDetectMode=videodetection[&<parameter>=<value>…]
```

| **Parameter**      | Value                                    | Description                              |
| ------------------ | ---------------------------------------- | ---------------------------------------- |
| InfraredDetectMode | videodetection<br />timedetection<br />IRdetection | 1：Video detection<br />2：Time detection <br />3:  IR detection |
| user               | SnApAdm1n                                | user name                                |
| pwd                | XXXXXXXX                                 | password                                 |

**example**

```http
http://192.168.55.88/cgi-bin/camerasetting_cgi?action=set&InfraredDetectMode=videodetection&user=SnApAdm1n&pwd=SCARYSLRADLE
```

**return**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```



## 4. Control IR CUT level

**syntax**

```http
http://<server ipaddr>/cgi-bin/videoparameter_cgi?action=set&TRCutLevel=low[&<parameter>=<value>…]
```

| **Parameter** | Value     | Description                              |
| ------------- | --------- | ---------------------------------------- |
| TRCutLevel    | low/high  | low：low level enable<br />high：high level enable |
| user          | SnApAdm1n | user name                                |
| pwd           | XXXXXXXX  | password                                 |

**example**：

```http
http://192.168.55.88/cgi-bin/videoparameter_cgi?action=set&TRCutLevel=low&user=SnApAdm1n&pwd=SCARYSLRADLE
```

**return**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```
## 5. Basic CTB

**Syntax**

```http
http://<server ipaddr>/cgi-bin/camerasetting_cgi?action=set&ColorToBlack=<value>[&<parameter>=<value>…]
```

| **Parameter** | Value     | Description                              |
| ------------- | --------- | ---------------------------------------- |
| ColorToBlack   | Color<br />Auto<br />Black | ColorToBlack=Color<br />ColorToBlack=Auto<br />ColorToBlack=Black |
| user          | SnApAdm1n | user name                                |
| pwd           | XXXXXXXX  | password                                 |

**Example**：

```http
http://192.168.55.88/cgi-bin/camerasetting_cgi?action=set&ColorToBlack=Color&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

## 6. OSD Settings

**Syntax**

```http
http://<server ipaddr>/cgi-bin/textoverlay_cgi?action=set&channel=<value>[&<parameter>=<value>…]
```

| **Parameter** | Value     | Description                              |
| ------------- | --------- | ---------------------------------------- |
| action   | get, set  | get = get the text overlay options.<br />set = set the text overlay options. |
| channel | 0~3 | The channel number of the video. |
| user          | SnApAdm1n | user name                                |
| pwd           | XXXXXXXX  | password                                 |
| Title | <string> | Valid characters are a thru z, A thru Z and 0 thru 9. |
| WeekValue | 0,1 | Whether to display the week, 0 - Do not show, 1 – Show. |
| TimeValue | 0,1 | Whether to display the time, 0 - Do not show, 1 – Show. |
| DateValue | 0,1 | Whether to display the date, 0 - Do not show, 1 – Show. |
| BitrateValue | 0,1 | Whether to display the bitrate, 0 - Do not show, 1 – Show. |
| TitleValue | 0,1 | Whether to display the title, 0 - Do not show, 1 – Show. |
| Color | 0~4 | The color of the font, 0-white, 1-black, 2-yellow, 3-red, 4-blue. |

**Example**：

```http
http://192.168.55.88/cgi-bin/textoverlay_cgi?action=set&channel=0&user=SnApAdm1n&pwd=DXLFYELRCBDB&Title=ipc&WeekValue=0&TimeValue=0&DateValue=0&TitleValue=0&BitrateValue=0
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

## 7. Face Parameters

**Syntax**

```http
http://<server ipaddr>/cgi-bin/faceparameter_cgi?action=<value>[&<parameter>=<value>…]
```
with the following parameters and values.

| **Parameter** | Value     | Description                              |
| ------------- | --------- | ---------------------------------------- |
| action   | get, set  | get = get Face parameters.<br />set = set Face parameters. |
| enable | 0,1 | the face detection switch. 0:Off,1:On |
| sensitivity | 0~10 | Default sensitivity is 4<br />The higher the sensitivity, the worse the quality of the captured pictures.<br /> The lower the sensitivity, the higher the quality of the captured picture. |
| snapMode | 0~4 | 0: Snap after leaving<br /> 1: Real-time snap<br />2: real time and Snap afte leaving(In seconds)<br />3: real time and Snap afte leaving(Farme as a unit)<br />4: A single mode |
| beatTime | 1~3 | Valid when setting snapMode=0,Defaults to 1 times<br />Description: From the time the person enters and leaves the screen, according to the maximum number of snap shots, select the best snapshot of the face to upload. Only if the face leaves the screen, the picture will be uploaded. If the face remains on the screen, the picture will not be uploaded. |
| TrackFrameNum | 1~1500 | Valid when setting snapMode=1,The default is 50.<br />Description:From the face into the screen start, detect 50 (real-time capture frame number) frame, select an optimal face photo upload.|
| IntervalTime | 1~30 | Valid when setting snapMode=2,The default is 2.<br />Description:After people enter the screen, according to the set time interval, every time will capture a face photo upload. |
| IntervalFrame | 1~1500 | Valid when setting snapMode=3,The default is 20.<br />Description:After the person enters the screen, according to the set interval frames, a snapshot of a person's face will be captured every certain number of frames. |
| GateIntervalFrame | 1~1500 | Valid when setting snapMode=4,The default is 30.<br />Description:Apply to the scene of the face lock machine. Many people over the gate, only to capture the front of that (the screen in the face of the largest pixel), according to the set of interval frame number, every frame number will capture a face photo upload. There's only one face frame in the picture. |
| faceMinPixel | 30~300 | The default is 80.<br />When the human face in the screen pixel points smaller than the set face recognition of the smallest pixel, will not be captured.|
| expansionCoeff | 0~10 | The default is 6.<br />This is used to adjust the size of the surrounding area of the captured face picture.<br />Value is 0: The captured image is just a face area.<br />Value is 6: The captured picture expands to the shoulder.  |
| faceScene | 0,1 | 0: Conventional scene,Suitable for normal environments.<br />1: Lobby scene,Suitable for backlit environments. |
| faceQuality | 1~99 |  The default is 99,The higher the value, the better the upload quality |
| originalQuality | 1~99 |  The default is 70,The higher the value, the better the upload quality |
| Trackmode | 0,1 | 0:Off<br />1:On,This parameter is used to display the face tracking box |
| PicMode | 0~2 | 0:Face Pictu<br />1:Original Pictu<br />2:Face and Original Pictu |
| PicPrefixEnable | 0,1 | 0:default<br />1: customize,Composed of letters and Numbers, 1 ~ 15 characters, case sensitive|
| PicPrefix | \<value> | Valid when setting PicPrefixEnable=1<br />PicPrefix=\<value>(Composed of letters and Numbers, 1 ~ 15 characters, case sensitive) |
| ResetFaceParam | 1 | Reset face param,restore defaults |
| user          | SnApAdm1n | user name                                |
| pwd           | XXXXXXXX  | password                                 |



### 7.1   Get face parameters



**Example**：

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=get&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.2  Face detection switch

**Example**：

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&enable=0&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.3  Capture sensitivity

**Example**：

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&sensitivity=4&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.4  SnapMode

**Example**：

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&snapMode=0&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

#### 7.4.1  beatTime(snapMode=0)

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&snapMode=0&beatTime=3&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

#### 7.4.2  TrackFrameNum(snapMode=1)

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&snapMode=1&TrackFrameNum=25&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

#### 7.4.3  IntervalTime(snapMode=2)

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&snapMode=2&IntervalTime=3&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

#### 7.4.4  IntervalFrame(snapMode=3)

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&snapMode=3&IntervalFrame=30&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

#### 7.4.5  GateIntervalFrame(snapMode=4)

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&snapMode=4&GateIntervalFrame=30&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.5  faceMinPixel

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&faceMinPixel=30&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.6  expansionCoeff

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&expansionCoeff=0&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.7  faceScene

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&faceScene=0&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.8  faceQuality

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&faceQuality=99&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.9  originalQuality

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&originalQuality=99&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.10  Trackmode

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&Trackmode=0&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.11  PicMode

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&PicMode=0&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.12  PicPrefixEnable

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&PicPrefixEnable=0&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```
#### 7.12.1  PicPrefix

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&PicPrefixEnable=0&PicPrefix=abcd&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```

### 7.13  ResetFaceParam

```http
http://192.168.55.88/cgi-bin/faceparameter_cgi?action=set&ResetFaceParam=1&user=SnApAdm1n&pwd=DXLFYELRCBDB
```

**Response**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```
