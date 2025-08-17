# Packet structure over serial Communication

Messages starting with 0xBB and ending 0xEE byte

Message structure:
- 0 2 action
- 2 1 length
- 3 4 CRC32
- 7 1 type
- 8 n data
- 2 2 frame checksum

Response message header structure is the same, but CRC32 is calculated with the requesting message length, extra data is filled with zero on calculation.

Command bytes
- 0x80 0x71 request
- 0x71 0x80 response

### Request 0x0A - Boiler send data

- 0 2 action
- 2 1 length
- 3 4 CRC32
- 7 1 0xa
- 8 2 seq number
- 10 n data
- 2 2 frame checksum

sequence numbers observed:
0 `{~ITYPE":2}`
1 `{~APN":"apn"}`
2 `{~APNUN":"usr"}`
3 `{~APNPA":"pas"}`
4 `{~URL":"portal.centrometal.hr"}`
5 `{~UPORT":1883}`
6 `{~PROT":0}`
7 `{~MQUN":"usr"}`
8 `{~MQPA":"pas"}`
9 `{~MQID":"000"}`
10 `{"~MQPU":"cm.inst.cmpelet"}`
11 `{"~MQSU":"cm.srv.cmpelet"}`
12 `{"~KEY1":"158208e846"}`
13 `{"~KEY2":"65e0158208"}`
14 `{"~KEY3":"e84665e065"}`
15 `{"~KEY4":"e0158208e8"}`
16 `{"~WIFIN":"WiFi network"}`
17 `{"~WIFIPA":"WiFi password"}`
18 `{"~SERVFL":3}`
19 `{"~CUPORT":44300}`
20 `{"~SAVE":""}`
21 `{"wf_req":"?"}`

### Response 0x0A

-  0 2 0x71 0x80
-  2 1 5
-  3 4 CRC32
-  7 1 0xa
-  8 2 message sequence number
- 10 1 internet status info
- 11 1 wifi signal info

### Request 0x0B - Boiler request data

- 0 2 action
- 2 1 length
- 3 4 CRC32
- 7 1 0xa
- 8 2 seq number
- 2 2 frame checksum

### Response 0x0B

-  0 2 0x71 0x80
-  2 1 5 + data length
-  3 4 CRC32
-  7 1 0xb
-  8 2 message sequence number
- 10 1 internet status info
- 11 1 wifi signal info
- 12 n data

0 .. 9 `{"_MQTT_ID":"4EED90D0","_WIFI_VER":"v1.15"}`
10 .. data is empty

### Request 0x0C - Boiler sends data

- 0 2 action
- 2 1 length
- 3 4 CRC32
- 7 1 0xc
- 8 2 seq number
- 10 n data
- 2 2 frame checksum

sequence numbers observed:
0 {1 0 409 409 409 409 OFF 0 10}
1 {1 23 409 409 409 409 OFF 0 10}
2 {2 0 80000000}
3 {2 0 80000000}

### Response 0x0C

-  0 2 0x71 0x80
-  2 1 5
-  3 4 CRC32
-  7 1 0xc
-  8 2 message sequence number
- 10 1 internet status info
- 11 1 wifi signal info

### Request 0x0D - Boiler request data

- 0 2 action
- 2 1 length
- 3 4 CRC32
- 7 1 0xa
- 8 2 seq number
- 2 2 frame checksum

sequence numbers observed: 0, 2, 3, 4

### Response 0x0D

-  0 2 0x71 0x80
-  2 1 5 + data length
-  3 4 CRC32
-  7 1 0xd
-  8 2 message sequence number
- 10 1 internet status info
- 11 1 wifi signal info
- 12 n data
