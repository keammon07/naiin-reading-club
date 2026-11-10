# Naiin Reading Club — Website Prototype

เว็บทดลอง Reading Challenge ภาษาไทย รองรับมือถือและคอมพิวเตอร์ สร้างด้วย HTML/CSS/JavaScript ล้วน ไม่ต้องใช้ Node.js หรือฐานข้อมูล

## ทดลองบนคอมพิวเตอร์
เปิดไฟล์ `index.html` ในเบราว์เซอร์ หรือรันเว็บเซิร์ฟเวอร์ในโฟลเดอร์นี้:

```bash
python -m http.server 8000
```

แล้วเปิด http://localhost:8000

## อัปโหลดขึ้น GitHub Pages
1. สร้าง Repository ใหม่บน GitHub (เช่น `naiin-reading-club`)
2. อัปโหลดไฟล์ทั้งหมด **รวมโฟลเดอร์ `.github/workflows/deploy.yml`** ไปยัง branch `main` โดยรักษาโครงสร้างเดิม
3. ไปที่ **Settings → Pages → Build and deployment → Source** แล้วเลือก **GitHub Actions**
4. ไปที่ **Actions** รอ Workflow `Deploy Naiin Reading Club to GitHub Pages` ทำงานเสร็จ หรือกด **Run workflow**
5. เปิด URL ที่แสดงในหน้า Deploy (โดยทั่วไปเป็น `https://USERNAME.github.io/REPOSITORY/`)

> หมายเหตุ: GitHub Pages สำหรับ repository สาธารณะจะเผยแพร่เว็บสู่สาธารณะ หากต้องการทดลองแบบไม่เผยแพร่ ให้เปิด `index.html` บนเครื่องหรือใช้เซิร์ฟเวอร์ภายในแทน

## ฟีเจอร์ที่ลองได้
- หน้า Landing Page / วิธีเข้าร่วม
- สมัครด้วยชื่อเล่นและเลือกหมวดหนังสือแบบทดลอง
- เช็กอินวันละ 1 ครั้งตามวันที่ในเครื่อง
- ปฏิทิน 21 วัน / Progress 15 วัน / Badge เมื่อครบเป้าหมาย
- เลือกหมวดหนังสือ / แชร์ความสำเร็จ / รีเซ็ตข้อมูล
- Responsive สำหรับมือถือและเดสก์ท็อป

## ข้อจำกัดสำคัญ
- **นี่คือ UI Prototype ไม่ใช่ระบบ Naiin จริง** ไม่มีระบบ Login/Member ID, Backend, Database, Email, LINE OA หรือ GA4 ที่เชื่อมใช้งานจริง
- ข้อมูลเก็บใน `localStorage` ของเบราว์เซอร์เดียวกันเท่านั้น ผู้ใช้คนละเครื่องไม่เห็นข้อมูลร่วมกัน และล้างข้อมูลเบราว์เซอร์แล้วข้อมูลจะหาย
- เวลา Check-in อ้างอิงวันที่ของอุปกรณ์ จึงไม่ป้องกันการแก้เวลา/การโกง
- ไม่ควรใช้เก็บข้อมูลลูกค้าจริงหรือแจกของรางวัลจริงจนกว่าจะมี Backend, Authentication, Consent/PDPA, Security, Rate Limit, Anti-fraud และ Analytics
- หนังสือ/ภาพปกในเว็บเป็นตัวอย่างสมมติ ไม่ใช่สินค้าจริง

## แนวทางพัฒนาต่อกับ IT
1. เชื่อม Member Login ของ Naiin ผ่าน API ที่ปลอดภัย
2. สร้างฐานข้อมูล Check-in โดยใช้ Customer ID ภายใน และตรวจสอบวันฝั่ง Server
3. เพิ่ม Event Tracking เช่น `reading_challenge_register`, `reading_challenge_checkin`, `reading_challenge_complete` โดยไม่ส่ง Email/PII ไป GA4
4. ทำหน้า Admin/Export KPI, แยก Consent, จัดเก็บข้อมูลตามระยะเวลาที่กำหนด
5. เพิ่ม Book Recommendations จาก Catalog จริง และ A/B Test / Control Group

## โครงสร้าง
- `index.html` — หน้าเว็บ
- `styles.css` — ดีไซน์และ Responsive
- `app.js` — การทำงานแบบ Demo
- `.github/workflows/deploy.yml` — GitHub Actions สำหรับ Deploy
