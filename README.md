# FaceRecognition
人脸识别活体检测

# CGIs list for JVT face camera

## History

| Version | Author | Date       | Description                   |
| ------- | ------ | ---------- | ----------------------------- |
| v0.1    | Qi Yao | 2018/04/11 | Create cgis document          |
| v0.2    | Qi Yao | 2018/04/20 | Update the IR mode parameters |



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
http://192.168.55.88/cgi-bin/camerasetting_cgi?action=set&InfraredDetectMode=1&user=SnApAdm1n&pwd=SCARYSLRADLE
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
http://192.168.55.88/cgi-bin/videoparameter_cgi?action=set&mode=0&TRCutLevel=low&user=SnApAdm1n&pwd=SCARYSLRADLE
```

**return**

```http
HTTP/1.0 200 OK\r\n
Content-Type:text/plain\r\n
\r\n
OK\r\n
```



