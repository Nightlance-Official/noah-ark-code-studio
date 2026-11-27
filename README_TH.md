<p align="center">
  <a href="README.md">English</a> | <b>ภาษาไทย</b>
</p>

# Noah Ark Code Studio

**โปรแกรม IDE ช่วยเขียน รีวิว และแก้โค้ดด้วย AI บน Windows — เน้นความปลอดภัยด้วย Diff-First, ย้อนกลับ Checkpoint ใน 1 คลิก, ตัวเบรกกันผลาญ API Key, รองรับทั้ง Local & Cloud AI และซื้อขาดออฟไลน์ (ไม่จ่ายรายเดือน)**

- **ดาวน์โหลดเวอร์ชันล่าสุด (Windows 64-bit):** [ดาวน์โหลด `NoahArkCodeStudio_Setup_v1.0.0.exe`](https://github.com/Nightlance-Official/noah-ark-code-studio/releases/latest)
- **ติดต่อสั่งซื้อคีย์ / เพจทางการ:** [Nightlance Official (Facebook)](https://www.facebook.com/NightlanceOfficial)
- **โปรแกรมแชทหลักคู่หู (ฟรี):** [Noah Ark AI Chat](https://github.com/Nightlance-Official/noah-ark-ai-chat)

---

## ภาพตัวอย่างหน้าจอ

### ตรวจ Diff ทีละท่อนก่อนแก้ไฟล์จริง (โหมด `Edit`)
<img width="2880" height="1704" alt="Noah Ark Code Studio en test1" src="https://github.com/user-attachments/assets/3b1fcb13-063b-4c41-9762-d7ac2eed38fb" />

### โหมด `Auto (ปลอดภัย)` + รันตรวจสอบอัตโนมัติ & ประวัติ Checkpoint
<img width="2880" height="1704" alt="Noah Ark Code Studio en test2" src="https://github.com/user-attachments/assets/941ec58b-5912-4d6f-b7f3-2aae7867a8cd" />

### หน้าจอภาษาไทยเต็มรูปแบบ + ดู Diff ย้อนหลังใน Checkpoint
<img width="2880" height="1704" alt="Noah Ark Code Studio test2" src="https://github.com/user-attachments/assets/eecec30d-cc87-408e-8ef7-fa997eff6d7e" />

### เขียนโค้ดออฟไลน์ 100% ด้วย Local Ollama
<img width="2880" height="1704" alt="Noah Ark Code Studio image" src="https://github.com/user-attachments/assets/5c0b4751-0462-4c8e-aeff-d7361c21a623" />

---

## จุดเด่นของ Noah Ark Code Studio

- **ซื้อขาดออฟไลน์ ไม่มีรายเดือน:** ตรวจสิทธิ์ด้วยลายเซ็นดิจิทัล `Ed25519` ในเครื่อง 100% ไม่ต้องล็อกอินบัญชี ไม่ต้องต่อเน็ตเช็กเซิร์ฟเวอร์ และอัปเดตเวอร์ชันใหม่ทับได้โดยไม่เสียคีย์เดิม
- **เลือกใช้ AI ได้อิสระ (Local AI + BYOK):** รันโมเดลฟรีในเครื่องด้วย **Ollama** หรือ **LM Studio** หรือเสียบ API Key ของคุณเองโดยตรง (**Google Gemini, OpenRouter, NVIDIA NIM, Groq, DeepSeek, OpenAI, Mistral AI** และเซิร์ฟเวอร์ Custom อื่นๆ)
- **ออกแบบมาเพื่อคุมความปลอดภัยและคุมงบโดยเฉพาะ:** มีทั้งหน้าต่าง **Diff-First**, สำรอง **Checkpoint อัตโนมัติ**, บล็อกไฟล์ความลับ (`.env`, `.key`, `.pem`), Workspace Jail, และระบบ **Anti-Burn** กัน AI วนลูปผลาญโควตา API

---

## ความสามารถหลักทั้งหมด

### 1. โหมดผู้ช่วยเขียนโค้ด AI 3 ระดับ
- **โหมด `Plan` (ค่าเริ่มต้น):** อ่านและวิเคราะห์โปรเจกต์ อธิบายโค้ด และวางแผนโครงสร้างโดยไม่แตะต้องไฟล์จริง
- **โหมด `Edit` (Diff-First):** AI อ่านโปรเจกต์และส่งข้อเสนอแก้โค้ดเข้าแท็บ **ตรวจ Diff** ให้คุณตรวจและติ๊กเลือกใช้/ปฏิเสธทีละ Hunk ก่อนเขียนลงไฟล์จริง
- **โหมด `Auto (ปลอดภัย)`:** รองรับการทำงานต่อเนื่องแบบ `แก้โค้ด -> รันเทสต์ -> แก้ซ้ำ` พร้อมเกราะป้องกัน 4 ชั้น:
  - สำรอง **Checkpoint อัตโนมัติ** ทุกครั้งก่อนเขียนทับไฟล์
  - **Dirty-Tab Guard:** ห้ามเขียนทับไฟล์ที่คุณกำลังพิมพ์ค้างไว้ในแท็บ (ส่งเข้าหน้าตรวจ Diff แทนอัตโนมัติ)
  - **Allowlist คำสั่งปลอดภัย:** รันอัตโนมัติเฉพาะคำสั่งตรวจไวยากรณ์/รันเทสต์ที่ปลอดภัย (`py_compile`, `pytest`, `unittest`, `ruff check`, `flake8`, `mypy`, `git status/diff/log`) และบล็อก shell chaining/redirection ทุกชนิด คำสั่งอื่นยังเด้งถามยืนยันตามเดิม
  - **ตัวเบรกเมื่อเทสต์พังติดกัน:** หยุดและสรุปอาการอัตโนมัติเมื่อรันเทสต์ไม่ผ่านติดกันครบจำนวนครั้งที่ตั้งไว้ (`0–30`, ค่าเริ่มต้น `8`)

### 2. หน้าตรวจ Diff ราย Hunk & ย้อนกลับ Checkpoint ใน 1 คลิก
- **Interactive Diff Viewer:** รองรับคิวแก้หลายไฟล์พร้อมกัน เลือกใช้ทีละส่วน ตรวจแฮช SHA-256 ป้องกันไฟล์เปลี่ยนระหว่างรอ และเขียนไฟล์แบบ Atomic
- **Checkpoint History:** เปิดดู Unified Diff ของการแก้ไขทุกครั้งย้อนหลัง และกด **ย้อนกลับ (Rollback)** คืนไฟล์เดิมได้ในคลิกเดียว
- **External Drift Watcher:** แจ้งเตือนเมื่อไฟล์ถูกแก้ไขจากโปรแกรมภายนอก

### 3. เครื่องมือเขียนโค้ดครบชุดในหน้าต่างเดียว
- **Project Explorer & Multi-Tab Code Editor:** แสดงโครงสร้างโฟลเดอร์จริงพร้อมไอคอนล็อก `🔒` เตือนไฟล์ความลับ, ไฮไลต์สีโค้ดด้วย Pygments ครบหลายภาษา, รักษา Line Ending เดิม (`CRLF`/`LF`) และ `UTF-8 BOM`, ค้นหาในไฟล์ (`Ctrl+F`) และค้นหาทั้งโปรเจกต์ (`Ctrl+Shift+F`)
- **Safe Test Runner:** ค้นหา Python ของโปรเจกต์ผู้ใช้โดยอัตโนมัติ (`.venv` / `venv` / `PATH`), ล้างตัวแปร API Key ออกจาก Environment ของโปรเซสลูก, ตัดโปรเซสลูกทั้งต้นไม้ด้วย Windows Job Object, และปุ่มคำสั่งด่วน / **"ส่ง Error ให้ AI"** (`<= 100` บรรทัดท้าย) เป็นแบบ **เติมลงช่องให้ตรวจก่อนเสมอ (Populate-Only)** ไม่รันหรือส่งเอง
- **Async Git Panel:** รันคำสั่ง `git` ทุกตัวในเธรดเบื้องหลังไม่ทำให้หน้าจอค้าง, เตือนสร้าง `.gitignore` อัตโนมัติเมื่อเจอ `.venv`/`node_modules`, บล็อกการเผลอ Stage ไฟล์ความลับ, รองรับ Unstage ทั้งหมดบน Repo ใหม่, และมีหน้าต่างช่วยตั้งชื่อ/อีเมล Git ครั้งแรกให้อัตโนมัติ

### 4. รองรับ AI หลายค่าย & ระบบป้องกันผลาญงบ (Anti-Burn)
- รองรับ **Ollama**, **LM Studio** (โหลด/คืน RAM อัตโนมัติ), **Google Gemini**, **OpenRouter**, และ **Custom API 3 ช่อง** (พรีเซ็ตด่วน 7 ค่าย)
- ตั้งเพดานได้ละเอียด: Local Context สูงสุด `1,048,576`, Cloud Context สูงสุด `1,048,576`, Cloud Max Tokens (`0 = ตามค่าผู้ให้บริการ` ถึง `131,072`), เพดาน Token/รอบ, จุดพักถามทุกรอบ, เพดานค่าใช้จ่าย OpenRouter, และ Loop Breaker อัตโนมัติ
- สลับภาษา **ไทย | English** สดทันทีในหน้าตั้งค่า, ธีม **ดำสนิท (OLED `#000000`) / Dark / Light**, และเก็บประวัติแชทแยกตามโปรเจกต์ใน `%LOCALAPPDATA%\NoahArkCodeStudio\studio_chats.sqlite3` พร้อมปุ่ม `VACUUM` บีบอัดฐานข้อมูล

### 5. ใช้เดี่ยวๆ ก็ได้ หรือใช้คู่กับ Noah Ark AI Chat
- ใช้งานแยกอิสระได้ 100% หรือติดตั้งคู่กับ [Noah Ark AI Chat](https://github.com/Nightlance-Official/noah-ark-ai-chat) เพื่อให้แอปแชทตรวจเจออัตโนมัติผ่าน Windows Registry และส่งโฟลเดอร์งาน/ไฟล์/บรรทัด/บริบทแชทข้ามมาเปิดได้ใน 1 คลิก

---

## วิธีติดตั้งและเปิดใช้งานคีย์สิทธิ์ (ออฟไลน์)

1. ดาวน์โหลดไฟล์ **`NoahArkCodeStudio_Setup_v1.0.0.exe`** จากหน้า [Releases](https://github.com/Nightlance-Official/noah-ark-code-studio/releases/latest) แล้วติดตั้งให้เรียบร้อย
2. เปิดโปรแกรม **Noah Ark Code Studio** -> หน้าต่าง **ยืนยันคีย์สิทธิ์ใช้งาน** จะแสดง **รหัสเครื่อง (Machine ID)** ของคุณ (รูปแบบ `NCS-XXXX-XXXX-XXXX`)
3. กดปุ่ม **คัดลอกรหัสเครื่อง** แล้วทักส่งให้ทางเพจทางการเพื่อสั่งซื้อและรับ License Key:
   - **เพจทางการ (Facebook):** https://www.facebook.com/NightlanceOfficial
4. นำ **License Key** (`NACS1....`) มาวางในช่องแล้วกด **เปิดใช้งานโปรแกรม** -> ปลดล็อกและใช้งานแบบออฟไลน์ได้ทันที
5. **การอัปเดตเวอร์ชันใหม่:** กด **ตรวจหาอัปเดต** ในหน้าตั้งค่า โหลดตัวติดตั้งใหม่มาลงทับได้เลย คีย์สิทธิ์ (`license.key`), การตั้งค่า, ประวัติแชท และ Checkpoint ใน `%LOCALAPPDATA%\NoahArkCodeStudio\` จะอยู่ครบ 100%

### ความต้องการของระบบ
- **ระบบปฏิบัติการ:** Windows 10 / Windows 11 (64-bit)
- **RAM:** ขั้นต่ำ 4 GB (แนะนำ 8 GB ขึ้นไป หรือ 16 GB+ หากต้องการรันโมเดล Local บนเครื่อง)
- **โปรแกรมเสริม (ไม่บังคับ):** [Git for Windows](https://git-scm.com/) (สำหรับแท็บ Git), Python หรือเครื่องมือของโปรเจกต์ที่คุณพัฒนา, และ [Ollama](https://ollama.com/) / [LM Studio](https://lmstudio.ai/) สำหรับรัน AI ออฟไลน์

---

## ลิขสิทธิ์และสัญญาอนุญาต Open Source

Noah Ark Code Studio เป็นซอฟต์แวร์เชิงพาณิชย์แบบจำหน่ายคีย์สิทธิ์ผูกเครื่อง (1 คีย์ ต่อ 1 เครื่อง)

โปรแกรมนี้เชื่อมโยงแบบไดนามิกกับไลบรารี **Qt for Python (PySide6)** และ **Qt6** ภายใต้สัญญาอนุญาต **GNU Lesser General Public License v3.0 (LGPLv3)** โดยไฟล์ไลบรารี (`.dll` / `.pyd`) ถูกแยกไว้ในโฟลเดอร์ติดตั้งอย่างถูกต้องตามเงื่อนไข LGPLv3 และสามารถเปิดอ่านรายละเอียดสัญญาอนุญาตทั้งหมดได้จากไฟล์ `THIRD-PARTY-LICENSES.txt` หรือเมนู **ตั้งค่า -> สัญญาอนุญาต Open Source**

---

## ช่องทางติดต่อและแจ้งปัญหา

- **สั่งซื้อคีย์ & เพจทางการ (Facebook):** https://www.facebook.com/NightlanceOfficial
- **แจ้งบั๊ก / เสนอแนะ:** [GitHub Issues](https://github.com/Nightlance-Official/noah-ark-code-studio/issues)
