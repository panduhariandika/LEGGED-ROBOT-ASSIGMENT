# LEGGED-ROBOT-ASSIGMENT
# 🤖 3-Link Planar Robot Simulator

**Forward & Inverse Kinematics Visualization using Python**

---

## 📌 Deskripsi

Project ini merupakan simulasi robot planar dengan 3 derajat kebebasan (3-DOF) yang digunakan untuk menganalisis hubungan antara ruang joint (*joint space*) dan ruang kerja (*task space*).

Simulasi ini mencakup:

* **Forward Kinematics (FK)** → menghitung posisi end-effector dari sudut joint
* **Inverse Kinematics (IK)** → menentukan sudut joint dari posisi target

Visualisasi dilakukan secara real-time menggunakan **Matplotlib Animation**.

---

## 🎯 Fitur Utama

* Simulasi pergerakan robot 3-link planar
* Visualisasi lintasan (*trajectory*) end-effector
* Perhitungan sudut joint secara dinamis
* Tracking posisi target menggunakan Inverse Kinematics
* Perhitungan error antara target dan posisi aktual

---

## 🗂️ Struktur Project

```id="f3k92l"
.
├── main.py          # Program utama (menu)
├── forwardk.py      # Forward Kinematics
├── inversek.py      # Inverse Kinematics
└── README.md
```

---

## ▶️ Cara Menjalankan

1. Install dependensi:

```bash id="p4c8e1"
pip install numpy matplotlib
```

2. Jalankan program:

```bash id="l8s2ka"
python main.py
```

3. Pilih mode simulasi:

```id="z1x8mn"
[1] Forward Kinematics
[2] Inverse Kinematics
```

---

## ⚙️ Model Robot

Robot terdiri dari tiga link dengan panjang:

| Link | Panjang |
| ---- | ------- |
| L1   | 8       |
| L2   | 6       |
| L3   | 4       |

Robot bekerja pada bidang 2D (planar).

---

## 📐 Forward Kinematics

Forward Kinematics digunakan untuk menentukan posisi end-effector berdasarkan sudut joint.

| Komponen | Persamaan                      |
| -------- | ------------------------------ |
| x₁       | x₁ = L₁ cos(θ₁)                |
| y₁       | y₁ = L₁ sin(θ₁)                |
| x₂       | x₂ = x₁ + L₂ cos(θ₁ + θ₂)      |
| y₂       | y₂ = y₁ + L₂ sin(θ₁ + θ₂)      |
| x₃       | x₃ = x₂ + L₃ cos(θ₁ + θ₂ + θ₃) |
| y₃       | y₃ = y₂ + L₃ sin(θ₁ + θ₂ + θ₃) |

---
## 📸 Forward Kinematics Visualization
<img src="https://raw.githubusercontent.com/panduhariandika/LEGGED-ROBOT-ASSIGMENT/efcb0f63a2b8401509742f2be60ff7483300e00c/assigment%202/forwardkinematik.png" width="500">
---
Figure 1. Visualization of Forward Kinematics showing robot configuration based on joint angles.

---

## 📐 Inverse Kinematics

### (Metode: *Geometric Approach*)

Inverse Kinematics pada sistem ini diselesaikan menggunakan pendekatan geometri (*geometric approach*), yaitu dengan memanfaatkan hubungasegitiga antar link robot.


### Langkah-langkah:

1. **Menentukan posisi wrist (pergelangan)**
   End-effector dikurangi kontribusi link terakhir:

| Komponen | Persamaan           |
| -------- | ------------------- |
| x_w      | x_w = x - L₃ cos(φ) |
| y_w      | y_w = y - L₃ sin(φ) |

---

2. **Menggunakan hukum cosinus (Law of Cosines)**

| Komponen | Persamaan                                 |
| -------- | ----------------------------------------- |
| D        | D = (x_w² + y_w² - L₁² - L₂²) / (2 L₁ L₂) |
| θ₂       | θ₂ = arccos(D)                            |

---

3. **Menghitung sudut θ₁**

| Komponen | Persamaan                                             |
| -------- | ----------------------------------------------------- |
| θ₁       | θ₁ = atan2(y_w, x_w) − atan2(L₂ sinθ₂, L₁ + L₂ cosθ₂) |

---

4. **Menentukan θ₃**

| Komponen | Persamaan        |
| -------- | ---------------- |
| θ₃       | θ₃ = φ − θ₁ − θ₂ |

---

Pendekatan ini disebut *geometric approach* karena:

* Menggunakan interpretasi bentuk segitiga dari konfigurasi robot
* Tidak melibatkan diferensiasi (berbeda dengan metode Jacobian)
* Lebih intuitif dan efisien untuk sistem planar

---

## 📸 Inverse Kinematics Visualization
<img src="https://raw.githubusercontent.com/panduhariandika/LEGGED-ROBOT-ASSIGMENT/efcb0f63a2b8401509742f2be60ff7483300e00c/assigment%202/inverskinematik.png" width="500">

Figure 2. Visualization of Inverse Kinematics where robot tracks a target position.

---

## 📊 Error Tracking

Untuk mengevaluasi performa tracking, digunakan error posisi:

| Parameter | Rumus                                              |
| --------- | -------------------------------------------------- |
| Error     | √((x_target − x_actual)² + (y_target − y_actual)²) |

Error menunjukkan seberapa dekat end-effector mengikuti trajectory yang diinginkan.

---

## 🧠 Kesimpulan

Simulasi ini menunjukkan hubungan langsung antara:

* Sudut joint → posisi end-effector (Forward Kinematics)
* Posisi target → sudut joint (Inverse Kinematics)

Pendekatan *geometric* pada Inverse Kinematics memberikan solusi yang cepat dan stabil untuk robot planar 3-link, serta cocok digunakan sebagai dasar dalam pengembangan sistem robotika yang lebih kompleks.

---

## 📄 License

Digunakan untuk keperluan pembelajaran dan penelitian.
 jadi saya ada menambhakan foto 

ini link 
https://github.com/panduhariandika/LEGGED-ROBOT-ASSIGMENT/blob/efcb0f63a2b8401509742f2be60ff7483300e00c/assigment%202/forwardkinematik.png
foto forward
https://github.com/panduhariandika/LEGGED-ROBOT-ASSIGMENT/blob/efcb0f63a2b8401509742f2be60ff7483300e00c/assigment%202/inverskinematik.png
