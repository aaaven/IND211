### Arduino Basic Workshop  

#### by Dr. Aven Le ZHOU, 2025/26 S1

---

## What is Arduino?  
- open-source electronics prototyping platform  
- **microcontroller boards** + **software (IDE)**  
- interactive art, design, robotics, IoT, .etc  

----

#### Arduino UNO

![arudino uno](images/arduino.png)

----

## Arduino Boards  
- **Uno** – beginner-friendly, most common  
- **Nano** – compact, breadboard-friendly  
- **Mega** – more pins & memory  
- **Leonardo** – USB keyboard/mouse emulation  
- **ESP32** – WiFi/Bluetooth support  

----

#### [Arduino Boards Guides](https://www.dfrobot.com/blog-1540.html?srsltid=AfmBOooyno3QZObH8bNBupJTIXjaNhtBHoUY2MiDHn-fN6cUP0jIdwuo)


----

## Arduino IDE  
- Free software to write & upload code  
- Main parts:  
  - **Editor** → write sketches  
  - **Verify** → check errors  
  - **Upload** → send to board  
  <!-- - **Serial Monitor** → read sensor data   -->

----

### Verify → Upload
![verify](images/verify.png)

----

## Arduino Code Basics  

```cpp
void setup() {
  // runs once
}
void loop() {
  // runs continuously
}
```

**setup()** → initialization
**loop()** → runs forever


---

### Exercises Overview  

1. **Blink LED**  
   - Part A: Onboard LED / Part B: [External LED](https://mc.dfrobot.com.cn/thread-1042-1-1.html)

2. **Fading LED**  
   - [Breathing effect](https://learn.dfrobot.com/makelog-314842.html) + experiment with speed  

3. **Student Choice**  
   - [Hand Control Light](https://mc.dfrobot.com.cn/thread-321466-1-1.html?fromuid=864588)  / [Morse Code Light](https://learn.dfrobot.com/makelog-314840.html)  


