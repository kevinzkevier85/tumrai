# คู่มือแก้ข้อมูล — TumraiSchedule v2

ไฟล์หลักคือ `schedule-2-69-v2.html` — เปิดด้วย text editor แล้วหา comment block ที่มีเส้น `──` ล้อมรอบ

---

## 1. เพิ่มกิจกรรมใหม่

หา comment นี้ในไฟล์:
```
// ── ADD ACTIVITIES HERE ──────────────────────────────────────────────────
```

เพิ่ม object ใหม่ใน `ACTIVITIES` array โดย copy template ด้านล่าง แล้ววางก่อน `];` ปิด array:

```js
{
  id: "a2",                    // เปลี่ยนเลขทุกครั้งที่เพิ่ม (a2, a3, a4...)
  title: "ชื่อกิจกรรม",
  date: "2026-07-15",          // วันเริ่ม — format YYYY-MM-DD เสมอ
  endDate: "2026-07-15",       // วันสิ้นสุด — ถ้า 1 วัน ใส่วันเดียวกัน
  location: "สถานที่",          // ใส่ "" ถ้าไม่มี
  link: "",                    // URL หรือ "" ถ้าไม่มี
  category: "วิชาการ",          // "วิชาการ" | "กีฬา" | "สังคม" | "สโมสร"
  visibleTo: "public"          // อย่าเปลี่ยน
},
```

**Date format rules:**
- เก็บในโค้ด: `"YYYY-MM-DD"` เช่น `"2026-07-15"`
- แสดงบนหน้าจอ: `DD-MM-YYYY` เช่น `15-07-2026` (แปลงอัตโนมัติ)

**Status badge คำนวณจากวันที่อัตโนมัติ:**
- ก่อนถึง date → UPCOMING
- date ถึง endDate → ACTIVE
- หลัง endDate → DONE

---

## 2. แก้ตารางเรียน (schedule)

แต่ละ block card ใน HTML มีรูปแบบ:
```html
<div class="block-card" data-color="green" data-id="b1"
     data-start="2026-05-25" data-end="2026-06-05">
  <h3>ชื่อวิชา</h3>
  <div class="sub">รายละเอียด</div>
  ...
</div>
```

**แก้ได้:**
- `data-start` / `data-end` — วันเริ่ม/สิ้นสุด (YYYY-MM-DD)
- `data-color` — สีเส้นและจุด: `green | yellow | orange | red | blue | purple | pink | teal`
- `<h3>` — ชื่อวิชา
- `.sub` — รายละเอียดย่อ (หน่วยกิต, สัปดาห์)

---

## 3. แก้ Topics ในแต่ละ block

หา comment นี้:
```
// ── EDIT TOPICS HERE ─────────────────────────────────────────────────────
```

แต่ละ block มีรูปแบบ:
```js
b1: { name:"ชื่อ block", pdf:"", topics:[
  {id:"b1-t1", name:"ชื่อ topic", priority:"high"},
  ...
]},
```

**priority:**
- `"high"` → จุดแดง (HIGH-YIELD)
- `"exam"` → จุดเหลือง (EXAM)
- `"concept"` → จุดเทา (CONCEPT)

**เพิ่ม topic ใหม่:** copy บรรทัด `{id:...}` แล้ววางต่อท้าย array  
**ลบ topic:** ลบบรรทัดนั้นออก  
**`id` ต้องไม่ซ้ำ** — ใช้รูปแบบ `b1-t7`, `b1-t8` ต่อเลขไปเรื่อยๆ

---

## 4. เพิ่ม PDF link ให้ block

ใน TOPICS object หา block ที่ต้องการแล้วเปลี่ยน `pdf:""` เป็น URL:

```js
b1: { name:"...", pdf:"https://drive.google.com/...", topics:[...] },
```

ปุ่ม "PDF ↗" จะปรากฏใน panel เมื่อเปิด block นั้น

---

## 5. Theme

- คลิก 🌙 / ☀ มุมบนขวา
- ค่าที่เลือกบันทึกอัตโนมัติ — จำไว้เมื่อ reload
