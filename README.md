# 🎓 Deep Learning auf Edge-Geräten: Echtzeit-Objekterkennung von Elektronikbauteilen

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![YOLO](https://img.shields.io/badge/YOLO-v8%20%7C%20v11-green.svg)](https://ultralytics.com/)
[![Raspberry Pi](https://img.shields.io/badge/Hardware-Raspberry%20Pi%205-c51a4a.svg)](https://www.raspberrypi.com/)
[![Hailo](https://img.shields.io/badge/NPU-Hailo--8L-orange.svg)](https://hailo.ai/)

Dieses Repository enthält die Skripte, Auswertungen und Dokumentationen zum Projekt: 
**"Deep Learning auf Edge-Geräten: Vergleichende Evaluation moderner YOLO-Architekturen zur Echtzeit-Objekterkennung"**.

## 📌 Über das Projekt
Das Ziel dieser Arbeit ist die Konzeption und Evaluation eines robusten, echtzeitfähigen Edge-AI-Systems zur Erkennung von elektronischen Teilen** (kleinteilige Elektronik-Sets). 

Dabei wurde eine vergleichende Analyse zwischen zwei heterogenen Edge-Hardware-Architekturen durchgeführt, um den optimalen Kompromiss aus Erkennungsgenauigkeit (mAP), Inferenzgeschwindigkeit (FPS) und Systemeffizienz (CPU/RAM-Auslastung) zu finden.

### ⚙️ Evaluierte Hardware-Architekturen
1. **System A (Integriert):** Raspberry Pi 5 + **Raspberry Pi AI Camera** (Sony IMX500 Sensor mit On-Sensor Processing).
2. **System B (Modular):** Raspberry Pi 5 + **Raspberry Pi AI HAT** (Hailo-8L NPU über PCIe angebunden, 13 TOPS).

### 🧠 Evaluierte Modelle
Trainiert und quantisiert wurden moderne Objekt-Detektoren der Nano-Klasse für Ressourcen-limitierte Geräte:
* **YOLOv8n**
* **YOLOv11n** (inkl. neuer Architektur-Module wie C3k2 und C2PSA)

---

## 🚀 Kern-Ergebnisse (Highlights)

* **Echtzeitfähigkeit:** Beide Systeme (AI Camera & AI HAT) erreichen stabile **30 FPS** bei der Objekterkennung.
* **Systemeffizienz (CPU-Overhead):** Die AI Camera arbeitet deutlich effizienter (**~16% CPU-Last**) als der AI HAT (**~28% CPU-Last**). Ursache ist der Datenübertragungs-Overhead (Memory Copying) über den PCIe-Bus zur Hailo-NPU im Gegensatz zur direkten Bildverarbeitung auf dem Sony-Sensor.

---

## 🛠️ Verwendeter Tech-Stack

* **Sprachen & Frameworks:** Python, PyTorch, Ultralytics (YOLO)
* **Computer Vision:** OpenCV
* **Edge ML Tools:** Hailo Dataflow Compiler (DFC), Sony IMX500 Toolchain
* **Datenverarbeitung:** Roboflow (Aggregation, Augmentation, Resize auf 640x640)

---

## 📂 Repository-Struktur

```text                  
├── src/                   # Source Code für die Inferenz auf dem Raspberry Pi
│   ├── ai_detect_code.py  # Inferenz-Skript für den Sony IMX500
│   └── hailo_detect_code_monitoring.py     # Inferenz-Skript für den AI HAT (Hailo-8L)
|   |__ aicam_detect_original_code
|   |__ hailo_detect_original_code
|   |__ yolo_convert
├── 
└── README.md
