# API

## Light Subsystem

My role is the Light Subsystem. I detect ambient light levels using a photoresistor connected through an ADS1115 16-bit ADC. My subsystem reports light status to the rest of the system by converting the sensor reading into a simple binary result, where `0` means no light detected and `1` means light detected.

My subsystem communicates on the team UART daisy chain using subsystem ID `6`. I receive Message Type 12 from Adrian (ID `2`) when the control subsystem requests my current status. I then respond with Message Type 13, returning the processed light status code. Although the sensor is read internally as a `uint16_t` value in MicroPython, the transmitted API message uses a `uint8_t` status code.

## Team Member IDs

| Individual | Subsystem Number |
|------------|------------------|
| Sam B      | 1                |
| Adrian P   | 2                |
| Andrew I   | 3                |
| Jacob D    | 4                |
| Sam M      | 5                |
| Mo A (me)  | 6                |

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

## Messages Sent By The Light Subsystem

### Message Type 13 -- Alert Control to Subsystem Status

**Number of Bytes:** 3

| Column name   | Byte 1       | Byte 2             | Byte 3       |
|---------------|--------------|--------------------|--------------|
| Variable Name | message_type | subsystem_number   | status_code  |
| Variable Type | uint8_t      | uint8_t            | uint8_t      |
| Min Value     | 13           | 6                  | 0            |
| Max Value     | 13           | 6                  | 1            |
| Example       | 13           | 6                  | 1            |

**Purpose:**  
Returns the current status of the Light Subsystem to the control subsystem.

**Status Code Definition:**  
- `0` = No light detected  
- `1` = Light detected  

**Notes:**  
- Byte 1 is always the message type.  
- Byte 2 identifies the sending subsystem, which is `6` for the Light Subsystem.  
- Byte 3 contains the light status code.  
- The light sensor is read internally as a `uint16_t` value in MicroPython, then converted into a binary status code before transmission.  


- The light sensor value is read internally as a `uint16_t` in MicroPython, then converted into a binary status code for transmission.

## Valid Message Examples

| description | example |
|------------|--------|
| received   | [0x41][0x5A][2][6][12][6][3]...[0x59][0x42] |
| sent       | [0x41][0x5A][6][2][13][6][1]...[0x59][0x42] |

The software of this API download is available[here](https://github.com/user-attachments/files/26317978/API.PDF.pdf) .
