# Implementasi Mikrokontroler dengan Sensor DHT22

## 📌 Deskripsi Proyek
Proyek ini merupakan implementasi sistem monitoring suhu dan kelembapan berbasis **ESP32** dan **sensor DHT22**. Sistem dirancang untuk membaca data suhu serta kelembapan lingkungan secara real-time dan menampilkannya melalui **Serial Monitor** pada Arduino IDE.

Sensor DHT22 digunakan karena memiliki akurasi yang baik dan mudah diintegrasikan dengan mikrokontroler ESP32, sehingga cocok digunakan pada aplikasi monitoring lingkungan berbasis IoT.

---

## 🖼️ Dokumentasi Sistem

<img width="270" height="200" alt="image" src="https://github.com/user-attachments/assets/fd2edbd1-6fc8-4799-9e7b-347f0b809dd5" />

---

## 🛠️ Alat dan Komponen
- ESP32 DOIT DEVKIT V1  
- Sensor DHT22  
- Breadboard  
- Kabel Jumper  
- Kabel USB Data  

---

## 🔌 Konfigurasi Pin

| Pin DHT22 | ESP32 |
|------------|--------|
| VCC        | 3.3V |
| GND        | GND |
| DATA       | GPIO15 |

---

## ⚙️ Langkah Implementasi

### Perakitan Hardware
1. Hubungkan pin VCC DHT22 ke 3.3V ESP32.  
2. Hubungkan pin GND DHT22 ke GND ESP32.  
3. Hubungkan pin DATA DHT22 ke GPIO15 ESP32.  
4. Pastikan seluruh koneksi terpasang dengan benar.  

### Pemrograman
1. Buka **Arduino IDE** dan buat file program baru.  
2. Install library:
   - `DHT sensor library`
   - `Adafruit Unified Sensor`

3. Tambahkan library `DHT.h` pada program.  
4. Pilih board:
   `Tools → Board → DOIT ESP32 DEVKIT V1`

5. Pilih port ESP32 yang sesuai.  
6. Upload program hingga muncul status **Done Uploading**.

---

## 💻 Program Arduino

```cpp
#include "DHT.h"

#define DHTPIN 15
#define DHTTYPE DHT22

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(115200);
  
  dht.begin();

  Serial.println("Monitoring Suhu dan Kelembapan DHT22");
}

void loop() {

  // Membaca kelembapan
  float humidity = dht.readHumidity();

  // Membaca suhu Celsius
  float temperature = dht.readTemperature();

  // Mengecek apakah pembacaan gagal
  if (isnan(humidity) || isnan(temperature)) {
    Serial.println("Gagal membaca sensor DHT22!");
    return;
  }

  // Menampilkan data
  Serial.print("Suhu: ");
  Serial.print(temperature);
  Serial.println(" °C");

  Serial.print("Kelembapan: ");
  Serial.print(humidity);
  Serial.println(" %");

  Serial.println("----------------------");

  delay(2000);
}
```

---

## 🔍 Cara Kerja Sistem
- Sensor DHT22 membaca nilai suhu dan kelembapan lingkungan.  
- ESP32 memproses data sensor menggunakan library `DHT.h`.  
- Data hasil pembacaan ditampilkan secara real-time melalui Serial Monitor Arduino IDE setiap 2 detik.  
- Sistem akan terus melakukan monitoring selama ESP32 aktif.

---

## 📊 Hasil Pengujian
Integrasi ESP32 dan sensor DHT22 berhasil diimplementasikan untuk monitoring suhu dan kelembapan secara real-time. Sistem mampu membaca dan menampilkan data dengan stabil melalui Serial Monitor tanpa error pembacaan. Proyek ini memberikan pemahaman dasar mengenai penggunaan sensor, pengolahan data, dan implementasi sistem monitoring berbasis IoT.

---

## 💻 Teknologi yang Digunakan
- Arduino IDE  
- ESP32  
- Sensor DHT22  
- Serial Communication  
- Embedded System Programming  

---

## 📚 Tujuan Pembelajaran
- Memahami penggunaan sensor DHT22 pada ESP32  
- Membaca data suhu dan kelembapan secara real-time  
- Menampilkan data sensor melalui Serial Monitor  
- Mengimplementasikan sistem monitoring sederhana berbasis IoT  

---

## 👨‍💻 Author
**Puspita**  
Computer Engineering Student — IPB University
