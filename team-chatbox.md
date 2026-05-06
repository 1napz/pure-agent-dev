---

📂 Feature: Working Chat Box

`markdown

💬 Feature: Working Chat Box

1. Goal
- ให้ทุกการสื่อสารกับ AI ผ่าน Chat Box เดียว
- ทุกข้อความถูก Summarize → เข้า Prompting → ส่งต่อให้ Listener
- เก็บ Log ทุกข้อความอัตโนมัติ

---

2. Flow
1. Contributor ส่งข้อความ → [Request]
2. System Summarize → [Summarized]
3. PromptEngine ประมวลผล → [Prompting]
4. Listener ส่งผลลัพธ์กลับ UI → [Listener]
5. ทุกขั้นตอนถูกเก็บลง log file → [Log]

---

3. Example Chat Flow
`
[2026-05-06 23:37] [Request] Contributor: "Optimize Performance Prompt ให้ตอบเร็วขึ้น"
[2026-05-06 23:37] [Summarized] System: "Optimize performance prompt → faster response"
[2026-05-06 23:37] [Prompting] Engine: ส่งเข้า AI model เพื่อ validate
[2026-05-06 23:37] [Listener] System: ตอบกลับ "Prompt optimized, response time reduced"
[2026-05-06 23:40] [Log] System: Status check → ยัง In Progress
`

---

4. UI Layout (Wireframe)
`
-----------------------------------------
| 🖥️ PureAgent Feature Chat Box          |
-----------------------------------------
| [Header]                               |
|  Project: Feature Request #123          |
|  Status: 🟦 Assigned / 🟨 In Progress / 🟩 Completed |
-----------------------------------------
| [Chat Panel]                           |
|  👤 Contributor: "ช่วย optimize prompt ให้เร็วขึ้น"
|  🤖 Summarizer: "Optimize prompt → faster response"
|  ⚙️ PromptEngine: "AI processed request"
|  📡 Listener: "Prompt optimized, response time reduced"
-----------------------------------------
| [Log Panel]                            |
|  [23:37] Request sent                  |
|  [23:37] Summarized → faster response  |
|  [23:37] Prompting → AI processed      |
|  [23:37] Listener → Response returned  |
|  [23:40] Status check → In Progress    |
-----------------------------------------
| [Input Box]                            |
|  [ Type message here... ] [Send]       |
-----------------------------------------
`

---

✅ ผลลัพธ์
- ทุกการส่งข้อความ → Summarize ก่อนเข้า AI  
- PromptEngine ใช้ข้อความที่สรุปแล้ว → ลด noise  
- Listener ส่งผลลัพธ์กลับ UI แบบ real‑time  
- Log Panel เก็บทุกข้อความ → ตรวจสอบย้อนหลังได้  

---
