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

1. Open **STM32CubeIDE**.

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/654aed41-5802-4007-9db5-d734a75ea3b2" />

2. Click **File → New STM32 Project**.
   
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/b68b28f2-ac36-41c1-8222-c8cab6b0f960" />

3. Select the **target microcontroller** or board and click **Next**.
   
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/be91095c-b0ee-4a8e-ba03-c046213624cd" />

4. Name the project.
   
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/01bdc052-be53-450b-b7fa-9f16aef70709" />

5. The corresponding `.ioc` file will be generated automatically.
  
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/788b10c0-2417-4a49-b7a6-b6d2fd82950e" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/de040c82-078f-4594-98fe-52de6d375187" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  
 <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/08541612-c7a9-4b94-bb6c-d468c830e627" />

8. Edit the generated main program as required.
   
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/f4e101d8-0c8f-4fad-b024-5c50074d0eeb" />
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/0615a1b5-8518-4a3d-9f32-8e69efd0bf3b" />

9. Click **Project → Build All**.

 <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/e1725c6f-3e7f-4d1f-9598-cc42fbb54ce8" />
   
10. Link the **HEX file** using the post-build process.
    
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/449599f2-bcee-470c-81d0-c6d21ab41f1c" />

11. Click **Debug** and connect the **STM Nucleo Board**.
    
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/c9396fde-b426-4bd9-b99f-8b4b8a8ccfc7" />

12. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
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
---
### OUTPUT
CASE 1: LED ON 

<img width="1280" height="576" alt="ON2" src="https://github.com/user-attachments/assets/bd660c0a-ebe7-4f45-87da-b5514cea01f8" />

CASE 2: LED OFF

<img width="1280" height="576" alt="OFF2" src="https://github.com/user-attachments/assets/252c81f1-1c7d-4830-b453-bb985c1b3a6d" />

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




