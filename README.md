# DeepFace Real-Time Facial Analysis Project

โปรเจ็กต์วิเคราะห์ใบหน้าแบบเรียลไทม์ที่ใช้ DeepFace สำหรับตรวจจับอายุ เพศ และอารมณ์ พร้อมฟีเจอร์ขั้นสูงในการวิเคราะห์จุดสำคัญบนใบหน้า

## 🌟 Features (ฟีเจอร์หลัก)

### ✨ การวิเคราะห์แบบเรียลไทม์
- **Age Detection** - ตรวจจับอายุจากใบหน้า
- **Gender Recognition** - จำแนกเพศ (ชาย/หญิง)
- **Emotion Analysis** - วิเคราะห์อารมณ์ (ดีใจ เศร้า โกรธ ตกใจ เกลียด กลัว เฉยๆ)
- **Face Landmarks** - แสดงจุดสำคัญบนใบหน้า (ดวงตา จมูก ปาก คิ้ว)

### 🚀 ประสิทธิภาพสูง
- **GPU Acceleration** - รองรับการเร่งความเร็วด้วย GPU (CUDA)
- **Real-time Processing** - ประมวลผลเรียลไทม์ด้วยการข้ามเฟรม
- **Multi-backend Support** - รองรับ OpenCV และ MediaPipe

### 📊 การแสดงผลข้อมูล
- **Live Data Table** - ตารางข้อมูลสดพร้อมประวัติการวิเคราะห์
- **Progress Monitoring** - แสดงความคืบหน้าการประมวลผล
- **Interactive Controls** - ควบคุมการเล่น หยุดชั่วคราว และออกจากโปรแกรม

## 🛠️ Installation (การติดตั้ง)

### ความต้องการของระบบ
- Python 3.8+
- pip package manager
- Webcam (สำหรับการวิเคราะห์แบบสด)
- CUDA-compatible GPU (ไม่บังคับ แต่แนะนำสำหรับประสิทธิภาพที่ดีขึ้น)

### ขั้นตอนการติดตั้ง

1. **Clone repository**
```bash
git clone https://github.com/ThammanoonAKE/my-python-DeepFace-predict_Age-gender-feelings-project.git
cd my-python-DeepFace-predict_Age-gender-feelings-project
```

2. **ติดตั้ง dependencies**
```bash
pip install -r requirements.txt
```

3. **เปิด Jupyter Notebook**
```bash
jupyter notebook DeepFace.ipynb
```

## 🎮 Usage (การใช้งาน)

### โหมดการวิเคราะห์

#### 1. 📹 Real-time Camera Analysis
- เปิด cell แรกใน notebook
- โปรแกรมจะเปิดกล้องและแสดงผลการวิเคราะห์แบบสด
- กด 'q' เพื่อออกจากโปรแกรม

#### 2. 🎬 Video File Analysis
- วางไฟล์วิดีโอในโฟลเดอร์โปรเจ็กต์ (เช่น `girl.mp4`)
- เปิด cell ที่ 2 สำหรับการวิเคราะห์พื้นฐาน
- ดูผลการวิเคราะห์พร้อมตารางข้อมูล

#### 3. 🔬 Advanced Analysis with Face Landmarks
- เปิด cell ที่ 3 สำหรับฟีเจอร์ขั้นสูง
- รองรับการแสดงจุดสำคัญบนใบหน้า
- มีการแสดงสถานะ GPU และการควบคุมขั้นสูง

### ⌨️ Keyboard Controls
- **'q' หรือ ESC** - ออกจากโปรแกรม
- **Space** - หยุดชั่วคราว (Advanced mode)
- **'c'** - ดำเนินการต่อหลังจากหยุดชั่วคราว

## 📋 Dependencies (ไลบรารีที่ใช้)

| Package | Version | Purpose |
|---------|---------|---------|
| opencv-python | 4.11.0.86 | Computer vision และการประมวลผลวิดีโอ |
| deepface | 0.0.93 | AI facial analysis (อายุ เพศ อารมณ์) |
| mediapipe | 0.10.21 | Face landmarks detection |
| tensorflow[and-cuda] | 2.16.1 | Machine learning backend |
| numpy | >=1.26 | Numerical computations |

## ⚙️ Technical Details (รายละเอียดทางเทคนิค)

### Architecture
- **Frontend**: Jupyter Notebook interface
- **Backend**: DeepFace + MediaPipe + OpenCV
- **AI Models**: Pre-trained models สำหรับ age, gender, emotion detection
- **Face Detection**: OpenCV Haar Cascades และ MediaPipe Face Mesh

### Performance Optimization
- **Frame Skipping**: ประมวลผลทุก 5 เฟรมเพื่อประสิทธิภาพที่ดีขึ้น
- **GPU Memory Management**: การจัดการหน่วยความจำ GPU แบบ dynamic
- **Error Handling**: `enforce_detection=False` เพื่อป้องกันการ crash

### Data Visualization
- Real-time data table แสดงประวัติการวิเคราะห์ 10 รายการล่าสุด
- Color-coded display สำหรับข้อมูลปัจจุบันและประวัติ
- Progress indicators และ frame counters

## 🎯 Example Output

การวิเคราะห์จะแสดงผลลัพธ์ดังนี้:
- **Age**: ประมาณการอายุ (เช่น 25, 30, 45)
- **Gender**: เพศ (Man/Woman)
- **Emotion**: อารมณ์หลัก (happy, sad, angry, surprised, disgust, fear, neutral)
- **Confidence**: ระดับความมั่นใจของการวิเคราะห์

## 🔧 Configuration

### GPU Settings
โปรแกรมจะตรวจจับ GPU อัตโนมัติ:
```python
physical_devices = tf.config.experimental.list_physical_devices('GPU')
if len(physical_devices) > 0:
    tf.config.experimental.set_memory_growth(physical_devices[0], True)
```

### Detector Backend Options
- `opencv` (default) - เสถียรและรวดเร็ว
- `mediapipe` - ความแม่นยำสูงกว่า

## 🐛 Troubleshooting

### ปัญหาที่พบบ่อย
1. **GPU ไม่ทำงาน**: ตรวจสอบการติดตั้ง CUDA และ cuDNN
2. **กล้องไม่เปิด**: ตรวจสอบ permissions และ camera drivers
3. **ไฟล์วิดีโอไม่เล่น**: ตรวจสอบ codec และ file path

### การแก้ไข
- ตรวจสอบ error messages ใน console
- ลองเปลี่ยน detector backend
- อัพเดต drivers และ dependencies

## 📝 License

MIT License - ดูรายละเอียดใน LICENSE file

## 🤝 Contributing

ยินดีรับ contributions! กรุณา:
1. Fork repository
2. สร้าง feature branch
3. Commit changes
4. สร้าง Pull Request

## 📞 Support

หากมีปัญหาหรือคำถาม กรุณาสร้าง issue ใน GitHub repository


