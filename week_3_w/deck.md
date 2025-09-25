#### Week 3 Workshop Arduino Simon Says

##### By *Dr. [Aven Le ZHOU](https://www.aven.cc)*, 2025

---

### 🎥 What is Simon Says?

<iframe width="1000" height="562.5" 
  src="https://www.youtube.com/embed/1Yqj76Q4jJ4?si=W6475OhM34tVEC3i" 
  frameborder="0" 
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
  allowfullscreen>
</iframe>

----

### 🧩 What is Simon Says?
- Memory game with lights (and sound)  
- Device plays a sequence → player repeats  
- Sequence grows each round  
- Wrong input = Game Over  

----

### 🎥 The "Arduino" Version

<iframe width="800" height="450" 
  src="https://www.youtube.com/embed/xLLTxN_UBnI" 
  frameborder="0" 
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
  allowfullscreen>
</iframe>

---

### 🛠 Components
- Arduino Uno (or compatible)  
- Breadboard + jumper wires  
- 4 LEDs (different colors) + 220Ω resistors  
- 4 Push buttons + 10kΩ resistors (pull-down)  
- Buzzer for sound feedback  

---

### ⚡ Circuit Setup – LEDs
- Connect LEDs to **pins 2, 3, 4, 5**  
- Each LED → resistor → GND  
- Use different colors for clarity  

---

### ⚡ Circuit Setup – Buttons
- Buttons to **pins 6, 7, 8, 9**  
- Each button → 10kΩ resistor → GND  
- Other side → +5V  
- Press = signal HIGH  

---

### ⚡ Circuit Setup – Buzzer
- Buzzer → Pin 10  
- Connect negative side to GND  
- Used for tones & feedback  

---

## 💻 Logic Overview
1. **Setup**: define LED + button pins  
2. **Game Loop**:  
   - Generate random sequence  
   - Play sequence with LEDs (and tones)  
   - Wait for player input  
   - Compare input vs. sequence  
   - If correct → extend sequence  
   - If wrong → reset game  

----

## 💻 Program Structure
- `setup()`  
  - Set pin modes, seed random
- `loop()`  
  1) Play current sequence  
  2) Read player input  
  3) Compare input vs. target  
  4) If correct → extend sequence; else → game over & reset

---

## 🧮 Key Functions I
- `digitalWrite(pin, HIGH/LOW)`
- → control LED  
- `digitalRead(pin)` 
- → read button  

---

## 🧮 Key Functions II
- `delay(ms)` → timing  
- `random(min, max)` → random LED index  
- `tone(pin, freq, duration)` → buzzer  

---


### 🧪 Step 1 — Test One LED
- Verify LED wiring with a simple blink

```cpp
pinMode(2, OUTPUT);
digitalWrite(2, HIGH); 
delay(300);
digitalWrite(2, LOW);  
delay(300);
```

---

### 🧪 Step 2 — Test All LEDs
- Loop through pins **2–5** for a quick chase

```cpp
int leds[] = {2,3,4,5};
for (int i=0; i<4; i++) {
  pinMode(leds[i], OUTPUT);
  digitalWrite(leds[i], HIGH); 
  delay(150);
  digitalWrite(leds[i], LOW);  
  delay(100);
}
```

---

### 🧪 Step 3 — Test Buttons
- Confirm pull-downs: idle LOW, press HIGH
- Use Serial Monitor at **9600** baud

```cpp
int btns[] = {6,7,8,9};

void setup(){
  Serial.begin(9600);
  for (int i=0; i<4; i++) pinMode(btns[i], INPUT);
}
void loop(){
  for (int i=0; i<4; i++){
    int v = digitalRead(btns[i]);
    if (v==HIGH) { 
        Serial.print("BTN " + i); 
        delay(150); 
    }
  }
}
```

---

### 🧱 Step 4 — Data Model
- LED pins: `{2,3,4,5}`
- Button pins: `{6,7,8,9}`
- Sequence: `int seq[MAX_LEN];`
- `level` holds current length
- Random step: `seq[level] = random(0,4);`

---

### ▶️ Step 5 — Show Sequence
- For i from 0 → `level-1`: 
    - `flashLed(seq[i], 350ms)`
- Short gap between cues: `delay(150)`

---

### ⌨️ Step 6 — Read Player Input
- For i from 0 → `level-1`:  
  - `pressed = waitForPress()`  
  - If `pressed != seq[i]` → fail

---

### 🧠 Step 7 — Game Logic
- Start with `level = 1`
- Correct round → `level++` (cap at MAX)
- Wrong → fail flash/sound → `level = 1`
- Optional score display via Serial

---

### ✨ Extensions （Optional）
- Increase difficulty (shorter LED on-time)
- Add tones per LED color
- Add start animation or “win” sequence
- Track high score (store in EEPROM)

* If you made it, write me an email about your sucess or questions, I would be more than happy to know!!! AI can help as well!

---

### 🧾 Full Code Sketch
> Copy–paste into Arduino IDE; Play!

