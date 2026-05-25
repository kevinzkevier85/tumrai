# ตารางเรียน ปี 2/69 — Tumrai Schedule

ตารางเรียนและกิจกรรม สำหรับนักศึกษา ปี 2 ภาคการศึกษา 2569

---

## ไฟล์ในโปรเจกต์

| ไฟล์ | คืออะไร |
|---|---|
| `schedule-2-69-v2.html` | หน้าหลัก — เปิดในเบราว์เซอร์ได้เลย |
| `schedule-2-69-dark.html` | เวอร์ชันเก่า (สำรอง) |
| `GUIDE.md` | คู่มือแก้ข้อมูล (เพิ่มกิจกรรม / แก้ตาราง) |

---

## วิธีใช้งานแบบออฟไลน์

ดับเบิลคลิก `schedule-2-69-v2.html` → เปิดในเบราว์เซอร์ได้เลย ไม่ต้องติดตั้งอะไร

---

## Deploy ขึ้น GitHub Pages (step by step)

### สิ่งที่ต้องมีก่อน
- [ ] GitHub account (สมัครฟรีที่ github.com)
- [ ] Git ติดตั้งในเครื่อง — ตรวจสอบด้วย `git --version` ใน terminal

---

### ขั้นที่ 1 — สร้าง repository ใหม่

1. เปิด github.com → login
2. กด **+** มุมบนขวา → **New repository**
3. ตั้งค่าดังนี้:
   - **Repository name:** `tumrai-schedule` (หรือชื่ออื่นก็ได้)
   - **Description:** ตารางเรียน ปี 2/69 (optional)
   - **Public** ← ต้องเลือก Public (GitHub Pages ฟรีใช้ได้เฉพาะ Public)
   - **Add a README file:** ไม่ต้องติ๊ก (เรามี README อยู่แล้ว)
   - **.gitignore / License:** ข้ามไปได้
4. กด **Create repository**

---

### ขั้นที่ 2 — upload ไฟล์เข้า repo

**วิธี A — ผ่านหน้าเว็บ (ง่ายสุด ไม่ต้องรู้ Git)**

1. ใน repo ที่เพิ่งสร้าง กด **uploading an existing file** (หรือ Add file → Upload files)
2. ลากไฟล์เหล่านี้เข้าไป:
   - `schedule-2-69-v2.html`
   - `GUIDE.md`
   - `README.md`
3. Commit message: `first upload`
4. กด **Commit changes**

**วิธี B — ผ่าน Git CLI (ถ้ารู้จัก Git)**

```bash
git init
git add schedule-2-69-v2.html GUIDE.md README.md
git commit -m "first upload"
git branch -M main
git remote add origin https://github.com/USERNAME/tumrai-schedule.git
git push -u origin main
```

---

### ขั้นที่ 3 — เปิด GitHub Pages

1. เข้าไปใน repo → แถบด้านบน กด **Settings**
2. เมนูซ้าย → **Pages**
3. ตั้งค่าดังนี้:
   - **Source:** Deploy from a branch
   - **Branch:** `main` | `/ (root)`
4. กด **Save**
5. รอ 1–3 นาที จะขึ้น URL แบบนี้:
   ```
   https://USERNAME.github.io/tumrai-schedule/schedule-2-69-v2.html
   ```

---

### ขั้นที่ 4 — ทดสอบ

เปิด URL ที่ได้ → ตรวจสอบ:
- [ ] หน้าโหลดได้
- [ ] Light/Dark toggle ทำงาน
- [ ] This Week strip แสดงข้อมูล
- [ ] สลับ tab ตารางเรียน / กิจกรรมได้

---

## อัปเดตข้อมูล (หลัง deploy แล้ว)

1. แก้ไข `schedule-2-69-v2.html` ในเครื่อง (ดู GUIDE.md สำหรับวิธีแก้)
2. upload ไฟล์ใหม่เข้า repo (วิธีเดิม — Add file → Upload files)
3. GitHub Pages อัปเดตอัตโนมัติใน 1–2 นาที

---

## การตั้งค่าที่ต้องรู้

| การตั้งค่า | ค่า | เหตุผล |
|---|---|---|
| Repository visibility | **Public** | GitHub Pages ฟรีต้องเป็น Public |
| Pages source | **main branch / root** | ไม่ได้ใช้ build system |
| File ที่เป็น homepage | ชื่อว่า `index.html` | ถ้าอยากให้ URL สั้น ไม่ต้องพิมพ์ชื่อไฟล์ |

> **Tip:** ถ้าอยากให้ URL เป็น `username.github.io/tumrai-schedule/` (ไม่ต้องพิมพ์ชื่อไฟล์)  
> ให้ rename `schedule-2-69-v2.html` → `index.html` ก่อน upload

---

## คำถามที่พบบ่อย

**Q: GitHub Pages ฟรีไหม?**  
A: ฟรี สำหรับ Public repo ไม่มีค่าใช้จ่าย bandwidth ปกติ

**Q: ข้อมูลจะหายไหมถ้า repo เป็น Public?**  
A: ใครก็เห็น source code ได้ แต่ข้อมูลใน app (localStorage) เก็บในเครื่องผู้ใช้เอง ไม่ได้อยู่ใน repo

**Q: อยากใช้ domain ของตัวเองได้ไหม?**  
A: ได้ — ตั้งค่าใน Settings → Pages → Custom domain (ต้องซื้อ domain เอง)
