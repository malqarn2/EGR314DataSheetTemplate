# API


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
| received   | [12][6][3] |
| sent       | [13][6][1] |
