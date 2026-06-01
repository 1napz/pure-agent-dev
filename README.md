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


นี่คือร่างของไฟล์ README.md สำหรับโปรเจกต์ **Python Playwright Google Search Scraper** ของคุณ โดยรวมเนื้อหาตั้งแต่การติดตั้ง การรันสคริปต์ ไปจนถึงการตั้งค่า Automation ครับ
# Python Playwright Google Search Scraper
ระบบดึงข้อมูลสินค้าขายดีจาก Google Search (Shopee, Lazada, TikTok Shop) โดยใช้ Python และ Playwright เพื่อนำไปวิเคราะห์ข้อมูลหรือติดตามเทรนด์สินค้า
## 📋 คุณสมบัติ (Features)
 * **Search Scraping:** รองรับการค้นหาแบบระบุเจาะจงเว็บไซต์ (Site Specific) เช่น site:shopee.co.th
 * **Data Export:** บันทึกข้อมูลออกมาในรูปแบบไฟล์ CSV พร้อมใช้งาน
 * **Automation Ready:** รองรับการรันแบบ Headless เพื่อทำงานเบื้องหลัง
 * **Notification:** ระบบส่งรายงานผ่าน Email อัตโนมัติเมื่อ Scraper ทำงานเสร็จสิ้น
## 🚀 การติดตั้ง (Installation)
 1. **ติดตั้ง Python** (แนะนำเวอร์ชัน 3.10 ขึ้นไป)
 2. **ติดตั้ง Library ที่จำเป็น:**
   ```bash
   pip install playwright
   playwright install
   
   ```
## 🛠 การใช้งาน (Usage)
### 1. การตั้งค่าสคริปต์
แก้ไขไฟล์ Google Search.py เพื่อระบุคำค้นหา (Queries) ที่คุณต้องการ:
```python
queries = [
    "site:shopee.co.th สินค้าขายดี 2026",
    "site:lazada.co.th สินค้าขายดี"
]

```
### 2. การรันโปรแกรม
รันคำสั่งผ่าน Terminal:
```bash
python google_search.py

```
ข้อมูลจะถูกบันทึกลงในไฟล์ google_bestsellers.csv ในโฟลเดอร์เดียวกับสคริปต์
## 🤖 ระบบอัตโนมัติ (Automation & Scheduling)
หากต้องการให้ระบบทำงานเองโดยไม่ต้องกดรัน:
### Windows (Task Scheduler)
 1. เปิด **Task Scheduler** > **Create Basic Task**
 2. ตั้ง Trigger เป็น **Daily** (ทุกวัน)
 3. Action เลือก **Start a program**
 4. โปรแกรม: path\to\your\python.exe
 5. อาร์กิวเมนต์: path\to\your\google_search.py
### Linux/macOS (Cron Job)
ใช้คำสั่ง crontab -e และเพิ่มบรรทัดนี้ (รันทุกวันเวลา 08:00):
```bash
0 8 * * * /usr/bin/python3 /path/to/your/google_search.py

```
## 💡 ข้อแนะนำเพิ่มเติม
 * **CAPTCHA Handling:** หากโดน Google บล็อกบ่อยครั้ง แนะนำให้เพิ่มการตั้งค่า user_agent ใน browser.new_context() หรือใช้บริการ Proxy
 * **Security:** หากเปิดใช้งานระบบส่งอีเมล อย่าลืมตั้งค่า App Password สำหรับ Gmail เพื่อความปลอดภัย
 * **Logging:** แนะนำให้ใช้ไลบรารี loguru เพื่อบันทึกประวัติการทำงาน (Log) ลงไฟล์แยกตามวันที่ เพื่อความสะดวกในการตรวจสอบข้อผิดพลาด
## 🛠 เครื่องมือเสริมแนะนำ
 * **BeautifulSoup4:** สำหรับกรณีต้องการดึงข้อมูลเชิงลึกจาก DOM ของหน้าเว็บที่ซับซ้อน
 * **SQLite:** หากข้อมูลมีจำนวนมาก แนะนำให้ย้ายจากการเก็บเป็น CSV มาเป็น SQLite Database เพื่อป้องกันปัญหาข้อมูลซ้ำ (Duplicate)
คุณสามารถคัดลอกเนื้อหานี้ไปสร้างเป็นไฟล์ README.md ไว้ในโฟลเดอร์โปรเจกต์ของคุณได้เลยครับ
