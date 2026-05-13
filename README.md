# pure-agent-dev 🤖

ระบบ Monitor ลิงก์สินค้าแฟชั่นอัตโนมัติ พร้อมแจ้งเตือนผ่าน LINE เมื่อลิงก์มีปัญหา

---

## ✨ Features

- 🔍 เช็กสถานะลิงก์สินค้าทุกรายการอัตโนมัติ
- 📨 แจ้งเตือนผ่าน LINE เฉพาะเมื่อสถานะเปลี่ยนแปลง (ไม่ spam)
- 🔁 Retry อัตโนมัติเมื่อเน็ตกระตุก (สูงสุด 3 ครั้ง)
- 📝 บันทึก Log ทุกครั้งที่รัน
- ⚙️ รันอัตโนมัติผ่าน GitHub Actions (ฟรี ไม่ต้องมีเซิร์ฟเวอร์)

---

## 📁 โครงสร้างไฟล์

```
pure-agent-dev/
│
├── link-monitor/
│   ├── monitor.py          # สคริปต์หลัก
│   ├── links.csv           # รายชื่อลิงก์สินค้า
│   └── requirements.txt    # Python dependencies
│
└── .github/
    └── workflows/
        └── monitor.yml     # GitHub Actions workflow
```

---

## 🚀 วิธีติดตั้ง

### 1. Clone repo

```bash
git clone https://github.com/1napz/pure-agent-dev.git
cd pure-agent-dev
```

### 2. ติดตั้ง dependencies (สำหรับรัน local)

```bash
pip install -r link-monitor/requirements.txt
```

### 3. สร้างไฟล์ `.env` (สำหรับรัน local เท่านั้น)

```env
MY_LINE_KEY=your_channel_access_token
MY_LINE_USER_ID=your_line_user_id
```

> ⚠️ ห้าม push ไฟล์ `.env` ขึ้น GitHub เด็ดขาด

### 4. เพิ่มลิงก์สินค้าใน `links.csv`

```csv
name,url
ชื่อสินค้า 1,https://example.com/product/1
ชื่อสินค้า 2,https://example.com/product/2
```

---

## ⚙️ ตั้งค่า GitHub Actions

### เพิ่ม Secrets

ไปที่ `Settings → Secrets and variables → Actions` แล้วเพิ่ม:

| Secret Name | ค่าที่ต้องใส่ |
|---|---|
| `MY_LINE_KEY` | Channel Access Token จาก LINE Developers |
| `MY_LINE_USER_ID` | User ID ของคุณ |

### ปรับเวลารัน

แก้ใน `.github/workflows/monitor.yml`:

```yaml
- cron: '0 */2 * * *'    # ทุก 2 ชั่วโมง
- cron: '*/30 * * * *'   # ทุก 30 นาที
- cron: '0 9 * * *'      # ทุกวัน 9 โมงเช้า
```

### ทดสอบรันมือ

ไปที่ `Actions → Link Monitor → Run workflow`

---

## 📨 ตัวอย่างข้อความแจ้งเตือน LINE

| สถานการณ์ | ข้อความ |
|---|---|
| ลิงก์พึ่งหยุดทำงาน | 🚫 ชื่อสินค้า — ลิงก์เพิ่งหยุดทำงาน! |
| ลิงก์กลับมาแล้ว | ✅ ชื่อสินค้า — ลิงก์กลับมาใช้งานได้แล้ว! 🎉 |

---

## 🛠️ Tech Stack

- Python 3.11
- [Requests](https://docs.python-requests.org/) — HTTP client
- [python-dotenv](https://pypi.org/project/python-dotenv/) — จัดการ environment variables
- LINE Messaging API — ส่งการแจ้งเตือน
- GitHub Actions — รันอัตโนมัติ

---

## 📄 License

Private repository — All rights reserved © 1napz
