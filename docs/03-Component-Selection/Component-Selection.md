---
title: Module's Selected Major Components
---


## **Photoresistor/Light Sensor Subsystem**

### **Option 1: Off-the-Shelf TEMT6000X01 Ambient Light Sensor**
![TEMT6000](https://github.com/user-attachments/assets/6d9e2bb8-a6c4-425e-988e-90cb5e046574)  
$1.22 each  
[DigiKey: TEMT6000X01 Ambient Light Sensor](https://www.digikey.com/en/products/detail/digilent-inc/410-286/4840868?s=N4IgTCBcDaICoFECycBsAGTANdBGABAIIC2ARgJYCmAdgC74Ay5A5gBb0DKNAzgPYBOIALoBfIA)

**Pros**
* Small SMD package (1206) meets surface mount requirements
* Low cost and currently in stock with reliable supply chain
* Good sensitivity in visible light spectrum (400-700nm)
* 3.3V operation compatible with microcontroller ADC input range
* Fast response time (<15μs) suitable for dynamic rover environment
* Simple interface requiring only basic voltage divider circuit

**Cons**
* Not waterproof - requires complex custom enclosure for underwater use
* No built-in signal conditioning or temperature compensation
* Sensitive to infrared light (peak at 850nm) which dominates underwater
* Limited output voltage range may require amplification for ADC resolution
* Requires precise calibration for accurate light intensity measurements
* Datasheet lacks application notes for underwater environments

### **Option 2: Off-the-Shelf Vishay VEML7700 Digital Light Sensor**
![VEML7700](https://github.com/user-attachments/assets/aaeabacf-5f2f-44e7-a440-32bda7008c64)  
$2.98 each  
[DigiKey: VEML7700 High Accuracy Ambient Light Sensor](https://www.digikey.com/en/products/detail/adafruit-industries-llc/4162/9997696)

**Pros**
* I²C digital interface eliminates need for microcontroller ADC channel
* High accuracy (±10%) with excellent linearity across range
* Factory calibrated with integrated temperature compensation
* Very low power consumption (2μA in shutdown mode)
* Wide dynamic range (0-120klux) covers all expected light conditions
* Ambient light rejection improves accuracy in variable conditions

**Cons**
* Significantly more expensive than analog photoresistor options
* Requires allocation of I²C bus which may be limited on microcontroller
* Not waterproof - needs additional housing and sealing
* More complex software driver and calibration routines required
* SMD package (2.0×2.4mm) is smaller than recommended 0805 size
* Limited availability and longer lead times reported

### **Option 3: Custom GL5528 Photoresistor Circuit with Waterproof Housing**
![GL5528](https://github.com/user-attachments/assets/b1d07783-6e8e-4130-ad6d-9422af8b44d4)  
~$3.50 estimated BOM cost (excluding labor)
Components:
- GL5528 Photoresistor: $0.75 [DigiKey: GL5528 Photoresistor](https://www.digikey.com/en/products/detail/adafruit-industries-llc/161/7244927?gclsrc=aw.ds&gad_source=1&gad_campaignid=20232005509&gbraid=0AAAAADrbLlj1fnVHDFXcm9ZQE3CLO1GPB&gclid=Cj0KCQiAy6vMBhDCARIsAK8rOgn8fMz6UXPT-uEfW5XfMAOu1Ybf4zwVPDRpQ6ir3dRp-_qCq7aVhvcaAkxmEALw_wcB)
- Waterproof housing materials: ~$1.00

**Pros**
* Can achieve IP68 waterproof rating for reliable underwater operation
* Customizable spectral filtering for underwater light conditions (blue-green)
* Uses 0805 SMD resistors/capacitors meeting EGR 314 requirements
* Lower unit cost than commercial underwater-specific sensors
* Buffered output provides stable 0-3.3V range for microcontroller ADC
* Easy to calibrate for specific water turbidity and depth conditions
* Mechanical design can be optimized for rover mounting and cleaning

**Cons**
* Requires custom PCB design, assembly, and testing time
* Needs individual calibration of each sensor unit
* Waterproofing adds mechanical complexity and assembly steps
* Larger overall footprint than commercial SMD sensors
* Requires epoxy potting process with potential reliability concerns
* Temperature compensation must be implemented in software
* Longer development timeline compared to off-the-shelf solutions

---

**Choice:** **Option 3: Custom GL5528 Photoresistor Circuit with Waterproof Housing**

**Rationale:** The underwater rover application demands a waterproof sensor, which commercial light sensors do not provide without significant modification. The custom GL5528 solution allows us to create a fully submersible sensor (IP68 rating) specifically optimized for underwater light penetration, where blue-green wavelengths (450-550nm) dominate. While requiring more initial design effort, this approach provides better long-term reliability underwater, allows customization for our specific depth and water conditions. The total cost ($3.50) remains reasonable compared to commercial underwater sensors (typically $50+), and the design can be easily scaled for multiple rover units.

---

## **3.3V Power Regulation Subsystem** 

### **Option 1: LM1085ISX-3.3-NOPB LDO Regulator**
![Image](https://github.com/user-attachments/assets/c201f543-9108-4bdd-a9b2-2cd5053df6d5)

**$3.45 each**  
[DigiKey: LM1085ISX-3.3-NOPB LDO Regulator](https://www.digikey.com/en/products/detail/texas-instruments/LM1085ISX-3-3-NOPB/366710) 


**Pros**
- **Surface-mount D²PAK (TO-263) package** – meets our SMD assembly requirements, no through-hole parts
- High output current: **3A** continuous, ample headroom for all sensors + MCU + peripherals
- Low dropout voltage: **1.3V max at 3A** – operates from 4.6V input for 3.3V out
- Fixed 3.3V output, no adjustment resistors needed
- Wide input voltage range: up to **27V** – compatible with 9V/12V/24V systems
- Excellent line/load regulation: 0.015% typical
- Built-in protection: thermal shutdown, current limit, safe area protection
- Low quiescent current: **5mA typical** at full load
- Stable with low-ESR ceramic output capacitors
- Industry-standard D²PAK footprint, compatible with reflow soldering

**Cons**
- **Higher cost**: $3.45 – significantly more expensive than AP2112 or LM2940
- Still a **linear regulator**: efficiency only ~37% with 9V input at 3.3V out
- **Significant heat dissipation at high current**: 3A load = 17.1W power dissipation – requires **heatsinking even in SMD package**
- Larger SMD package than SOT-23 LDOs, consumes more PCB area
- Not adjustable; fixed 3.3V version only
- Higher quiescent current than modern CMOS LDOs (AP2112: 60µA)
- Overkill for low-power sensor applications (600mA vs our ~200mA load)
- D²PAK requires proper PCB copper pour for thermal management

---


### **Option 2: LM7805CT-NOPB Linear Regulator**
![LM7805CT](https://github.com/user-attachments/assets/27e006c2-1af3-44d2-a514-25bb346cb301)

**$1.80 each**

[DigiKey: LM7805CT-NOPB Linear Regulator](https://www.digikey.com/en/products/detail/texas-instruments/LM7805CT-NOPB/3901929)



**Pros**
* Very rugged and proven design with decades of field history
* Wide input voltage range (7V to 25V) ideal for 9V battery/supply operation
* High output current capability (1.5A max) for powering multiple sensors
* Excellent thermal shutdown and short-circuit protection built-in
* Through-hole TO-220 package is extremely easy to prototype on breadboards
* No external passives required for basic operation
* Industry-standard pinout, widely available and second-sourced
* Junction temperature range up to +125°C for robust operation


**Cons**
* Much higher dropout voltage (2V) requires minimum 7V input for 5V out
* Linear efficiency only ~55% at 9V input (worse than AP2112 for lower Vout)
* Large through-hole package consumes significant board space
* No adjustable version; fixed 5.0V output only
* Significant heat generation: at 500mA load with 9V input, power dissipation is 2W
* Requires heatsink for currents above ~300mA in ambient temperatures
* Higher quiescent current (5mA typical) than modern LDOs or switchers
* Output noise and ripple rejection inferior to low-noise LDOs for analog circuits

---

### **Option 3: LM2575T-3.3G Switching Regulator**
![LM2575T](https://github.com/user-attachments/assets/26bf1b16-a4f2-4a0a-b779-7738411228d3)

**$2.78 each**
gived in class
[DigiKey: LM2575T-3.3G Switching Regulator](https://www.digikey.com/en/products/detail/onsemi/LM2575T-3-3G/1476700) 

**Pros**
* High efficiency step-down (buck) regulator: ~78% efficient with 9V input
* Significantly less heat generation than linear regulators (0.45W at 200mA)
* Wide input voltage range: 4.75V to 40V, highly versatile for various supplies
* Fixed 3.3V output with ±4% tolerance over line/load/temperature
* 1A output current capability sufficient for most sensor suites
* Built-in thermal shutdown and current limit protection
* Simple circuit requires only 4 external components
* Through-hole TO-220 package with 5 leads, breadboard-friendly
* 52 kHz fixed frequency oscillator—avoids noise issues in audio bands


**Cons**
* Higher cost than equivalent LDO solutions (≈4× price of AP2112)
* Larger footprint: requires external inductor and Schottky diode
* Output ripple voltage (50mV typical) may need post-filtering for sensitive analog sensors
* Slower transient response compared to LDOs
* Through-hole package only—no SMD option in this fixed voltage variant
* Bulky external inductor (330µH) consumes significant board space
* Not adjustable; requires different part number for other voltages
* Higher quiescent current (5mA typical for I<sub>Q</sub> + 2.5mA for I<sub>adj</sub>) than modern switchers

---

**Choice:** **Option 1: LM1085ISX-3.3-NOPB LDO Regulator**

**Rationale:** Surface-mount compatibility is the primary requirement for our power rail. The LM1085ISX-3.3-NOPB comes in a D²PAK package, making it fully reflow-compatible with our SMD assembly process. Its 3A output provides substantial headroom for all sensors and the microcontroller. While it is a linear regulator, our typical 200mA load keeps dissipation under 1.3W—manageable with proper PCB copper pouring. Built-in thermal shutdown and current limit protect against faults. Although the $3.45 unit cost is higher than through-hole alternatives, this part eliminates manual soldering and keeps our bill of materials fully surface-mount.

---

## **Connector Subsystem**

### **Option 1: JST XH Series 3-Pin Connectors**
![JST XH](https://github.com/user-attachments/assets/d8b40aae-004c-40d3-8930-7b5fc257a02f)
$0.45 each (connector) + $1.00 (housing)  
[DigiKey: JST XH 3-Pin Connector](https://www.digikey.com/en/products/detail/jst-sales-america-inc/B3B-XH-A-LF-SN/1651037)

**Pros**
* Polarized design prevents incorrect connection
* Locking mechanism secures connection against vibration
* 3A current rating per contact provides good margin
* Standard in robotics and industrial applications
* Available with pre-crimped cables
* Reliable and durable construction

**Cons**
* Through-hole mounting only (not SMD)
* Requires crimping tool for custom cables
* Larger footprint than plain headers
* Additional cost for housing and pins
* More complex assembly process
* Limited to specific wire gauges
---
### **Option 2: Sullins PPTC Series Pin Headers**
![PPTC Headers](https://github.com/user-attachments/assets/23cd9246-31e1-4071-9b63-c75e32c29e7c)
$0.32 per 10-pin strip  
[DigiKey: Sullins PPTC101LFBN-RC Header](https://www.digikey.com/en/products/detail/sullins-connector-solutions/PPTC101LFBN-RC/810149)

**Pros**
* Very low cost per connection
* Breakable to any pin count needed
* Available in SMD version (PPTC091LFBN-RC)
* Easy to prototype and modify
* Compatible with standard jumper wires
* Simple through-hole assembly

**Cons**
* Not polarized - can be inserted backwards
* No locking mechanism
* Less secure in high-vibration environments
* Limited current rating (≈1A per pin)
* Exposed pins can short if not careful
* Less professional appearance

---

**Choice:** **Option 1: JST XH Series 3-Pin Connectors**

**Rationale:** The rover will operate in environments with vibration and movement, making secure connections critical. JST XH connectors provide polarization to prevent incorrect wiring, a locking mechanism to prevent disconnection, and a 3A rating that exceeds our power requirements. While through-hole and requiring a crimping tool, their reliability in robotics applications justifies the departure from SMD preference. The connectors are standard in the industry, making replacement cables readily available, and the cost remains reasonable for the reliability provided.

---

## **Barrel Jack Connector**

### **Option 1: Model 0930 9V 3A AC-DC Wall Power Supply(given in class)**
In class 

**Pros**
* Exact voltage specification (9V DC) matches our system requirements
* High current capacity (3A) provides ample power margin for all rover subsystems
* Universal input voltage (100-240VAC) works worldwide without modification
* Standard barrel jack connector compatible with our chosen PJ-102AH receptacle
* 27W total power exceeds our estimated maximum power consumption
* Compact and lightweight design suitable for rover field operation
* No additional voltage conversion required for our LDO regulator input

**Cons**
* No specific manufacturer or datasheet available (generic model)
* May not have proper safety certifications (UL/CE) depending on supplier
* Quality and reliability may vary between suppliers
* Limited warranty or technical support for generic power supplies
* May generate electrical noise that could interfere with sensitive analog circuits
* Fixed output voltage cannot be adjusted if design changes require different voltage

### **Option 2: Kycon KLDX-0202-B-C SMD Barrel Jack**
![KLDX-0202](https://github.com/user-attachments/assets/77b86c58-60cf-477f-b2a5-bb5c0fa8d8db)
$0.69 each  
[DigiKey: Kycon KLDX-0202 SMD Barrel Jack](https://www.digikey.com/en/products/detail/kycon-inc/KLDX-0202-BC/9990097?s=N4IgTCBcDaINIE8DGB7AdgAjgGQCIA0BaABjFMICFCBhEAXQF8g)

**Pros**
* SMD mounting compatible with automated assembly
* Low profile design (6.0mm height)
* Same 5.5×2.1mm standard size
* RoHS compliant and lead-free
* Better for high-volume production
* Cleaner PCB assembly

**Cons**
* More than 2.5× the cost of PJ-102AH
* Less mechanical strength than through-hole
* Requires precise PCB placement
* Limited mechanical strain relief
* Less common in hobbyist projects
* Potential reliability concerns with repeated insertion

---

**Choice:** **Option 1**: Model 0930 9V 3A AC-DC Wall Power Supply

**Rationale**:
The rover requires a dependable and precisely regulated power source for consistent operation in field conditions. This supply provides the exact 9V output needed by our voltage regulator, eliminating any additional voltage conversion circuitry. Its 3A capacity offers substantial headroom above our maximum power requirements, ensuring reliable performance under load. While a generic model without formal certifications, its universal AC input (100–240V) supports worldwide operation, and the standard barrel jack connects directly to our PJ-102AH receptacle. The balance of exact voltage matching, ample power margin, and straightforward integration justifies selecting this option for our prototyping needs.

---
