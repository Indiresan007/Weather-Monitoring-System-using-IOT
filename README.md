Sure! Here’s a clean and professional **README.md** content you can put on GitHub for this Arduino + DHT22 + I2C LCD project. You can edit project name and add extra badges later.

---

# 🌡️ **DHT22 Temperature & Humidity Monitor with I2C LCD**

This project reads **temperature** and **humidity** values from a **DHT22 sensor** and displays them on a **16x2 I2C LCD display** using an Arduino Uno.
It is ideal for beginners exploring embedded systems, sensors, and microcontroller interfacing.

---

## 📌 **Features**

* Measure **temperature (°C)** using DHT22
* Measure **humidity (%)**
* Display data in real-time on I2C LCD
* Error handling for failed sensor readings
* Simple & low-cost hardware setup

---

## 🛠️ **Hardware Requirements**

| Component            | Quantity |
| -------------------- | -------- |
| Arduino Uno          | 1        |
| DHT22 Sensor         | 1        |
| 16x2 I2C LCD Display | 1        |
| Breadboard           | 1        |
| Jumper Wires         | –        |

---

## 🔌 **Circuit Diagram**

> DHT22 → Arduino

* **VCC → 5V**
* **GND → GND**
* **DATA → D2**

> LCD → Arduino (I2C)

* **SDA → A4**
* **SCL → A5**
* **VCC → 5V**
* **GND → GND**

---

## 📚 **Required Libraries**

Make sure the following libraries are installed:

```cpp
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <DHT.h>
```

---

## 🧾 **Source Code**

```cpp
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <DHT.h>

#define DHTPIN 2
#define DHTTYPE DHT22

DHT dht(DHTPIN, DHTTYPE);
LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0,0);
  lcd.print("Temp: ");
  lcd.setCursor(0,1);
  lcd.print("Humidity: ");
  dht.begin();
}

void loop() {
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();

  if (isnan(temperature) || isnan(humidity)) {
    lcd.setCursor(0, 0);
    lcd.print("Failed to read");
    lcd.setCursor(0, 1);
    lcd.print("from DHT sensor");
    delay(2000);
    return;
  }

  lcd.setCursor(6, 0);
  lcd.print(temperature);
  lcd.setCursor(10, 0);
  lcd.print("C");
  lcd.setCursor(10, 1);
  lcd.print("%");
  lcd.setCursor(11, 1);
  lcd.print(humidity);
  delay(2000);
}
```

---

## 🎯 **Applications**

✔ Weather monitoring
✔ Smart home systems
✔ Environmental sensing
✔ IoT projects

---


---

## 📄 **License**

This project is open-source under the **MIT License**.

---

## 🤝 **Contributing**

Pull requests are welcome! Feel free to open an issue for bug fixes or improvements.

---


