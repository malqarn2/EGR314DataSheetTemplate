# API

## Light Subsystem

My role is the Light Subsystem. I monitor ambient light using a photoresistor.

## Team Member IDs

| Individual | Subsystem Number |
|------------|------------------|
| Sam B      | 1                |
| Adrian P   | 2                |
| Andrew I   | 3                |
| Jacob D    | 4                |
| Sam M      | 5                |
| Mo A (me)  | 6                |

These tables describe the **message data portion** of each packet only.

---

## Messages Sent By The Light Subsystem

### Message Type 3 -- Print Sensor Value

**Number of Bytes:** 5

| Column name   | Byte 1       | Byte 2             | Byte 3         | Byte 4               | Byte 5               |
|---------------|--------------|--------------------|----------------|----------------------|----------------------|
| Variable Name | message_type | subsystem_number   | sensor_number  | upper_sensor_value   | lower_sensor_value   |
| Variable Type | uint8_t      | uint8_t            | uint8_t        | uint8_t              | uint8_t              |
| Min Value     | 3            | 6                  | 1              | 0                    | 0                    |
| Max Value     | 3            | 6                  | 1              | 255                  | 255                  |
| Example       | 3            | 6                  | 1              | 54                   | 176                  |

**Purpose:**  
Sends the raw light sensor value from the Light Subsystem.

**Notes:**  
- Byte 1 is the message type.  
- Byte 2 identifies the sending subsystem, which is `6` for the Light Subsystem.  
- Byte 3 identifies the sensor, which is `1` for the light sensor.  
- Bytes 4 and 5 contain the 16-bit sensor value split into upper and lower bytes.  
- Example value `54, 176` corresponds to decimal `14000`.

---

### Message Type 10 -- Alert Control Unit to Subsystem Error

**Number of Bytes:** 4

| Column name   | Byte 1       | Byte 2             | Byte 3      | Byte 4      |
|---------------|--------------|--------------------|-------------|-------------|
| Variable Name | message_type | subsystem_number   | error_code  | sender_num  |
| Variable Type | uint8_t      | uint8_t            | int8_t      | uint8_t     |
| Min Value     | 10           | 2                  | 0           | 6           |
| Max Value     | 10           | 2                  | 64          | 6           |
| Example       | 10           | 2                  | 10          | 6           |

**Purpose:**  
Sends an error code from the Light Subsystem to Adrian's control subsystem.

**Notes:**  
- Byte 1 is the message type.  
- Byte 2 identifies the destination subsystem, which is `2` for Adrian.  
- Byte 3 contains the error code.  
- Byte 4 identifies the sender, which is `6` for the Light Subsystem.  
- This message is sent when the Light Subsystem detects an error condition.

---

### Message Type 13 -- Alert Control to Subsystem Status

**Number of Bytes:** 4

| Column name   | Byte 1       | Byte 2             | Byte 3      | Byte 4       |
|---------------|--------------|--------------------|-------------|--------------|
| Variable Name | message_type | subsystem_number   | sender_num  | status_code  |
| Variable Type | uint8_t      | uint8_t            | uint8_t     | int8_t       |
| Min Value     | 13           | 2                  | 6           | 0            |
| Max Value     | 13           | 2                  | 6           | 10           |
| Example       | 13           | 2                  | 6           | 1            |

**Purpose:**  
Sends the Light Subsystem status to Adrian's control subsystem.

**Status Code Definition:**  
- `0` = No light detected  
- `1` = Light detected  

**Notes:**  
- Byte 1 is the message type.  
- Byte 2 identifies the destination subsystem, which is `2` for Adrian.  
- Byte 3 identifies the sender, which is `6` for the Light Subsystem.  
- Byte 4 contains the status code.

---

## Messages Directed To The Light Subsystem

### Message Type 12 -- Request Subsystem Status

**Number of Bytes:** 3

| Column name   | Byte 1       | Byte 2             | Byte 3 |
|---------------|--------------|--------------------|--------|
| Variable Name | message_type | subsystem_number   | code   |
| Variable Type | uint8_t      | uint8_t            | uint8_t |
| Min Value     | 12           | 6                  | 0      |
| Max Value     | 12           | 6                  | 15     |
| Example       | 12           | 6                  | 3      |

**Purpose:**  
Requests the current status of the Light Subsystem.

**Notes:**  
- Byte 1 is always the message type.  
- Byte 2 identifies the target subsystem, which is `6` for the Light Subsystem.  
- Byte 3 is a request code from the control subsystem.

---

## Valid Message Examples

| description | example |
|------------|--------|
| sent sensor value | [0x41][0x5A][6][0x58][3][6][1][54][176]...[0x59][0x42] |
| received status request | [0x41][0x5A][2][6][12][6][3]...[0x59][0x42] |
| sent status response | [0x41][0x5A][6][2][13][2][6][1]...[0x59][0x42] |
| sent error response | [0x41][0x5A][6][2][10][2][10][6]...[0x59][0x42] |

The software of this API download is available[here](https://github.com/user-attachments/files/26317978/API.PDF.pdf) .