```cpp
// Arduino Simon Says — Starter v1.0
// LEDs: 2,3,4,5 | Buttons: 6,7,8,9 (pull-down) | Optional buzzer: 10

const int LED_PINS[4]  = {2, 3, 4, 5};
const int BTN_PINS[4]  = {6, 7, 8, 9};
const int BUZZER_PIN   = 10;     // set to -1 to disable tones
const bool USE_TONE    = true;   // set false to silence even if buzzer wired

const int MAX_LEN      = 64;     // max sequence length
int sequenceArr[MAX_LEN];
int level = 1;                   // current visible length

// Timing (tune for difficulty)
int ledOnMs   = 350;
int gapMs     = 140;
int pressLedMs= 220;
int debounceMs= 20;
int releaseMs = 20;

void setup() {
  for (int i=0; i<4; i++) {
    pinMode(LED_PINS[i], OUTPUT);
    digitalWrite(LED_PINS[i], LOW);
    pinMode(BTN_PINS[i], INPUT); // using external 10k pull-downs
  }
  if (BUZZER_PIN >= 0) pinMode(BUZZER_PIN, OUTPUT);

  Serial.begin(9600);
  randomSeed(analogRead(A0)); // seed randomness from floating analog pin

  // Pre-fill sequence with random steps
  for (int i=0; i<MAX_LEN; i++) sequenceArr[i] = random(0,4);

  startAnimation();
}

void loop() {
  playSequence(level);
  if (readPlayer(level)) {
    // Success — extend
    successCue();
    level++;
    level = constrain(level, 1, MAX_LEN);
    // Optional difficulty ramp
    if (ledOnMs > 180) ledOnMs -= 10;
  } else {
    // Fail — reset
    failCue();
    level = 1;
    // Re-roll for freshness
    for (int i=0; i<MAX_LEN; i++) sequenceArr[i] = random(0,4);
    delay(600);
  }
  delay(400);
}

void flashLed(int idx, int onMs) {
  digitalWrite(LED_PINS[idx], HIGH);
  if (USE_TONE && BUZZER_PIN >= 0) {
    int freq = 400 + idx*200; // 400, 600, 800, 1000 Hz
    tone(BUZZER_PIN, freq, onMs);
  }
  delay(onMs);
  digitalWrite(LED_PINS[idx], LOW);
  delay(gapMs);
}

void playSequence(int len) {
  for (int i=0; i<len; i++) {
    flashLed(sequenceArr[i], ledOnMs);
  }
}

bool readPlayer(int len) {
  for (int i=0; i<len; i++) {
    int pressed = waitForPress();
    if (pressed < 0) return false;           // safety
    flashPressEcho(pressed);
    if (pressed != sequenceArr[i]) return false;
  }
  return true;
}

int waitForPress() {
  // wait until any button goes HIGH, with light debounce
  while (true) {
    for (int i=0; i<4; i++) {
      if (digitalRead(BTN_PINS[i]) == HIGH) {
        delay(debounceMs);
        // confirm still pressed
        if (digitalRead(BTN_PINS[i]) == HIGH) {
          // wait until release for next step
          while (digitalRead(BTN_PINS[i]) == HIGH) delay(releaseMs);
          return i;
        }
      }
    }
  }
  // unreachable
  // return -1;
}

void flashPressEcho(int idx) {
  digitalWrite(LED_PINS[idx], HIGH);
  if (USE_TONE && BUZZER_PIN >= 0) tone(BUZZER_PIN, 700 + idx*150, pressLedMs);
  delay(pressLedMs);
  digitalWrite(LED_PINS[idx], LOW);
  delay(gapMs);
}

void successCue() {
  // sweep LEDs forward
  for (int i=0; i<4; i++) flashLed(i, 90);
}

void failCue() {
  // all flash 3× with a low buzz
  for (int k=0; k<3; k++) {
    for (int i=0; i<4; i++) digitalWrite(LED_PINS[i], HIGH);
    if (USE_TONE && BUZZER_PIN >= 0) tone(BUZZER_PIN, 200, 180);
    delay(180);
    for (int i=0; i<4; i++) digitalWrite(LED_PINS[i], LOW);
    delay(120);
  }
}

void startAnimation() {
  // bounce
  for (int r=0; r<2; r++) {
    for (int i=0; i<4; i++) flashLed(i, 80);
    for (int i=2; i>=1; i--) flashLed(i, 80);
  }
}
```

---

### 🎥 An online tutorial with [code](https://github.com/printnplay/SimpleSimon/blob/main/simon.ino)

<iframe width="1000" height="562.5" 
  src="https://www.youtube.com/embed/fB4h0hNWz2o?si=gUdMIjFbmq6ZkRSV" 
  frameborder="0" 
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
  allowfullscreen>
</iframe>


---

#### Step-by-step Tutorial from [Spark](https://learn.sparkfun.com/tutorials/tinker-kit-circuit-guide/circuit-7-simon-says-game-)

![Spark](https://cdn.sparkfun.com/r/600-600/assets/learn_tutorials/1/9/9/2/Tinker_Kit_Circuit7-Fritzing.jpg)

---


### 📝 Submission
- Demonstration video of working game
- Brief reflection (upto 200 words)
- Submit to Learning Mall (Week 3 Workshop)
