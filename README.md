# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1.<img width="1920" height="1080" alt="Screenshot 2025-10-27 184507" src="https://github.com/user-attachments/assets/4f00f1e5-dd40-4d3a-8791-752f1119bfb5" />
2.<img width="1920" height="1080" alt="Screenshot 2025-10-27 184609" src="https://github.com/user-attachments/assets/d5b3eede-26cc-4730-89f3-ae3c30b90858" />
3.<img width="1920" height="1080" alt="Screenshot 2025-11-03 104429" src="https://github.com/user-attachments/assets/8d63c8ca-bedb-480b-bf8e-ccc9416f1abe" />
4.<img width="1920" height="1080" alt="Screenshot 2025-10-28 094050" src="https://github.com/user-attachments/assets/86406cbd-fe85-4ef1-a5b6-dfc010aa3f4b" />
5.<img width="1920" height="1080" alt="Screenshot 2025-11-03 103306" src="https://github.com/user-attachments/assets/96eaa3b6-cbb9-4e88-8d0e-e943a66c248b" />
6.<img width="1920" height="1080" alt="Screenshot 2025-10-28 094106" src="https://github.com/user-attachments/assets/1297b234-2a5a-43d7-befb-e388602d17c0" />

## program:
```
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}    
```
## output:
CASE 1: LED ON
<img width="1034" height="468" alt="Screenshot 2025-11-16 173340" src="https://github.com/user-attachments/assets/ddb6d3f4-2b3a-4e71-9a74-147f19ea28b9" />

CASE 2: LED OFF
<img width="1036" height="468" alt="Screenshot 2025-11-16 173350" src="https://github.com/user-attachments/assets/fca33823-9d7e-4fe1-b272-de2a095a003d" />


## Result:
The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.
