# Restaurant Management System (RMS)

> **ข้อสอบปฏิบัติการทดสอบและติดตั้งระบบซอฟต์แวร์เชิงธุรกิจ**  
> รายวิชา: การออกแบบและพัฒนาซอฟต์แวร์ 1

**✏️ กรอกข้อมูลของตนเอง:**

| รายการ | ข้อมูล |
|--------|--------|
| ชื่อ-นามสกุล | นายศรัณย์ สังขบุญ |
| รหัสนักศึกษา | 68030273 |
| วันที่สอบ | 14/11/2569 |

---

## Project Overview

ระบบจัดการร้านอาหาร (Restaurant Management System: RMS) เป็นระบบสำหรับจัดการเมนู การรับออเดอร์ การชำระเงิน และรายงานยอดขาย

**Source Repository:** `https://github.com/surachai-p/Restaurant-Management-System-Exam-2025.git`  
**✏️ Student Repository:** `https://github.com/JetSoGoof/Restaurant-Management-System-Exam-2025.git`

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + Vite + TypeScript + Tailwind CSS |
| Backend | Node.js 22 LTS + Express + TypeScript |
| Database | PostgreSQL 16 (Neon.tech) |
| ORM | Prisma |
| Testing | Vitest (Unit) + Newman (E2E) |
| Container | Docker / Docker Compose |
| CI/CD | GitHub Actions |

---

## Production URLs

**✏️ แทนที่ URL placeholder ด้วย URL จริงหลัง Deploy เสร็จ แล้วเปลี่ยนสถานะเป็น ✅ หรือ ❌**

| Service | URL (กรอก URL จริง) | สถานะ |
|---------|---------------------|-------|
| Frontend (Vercel) | https://restaurant-management-system-exam-2-sand.vercel.app/ | ✅ |
| Backend (Render) | https://rms-backend-68030273.onrender.com/api/health | ✅ |
| API Health Check (`/api/health`) | http://localhost:3001/api/health | ✅ |
| Database (Neon.tech connection string) | postgresql://exam-68030273_owner:npg_HnDV7MECRd5v@ep-nameless-feather-aoq62l8o-pooler.c-2.ap-southeast-1.aws.neon.tech/exam-68030273?sslmode=require&channel_binding=require | ✅ |

---

## Test Plan

> **ส่วนที่ 1 — แผนการทดสอบ (4 คะแนน)**

### 1.1 ขอบเขตการทดสอบ (Test Scope)

#### In Scope
**✏️ ระบุ Feature ที่จะทดสอบและเหตุผล (ตารางด้านล่างเป็นตัวอย่างเริ่มต้น แก้ไข/เพิ่มเติมได้)**

| Feature | เหตุผลที่ทดสอบ |
|---------|----------------|
| Auth | ตรวจสอบความถูกต้องของการเข้าสู่ระบบ Login การออกและตรวจสอบ JWT Token รวมถึงการจัดการสิทธิ์การเข้าถึงตามบทบาทผู้ใช้งาน |
| Menu |  ตรวจสอบการแสดงผลรายการอาหาร หมวดหมู่ ราคา และสถานะความพร้อมจำหน่าย รวมถึงการจัดการข้อมูลเมนูได้อย่างถูกต้อง |
| Order | ตรวจสอบขั้นตอนหลักของการให้บริการ ตั้งแต่การเปิดโต๊ะ เพิ่มรายการอาหาร ปรับจำนวน ยืนยันออเดอร์ และอัปเดตสถานะไปยังห้องครัว |
| Payment | ตรวจสอบความแม่นยำในการคำนวณยอดรวม ภาษี/ส่วนลด เงินทอน การบันทึกประวัติการชำระเงิน และการอัปเดตสถานะโต๊ะให้กลับเป็นว่างหลังปิดบิล |
| Report | ตรวจสอบความถูกต้องของข้อมูลสรุปยอดขายรายวัน จำนวนออเดอร์ และเมนูขายดี เพื่อใช้ประกอบการตัดสินใจและตรวจสอบบัญชีของร้าน |
| Security | ป้องกันการเข้าถึง API โดยไม่ได้รับอนุญาต |

#### Out of Scope
**✏️ ระบุสิ่งที่ไม่ทดสอบและเหตุผล อย่างน้อย 1 รายการ**

| Feature / ขอบเขตที่ไม่ทดสอบ | เหตุผล |
|-----------------------------|--------|
| Payment Gateway / QR PromptPay API | ระบบจำลองการคำนวณเงินสดและเงินทอนภายในแอปพลิเคชันเท่านั้น ไม่ได้เชื่อมต่อกับธนาคารหรือผู้ให้บริการชำระเงินภายนอก |
| Load / Stress Testing | สภาพแวดล้อม Production ใช้แผนบริการฟรี (Free Tier) บน Render และ Neon.tech จึงมุ่งเน้นการทดสอบความถูกต้องของฟังก์ชัน |

---

### 1.2 แนวทางการทดสอบ (Test Approach)

**✏️ ระบุประเภทการทดสอบ เครื่องมือ และรายละเอียดที่จะใช้จริง (ตารางด้านล่างเป็นตัวอย่างเริ่มต้น)**

| ประเภทการทดสอบ | เครื่องมือ | รายละเอียด |
|----------------|-----------|------------|
| Unit Testing | Vitest | ทดสอบความถูกต้องของ Business Logic ในฝั่ง Backend |
| API Testing (E2E) | Postman / Newman | ทดสอบการทำงานของ REST API Endpoints ทั้งหมดตาม Flow การใช้งานจริง |
| Security Testing | npm audit | สแกนตรวจสอบช่องโหว่ |
| Smoke Testing | Manual | ทดสอบฟังก์ชันหลักของระบบบนหน้าเว็บจริงหลังการติดตั้ง |
| Staging Test | Docker Compose | จำลองสภาพแวดล้อมใกล้เคียง Production ด้วยการรัน Backend และ Frontend ผ่าน Container |

---

### 1.3 สภาพแวดล้อมทดสอบ (Test Environment)

**✏️ กรอกเวอร์ชันจริงของเครื่องที่ใช้สอบ (รันคำสั่ง `node -v`, `npm -v`, `docker -v`, `newman -v` เพื่อตรวจสอบ)**

| รายการ | เวอร์ชัน / ค่า |
|--------|---------------|
| OS | win11 |
| Node.js | v24.14.0 |
| npm | 11.9.0 |
| Docker | Docker version 29.2.1, build a5c7197 |
| PostgreSQL | 16 (Neon.tech) |
| Browser | |
| Newman | 6.2.3 |

---

### 1.4 เงื่อนไขการผ่าน/ไม่ผ่านการทดสอบ (Entry / Exit Criteria)

#### Entry Criteria — ✏️ ทำเครื่องหมาย ✅ เมื่อทำสำเร็จแล้ว
- [✅] Repository ถูก Clone และรัน Backend + Frontend ได้
- [✅] Database เชื่อมต่อ Neon.tech สำเร็จ
- [✅] `/api/health` ตอบกลับ `{"status":"ok"}`
- [✅] Postman Collection พร้อมสำหรับ Newman

#### Exit Criteria (เงื่อนไขผ่านการทดสอบ)
**✏️ ระบุเงื่อนไขที่ถือว่าผ่านการทดสอบและพร้อม Deploy**

| เงื่อนไข | ค่าที่กำหนด |
|---------|------------|
| Newman Pass Rate ขั้นต่ำ | ≥ 80% |
| Bug ระดับ Critical ที่ยังเปิดอยู่ | ≤ 0 รายการ |
| Smoke Test บน Production ผ่าน | 4 / 4 Feature |

---

### 1.5 ความเสี่ยงเชิงธุรกิจ (Business Risk)

> **✏️ ระบุ Feature ของระบบ RMS ที่หากเกิดความผิดพลาดแล้วจะกระทบการดำเนินธุรกิจ อย่างน้อย 2 รายการ**  
> ระดับความเสี่ยง: `Critical` / `High` / `Medium` / `Low`

| # | Feature ที่มีความเสี่ยง | ผลกระทบหากเกิดความผิดพลาด | ระดับความเสี่ยง |
|---|------------------------|--------------------------|----------------|
| 1 | Payment Calculation Logic | ระบบชำระเงินยอมรับยอดเงินที่น้อยกว่าค่าอาหารจริง และบันทึกเงินทอนติดลบ | Critical |
| 2 | Authentication & Authorization | ผู้ใช้งานที่ไม่มีสิทธิ์ สามารถเข้าถึงข้อมูลยอดขายหรือแก้ไขราคาสินค้าได้ | Critical|
| 3 | Order Management | เกิดการเปิดบิลซ้ำซ้อนบนโต๊ะเดียวกัน | High |

---

## Test Cases & Results

> **ส่วนที่ 2 — กรณีทดสอบ (8 คะแนน)**

### กรณีทดสอบทั้งหมด (≥ 10 กรณี — sub-category: Positive ≥ 3 | Negative ≥ 3 | Security ≥ 3 | Edge ≥ 2)

**✏️ กรอกข้อมูลทุกคอลัมน์ให้ครบ รวมถึง Actual Result และ Pass/Fail หลังทดสอบจริง**

| TC-ID | Type | Feature | Scenario | Input | Expected Result | Actual Result | Pass/Fail |
|-------|------|---------|----------|-------|----------------|---------------|-----------|
| TC-001 | GET /api/health (Positive) | GET | `/api/health` | HTTP 200 OK (`status: "ok"`, `version: "2.0.0"`) | ✅ |
| TC-002 | Login Admin (Positive) | POST | `/api/auth/login` | HTTP 200 OK ได้รับ JWT Token | ✅ |
| TC-003 | Login Cashier | POST | `/api/auth/login` | HTTP 200 OK ได้รับ JWT Token | ✅ |
| TC-004 | Login Waiter | POST | `/api/auth/login` | HTTP 200 OK ได้รับ JWT Token | ✅ |
| TC-005 | Login Wrong Password (Negative) | POST | `/api/auth/login` | HTTP 401 Unauthorized | ✅ |
| TC-006 | Login Missing Credentials (Negative) | POST | `/api/auth/login` | HTTP 400 Bad Request | ✅ |
| TC-007 | No Token → 401 (Security) | GET | `/api/menu` | HTTP 401 Unauthorized (`Access token required`) | ✅ |
| TC-008 | GET /menu (Positive) | GET | `/api/menu` | HTTP 200 OK คืนค่ารายการเมนูทั้งหมด (Array) | ✅ |
| TC-009 | Search Menu (Positive) | GET | `/api/menu?search=Pad+Thai` | HTTP 200 OK คืนค่าเมนูที่ค้นหาสำเร็จ | ✅ |
| TC-010 | SQL Injection in Search (Security - BUG-003) | GET | `/api/menu?search=' OR '1'='1` | HTTP 200 OK คืนค่ารายการเมนูทั้งหมด  | ❌ |
| TC-011 | Waiter Updates Menu Price (Security - BUG-004) | PUT | `/api/menu/4` | HTTP 200 OK แก้ไขราคาสำเร็จ  | ❌ |

**✏️ สรุปผล:** ผ่าน 9 / 11 กรณี (100%)

---

## Test Reports

> **ส่วนที่ 3 — การทดสอบและรายงานผล (20 คะแนน)**

### Postman Test Evidence
> Rubric 1.4: สร้าง Collection + ตั้งค่า Environment + รันครบ + บันทึกผล + แนบรูป

#### ชื่อ Collection และไฟล์ที่ Export

**✏️ แทนที่ `[รหัสนักศึกษา]` ด้วยรหัสจริง**

| รายการ | ค่าจริง |
|--------|--------|
| Collection Name | `RMS-68030273-TestSuite` |
| ไฟล์ที่ Export ไปไว้ใน Repository | `tests/postman/RMS-68030273-TestSuite.json` |
| ไฟล์ Environment | `tests/postman/env.json` |

> 📌 Repository มี Newman Collection 21 test cases ใน `tests/postman/` อยู่แล้ว  
> นักศึกษาต้องสร้าง Collection ของตนเองที่ครอบคลุมกรณีทดสอบในส่วนที่ 2

#### Environment Variables ที่ต้องตั้งค่าใน Postman

**✏️ ค่าในคอลัมน์ "ค่าที่ตั้งจริง" ให้กรอกหลังจาก Login สำเร็จและได้ Token มาแล้ว**

| Variable | ค่าที่ตั้งจริง | ใช้สำหรับ |
|----------|--------------|-----------|
| `{{base_url}}` | | `https://rms-backend-68030273.onrender.com/api |
| `{{token}}` | eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwidXNlcm5hbWUiOiJjYXNoaWVyMSIsInJvbGUiOiJjYXNoaWVyIiwibmFtZSI6IkNhc2hpZXIgT25lIiwiaWF0IjoxNzk0NjQ0NTk3LCJleHAiOjE3OTQ2NzMzOTd9.MVwL5Wc1dEtD_WjGIMUesGv6OQwLplWQHSnM7IEtqro | Request ที่ต้องใช้ Token |
| `{{admin_token}}` | eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwidXNlcm5hbWUiOiJhZG1pbiIsInJvbGUiOiJhZG1pbiIsIm5hbWUiOiJBZG1pbiBVc2VyIiwiaWF0IjoxNzk0NjQyMDg4LCJleHAiOjE3OTQ2NzA4ODh9.Tei2pEyeHo1tDLiMg77y4Qx9cvi1SYs5gR8xEDbpKV4 | Request ที่ต้องการสิทธิ์ Admin |

#### pm.test Scripts ใน Collection
> ⚠️ ทุก Request ใน Collection ต้องมี `pm.test(...)` ตรวจสอบ Response  
> ตัวอย่าง:
> ```javascript
> pm.test("Status code is 200", function () {
>     pm.response.to.have.status(200);
> });
> pm.test("Response has JWT token", function () {
>     const jsonData = pm.response.json();
>     pm.expect(jsonData).to.have.property('token');
> });
> ```

**✏️ ยืนยันว่าทุก Request มี pm.test แล้ว:** ✅ ใช่

#### สรุปผลการรัน Postman (กรอกหลังรัน Collection Run)

**✏️ กรอกผลจริงจาก Postman Collection Runner**

| Request Name | Method | Endpoint | Actual Result | Pass/Fail |
|-------------|--------|----------|--------------|-----------|
|-------------|--------|----------|--------------|-----------|
| TC-001 | GET /api/health (Positive) | GET | `/api/health` | HTTP 200 OK (`status: "ok"`, `version: "2.0.0"`) | ✅ |
| TC-002 | Login Admin (Positive) | POST | `/api/auth/login` | HTTP 200 OK ได้รับ JWT Token | ✅ |
| TC-003 | Login Cashier | POST | `/api/auth/login` | HTTP 200 OK ได้รับ JWT Token | ✅ |
| TC-004 | Login Waiter | POST | `/api/auth/login` | HTTP 200 OK ได้รับ JWT Token | ✅ |
| TC-005 | Login Wrong Password (Negative) | POST | `/api/auth/login` | HTTP 401 Unauthorized | ✅ |
| TC-006 | Login Missing Credentials (Negative) | POST | `/api/auth/login` | HTTP 400 Bad Request | ✅ |
| TC-007 | No Token → 401 (Security) | GET | `/api/menu` | HTTP 401 Unauthorized (`Access token required`) | ✅ |
| TC-008 | GET /menu (Positive) | GET | `/api/menu` | HTTP 200 OK คืนค่ารายการเมนูทั้งหมด (Array) | ✅ |
| TC-009 | Search Menu (Positive) | GET | `/api/menu?search=Pad+Thai` | HTTP 200 OK คืนค่าเมนูที่ค้นหาสำเร็จ | ✅ |
| TC-010 | SQL Injection in Search (Security - BUG-003) | GET | `/api/menu?search=' OR '1'='1` | HTTP 200 OK คืนค่ารายการเมนูทั้งหมด  SQL | ❌ |
| TC-011 | Waiter Updates Menu Price (Security - BUG-004) | PUT | `/api/menu/4` | HTTP 200 OK แก้ไขราคาสำเร็จ (พบข้อบกพร่อง [BUG-004] ไม่จำกัดสิทธิ์ Waiter) | ❌ |
| TC-012 | Admin Adds Menu Item (Positive) | POST | `/api/menu` | HTTP 201 Created เพิ่มเมนูใหม่สำเร็จ | ✅ |
| TC-013 | Waiter Cannot Add Menu Item (Negative - Role Check) | POST | `/api/menu` | HTTP 403 Forbidden ปฏิเสธสิทธิ์ Waiter ถูกต้อง | ✅ |
| TC-014 | Create Order (Positive) | POST | `/api/orders` | HTTP 201 Created เปิดออเดอร์ใหม่สำเร็จ | ✅ |
| TC-015 | Double Booking Same Table (BUG-002) | POST | `/api/orders` | HTTP 201 Created สร้างออเดอร์ซ้ำโต๊ะเดิมได้  | ❌ |
| TC-016 | Add Item to Order | POST | `/api/orders/2/items` | HTTP 201 Created เพิ่มรายการอาหารลงออเดอร์สำเร็จ | ✅ |
| TC-017 | Confirm Order | PUT | `/api/orders/2/confirm` | HTTP 200 OK ยืนยันออเดอร์สำเร็จ | ✅ |
| TC-018 | Create Order Without TableId (Negative) | POST | `/api/orders` | HTTP 400 Bad Request แจ้งเตือนเมื่อไม่ระบุ TableId | ✅ |
| TC-019 | Exact Payment (Positive) | POST | `/api/payments` | HTTP 201 Created ชำระเงินสำเร็จและคำนวณเงินทอนถูกต้อง | ✅ |
| TC-020 | Underpayment (BUG-001) | POST | `/api/payments` | พบข้อบกพร่อง  ระบบไม่ตรวจสอบยอดเงินขาด (คาดหวัง HTTP 400) | ❌ |
| TC-021 | Payment Without Auth (Security) | POST | `/api/payments` | HTTP 401 Unauthorized (`Access token required`) | ✅ |

**✏️ สรุป:** ผ่าน 17 / 21 Request *

#### หลักฐานภาพหน้าจอ Postman

**✏️ แทนที่ข้อความด้านล่างด้วยภาพจริง โดยใช้ syntax: `![คำอธิบาย](./tests/reports/ชื่อไฟล์.png)`**

**รูปที่ 1 — Postman Collection และ Environment Variables (แสดง `base_url`, `token`, `admin_token` ครบ)**

`![Postman Collection + Env Vars](./tests/reports/postman-collection-env.png)`
![แสดง `base_url`, `token`, `admin_token` ครบ](image-1.png)
**รูปที่ 2 — ผล Postman Collection Run (แสดง Pass/Fail ทุก Request)**

`![Postman Run Result](./tests/reports/postman-run-result.png)`
![แสดง Pass/Fail ทุก Request](image.png)
---

### Newman E2E Test Summary

#### คำสั่งรัน Newman

```bash
# ติดตั้ง Newman (ถ้ายังไม่ได้ติดตั้ง)
npm install -g newman newman-reporter-htmlextra

# รัน Collection
newman run tests/postman/RMS-[รหัสนักศึกษา]-TestSuite.json \
    --environment tests/postman/env.json \
    --reporters cli,htmlextra \
    --reporter-htmlextra-export tests/reports/newman-report.html
```

#### ผลการรัน Newman (Local)

**✏️ วาง output จาก Terminal ที่ได้หลังรัน Newman แทนที่ข้อความ template ด้านล่างทั้งหมด**

```
$ newman run tests/postman/RMS-68030273-TestSuite.json \
    --environment tests/postman/env.json \
    --reporters cli,htmlextra \
    --reporter-htmlextra-export tests/reports/newman-report.html
(node:7072) [DEP0176] DeprecationWarning: fs.F_OK is deprecated, use fs.constants.F_OK instead
(Use `node --trace-deprecation ...` to show where the warning was created)
newman

RMS-68030273-TestSuite

□ Health & System
└ TC-001 GET /api/health (Positive)
  GET https://rms-backend-68030273.onrender.com/api/health [200 OK, 600B, 196ms]
  √  TC-001: health returns 200
  √  TC-001: status is ok
  √  TC-001: version 2.0.0

□ Authentication
└ TC-002 Login Admin (Positive)
  POST https://rms-backend-68030273.onrender.com/api/auth/login [200 OK, 821B, 1085ms]
  √  TC-002: admin login 200
  √  TC-002: returns JWT token

└ TC-003 Login Cashier
  POST https://rms-backend-68030273.onrender.com/api/auth/login [200 OK, 835B, 478ms]
  √  TC-003: cashier login 200

└ TC-004 Login Waiter
  POST https://rms-backend-68030273.onrender.com/api/auth/login [200 OK, 828B, 514ms]
  √  TC-004: waiter login 200

└ TC-005 Login Wrong Password (Negative)
  POST https://rms-backend-68030273.onrender.com/api/auth/login [401 Unauthorized, 569B, 509ms]
  √  TC-005: wrong password → 401

└ TC-006 Login Missing Credentials (Negative)
  POST https://rms-backend-68030273.onrender.com/api/auth/login [400 Bad Request, 579B, 57ms]
  √  TC-006: missing creds → 400

└ TC-007 No Token → 401 (Security)
  GET https://rms-backend-68030273.onrender.com/api/menu [401 Unauthorized, 571B, 51ms]
  √  TC-007: no token → 401

□ Menu
└ TC-008 GET /menu (Positive)
  GET https://rms-backend-68030273.onrender.com/api/menu [200 OK, 3.14kB, 68ms]
  √  TC-008: get menu 200
  √  TC-008: returns array

└ TC-009 Search Menu (Positive)
  GET https://rms-backend-68030273.onrender.com/api/menu?search=Pad+Thai [200 OK, 749B, 64ms]
  √  TC-009: search returns results

└ TC-010 SQL Injection in Search (Security - BUG-003)
  GET https://rms-backend-68030273.onrender.com/api/menu?search=' OR '1'='1 [200 OK, 3.14kB, 56ms]
  1. TC-010 [BUG-003]: SQL Injection should NOT leak all records

└ TC-011 Waiter Updates Menu Price (Security - BUG-004)
  PUT https://rms-backend-68030273.onrender.com/api/menu/4 [200 OK, 747B, 70ms]
  2. TC-011 [BUG-004]: Waiter cannot update menu price (expect 403)

└ TC-012 Admin Adds Menu Item (Positive)
  POST https://rms-backend-68030273.onrender.com/api/menu [201 Created, 725B, 64ms]
  √  TC-012: admin adds menu item → 201

└ TC-013 Waiter Cannot Add Menu Item (Negative - Role Check)
  POST https://rms-backend-68030273.onrender.com/api/menu [403 Forbidden, 571B, 49ms]
  √  TC-013: waiter cannot add menu → 403

□ Orders
└ TC-014 Create Order (Positive)
  POST https://rms-backend-68030273.onrender.com/api/orders [201 Created, 691B, 75ms]
  √  TC-014: create order → 201

└ TC-015 Double Booking Same Table (BUG-002)
  POST https://rms-backend-68030273.onrender.com/api/orders [201 Created, 691B, 61ms]
  3. TC-015 [BUG-002]: Double booking → 409 Conflict

└ TC-016 Add Item to Order
  POST https://rms-backend-68030273.onrender.com/api/orders/6/items [201 Created, 869B, 104ms]
  √  TC-016: add item → 201

└ TC-017 Confirm Order
  PUT https://rms-backend-68030273.onrender.com/api/orders/6/confirm [200 OK, 691B, 60ms]
  √  TC-017: confirm order → 200

└ TC-018 Create Order Without TableId (Negative)
  POST https://rms-backend-68030273.onrender.com/api/orders [400 Bad Request, 565B, 47ms]
  √  TC-018: missing tableId → 400

□ Payment
└ TC-019 Exact Payment (Positive)
  POST https://rms-backend-68030273.onrender.com/api/payments [201 Created, 785B, 72ms]
  √  TC-019: payment → 201
  √  TC-019: change is non-negative

└ TC-020 Underpayment (BUG-001)
  POST https://rms-backend-68030273.onrender.com/api/payments [404 Not Found, 562B, 58ms]
  4. TC-020 [BUG-001]: Underpayment should → 400

└ TC-021 Payment Without Auth (Security)
  POST https://rms-backend-68030273.onrender.com/api/payments [401 Unauthorized, 571B, 56ms]
  √  TC-021: no auth → 401

┌─────────────────────────┬─────────────────────┬────────────────────┐
│                         │            executed │             failed │
├─────────────────────────┼─────────────────────┼────────────────────┤
│              iterations │                   1 │                  0 │
├─────────────────────────┼─────────────────────┼────────────────────┤
│                requests │                  21 │                  0 │
├─────────────────────────┼─────────────────────┼────────────────────┤
│            test-scripts │                  21 │                  0 │
├─────────────────────────┼─────────────────────┼────────────────────┤
│      prerequest-scripts │                   0 │                  0 │
├─────────────────────────┼─────────────────────┼────────────────────┤
│              assertions │                  26 │                  4 │
├─────────────────────────┴─────────────────────┴────────────────────┤
│ total run duration: 5.6s                                           │
├────────────────────────────────────────────────────────────────────┤
│ total data received: 8.1kB (approx)                                │
├────────────────────────────────────────────────────────────────────┤
│ average response time: 180ms [min: 47ms, max: 1085ms, s.d.: 253ms] │
└────────────────────────────────────────────────────────────────────┘

  #  failure                       detail                                                                                                                
                                                                                                                                                         
 1.  AssertionError                TC-010 [BUG-003]: SQL Injection should NOT leak all records                                                           
                                   BUG-003: SQL Injection leaked 12 records: expected 12 to equal +0                                                     
                                   at assertion:0 in test-script                                                                                         
                                   inside "Menu / TC-010 SQL Injection in Search (Security - BUG-003)"                                                   
                                                                                                                                                         
 2.  AssertionError                TC-011 [BUG-004]: Waiter cannot update menu price (expect 403)                                                        
                                   expected response to have status code 403 but got 200                                                                 
                                   at assertion:0 in test-script                                                                                         
                                   inside "Menu / TC-011 Waiter Updates Menu Price (Security - BUG-004)"                                                 
                                                                                                                                                         
 3.  AssertionError                TC-015 [BUG-002]: Double booking → 409 Conflict                                                                       
                                   expected response to have status code 409 but got 201                                                                 
                                   at assertion:0 in test-script                                                                                         
                                   inside "Orders / TC-015 Double Booking Same Table (BUG-002)"                                                          
                                                                                                                                                         
 4.  AssertionError                TC-020 [BUG-001]: Underpayment should → 400                                                                           
                                   expected response to have status code 400 but got 404                                                                 
                                   at assertion:0 in test-script                                                                                         
                                   inside "Payment / TC-020 Underpayment (BUG-001)"  
```

**✏️ กรอกตัวเลขจริงจาก Newman output:**

| Metric | ค่าจริง |
|--------|--------|
| Total Requests |26 |
| Tests Passed |22 |
| Tests Failed | 4 |
| Pass Rate | 84.62% |

**รูปที่ 3 — ผล Newman CLI (แสดง Pass/Fail summary)**

`![Newman Run Result](./tests/reports/newman-cli-result.png)`
![alt text](image-2.png)
---

### Automated Testing via CI Pipeline
> Rubric 1.6: สคริปต์อัตโนมัติ + รันผ่าน CI ได้ + บันทึกผล

**✏️ ทำเครื่องหมาย ✅ เมื่อทำเสร็จแล้ว และแนบหลักฐานรูปภาพ**

| รายการ | สถานะ |
|--------|-------|
| Newman Collection JSON อยู่ที่ `tests/postman/` ใน Repository | ✅ |
| `.github/workflows/cicd.yml` มี step ติดตั้งและรัน Newman | ✅ |
| GitHub Actions Pipeline รันสำเร็จ (สีเขียว) | ✅ |
| Newman Pass Rate บันทึกอยู่ใน Pipeline log | ✅ |

**✏️ Newman Pass Rate จาก CI/CD:** 4 / 4 (100%)

**รูปที่ 4 — GitHub Actions Pipeline สำเร็จ (แสดง Newman step และ Pass Rate)**

![alt text](image-4.png)

---

## Security Scan Report

> ส่วนที่ 3.4 — Rubric 1.7: รันทั้ง Backend + Frontend + บันทึกผล + ระบุ CVE + เพิ่มใน CI

### Backend Security Scan

```bash
cd backend && npm audit --audit-level=moderate
```

**✏️ กรอกจำนวนช่องโหว่จริงที่พบ (ถ้าไม่มีให้ใส่ 0)**

| Severity | จำนวน |
|----------|-------|
| Critical | 1 |
| High |6 |
| Medium |4 |
| Low |1 |
| **รวม** |12 |

**✏️ กรอกรายละเอียด Dependency ที่มีช่องโหว่ระดับ High ขึ้นไป (ถ้าไม่มีให้ระบุ "ไม่พบช่องโหว่")**

| Package | CVE ID | Severity | เวอร์ชันที่มีปัญหา | เวอร์ชันที่ปลอดภัย | สถานะการแก้ไข |
|---------|--------|----------|--------------------|--------------------|--------------| 
|proxy-addr |GHSA-jqcg-44mw-7w3h |Critical |1.1.0 - 2.0.7 |> 2.0.7 |มีแพตช์แก้ไข |

**รูปที่ 5 — ผล npm audit Backend**

`![Backend npm audit](./tests/reports/npm-audit-backend.png)`
![alt text](image-5.png)
---

### Frontend Security Scan

```bash
cd frontend && npm audit --audit-level=moderate
```

**✏️ กรอกจำนวนช่องโหว่จริงที่พบ**

| Severity | จำนวน |
|----------|-------|
| Critical |0 |
| High |8 |
| Medium |6 |
| Low |1 |
| **รวม** | 15|

**รูปที่ 6 — ผล npm audit Frontend**

`![Frontend npm audit](./tests/reports/npm-audit-frontend.png)`
![alt text](image-6.png)
### Security Scan ใน CI Pipeline (Rubric 1.7 ข้อ 4)

**✏️ ยืนยันว่าได้เพิ่ม `npm audit --audit-level=high` ใน `.github/workflows/cicd.yml` แล้ว:** ✅ ใช่

**รูปที่ 7 — GitHub Actions แสดง npm audit step รันสำเร็จ**

`![CI Security Scan](./tests/reports/ci-security-scan.png)`
![alt text](image-7.png)
---

## Bug Reports

> ส่วนที่ 3 — Rubric 1.5: รายงานข้อบกพร่อง อย่างน้อย 2 รายการ พร้อม Business Impact

---

### BUG-001: ให้ชำระเงินน้อยกว่ายอดรวมและบันทึกเงินทอนติดลบ

| รายการ | ค่า |
|--------|-----|
| **Severity** | Critical |
| **Priority** | P1 |
| **Feature** | Payment Processing|
| **Status** | Open |

#### Steps to Reproduce
**✏️ ระบุขั้นตอนที่ทำให้เกิด Bug ซ้ำได้ชัดเจน**
1. เข้าสู่ระบบด้วยบัญชีผู้ใช้งานที่มีสิทธิ์รับชำระเงินเพื่อรับ JWT Token
2. สร้างออเดอร์ใหม่ ที่มีรายการอาหารรวมยอดสุทธิ เช่น 200 บาท และบันทึก orderId ที่ได้
3. ส่งคำขอชำระเงิน โดยระบุ orderId ดังกล่าว และใส่จำนวนเงินที่จ่าย น้อยกว่ายอดรวม เช่น 150 บาท

#### Expected Result
> ✏️ ระบบต้องปฏิเสธการทำรายการและส่ง HTTP Status 400 Bad Request กลับมา พร้อมข้อความแจ้งเตือนว่าจำนวนเงินที่ชำระไม่เพียงพอ

#### Actual Result
> ✏️ ระบบยอมรับการชำระเงินสำเร็จปิดสถานะออเดอร์ และคำนวณค่าเงินทอน บันทึกลงฐานข้อมูลเป็นค่าติดลบ

#### Evidence

`![BUG-001](./tests/reports/bug-001.png)`
![alt text](image-8.png)![alt text](image-10.png)
#### Business Impact
> ✏️ Business Impact
ร้านอาหารสูญเสียรายได้โดยตรงจากการที่ลูกค้าหรือพนักงานสามารถปิดบิลได้โดยจ่ายเงินไม่ครบตามยอดจริง

---

### BUG-002: ของไม่มีแต่สั่งได้

| รายการ | ค่า |
|--------|-----|
| **Severity** | High |
| **Priority** | P1  |
| **Feature** | Order Management|
| **Status** |  Open |

#### Steps to Reproduce
**✏️ ระบุขั้นตอนที่ทำให้เกิด Bug ซ้ำได้ชัดเจน**
1. เข้าสู่ระบบ เพื่อรับ JWT Token
2. ตรวจสอบรหัสเมนูอาหารที่มีอยู่ในระบบผ่าน
3. ส่งคำขอสร้างออเดอร์โดยระบุหมายเลขโต๊ะที่ถูกต้อง แต่กำหนดจำนวนสินค้า

#### Expected Result
> ✏️ ระบบต้องตรวจสอบความถูกต้องของข้อมูลและปฏิเสธคำขอด้วย HTTP Status 400 Bad Request

#### Actual Result
> ✏️ ระบบยอมรับคำขอและสร้างออเดอร์สำเร็จ ส่งผลให้ยอดรวมของออเดอร์ คำนวณออกมาเป็นค่าติดลบหรือศูนย์

#### Evidence

`![BUG-002](./tests/reports/bug-002.png)`
![alt text](image-9.png)![alt text](image-11.png)
#### Business Impact
> ✏️ Business Impact
ส่งผลกระทบต่อความถูกต้องของข้อมูลการสั่งอาหารในครัว ทำให้ยอดรวมบิลผิดเพี้ยน
---

## Deployment Guide

> ส่วนที่ 4 & 5 — คู่มือการติดตั้ง

### Prerequisites

| รายการ | เวอร์ชันที่ต้องการ |
|--------|------------------|
| Node.js | 22 LTS |
| Git | ล่าสุด |
| Docker | ล่าสุด |
| Docker Compose | v2+ |

---

### Local Setup (Docker Compose + Manual)

#### On-Premises Setup
> **ส่วนที่ 4.1 — ติดตั้งบนเครื่องตนเองในรูปแบบ On-Premises Server (8 คะแนน)**

**ขั้นตอนการติดตั้ง:**

```bash
# 1. Clone Repository
git clone https://github.com/[รหัสนักศึกษา]/Restaurant-Management-System-Exam-2025.git
cd Restaurant-Management-System-Exam-2025

# 2. ตั้งค่า Environment Variables (Backend)
cp backend/.env.example backend/.env
# เปิดไฟล์ backend/.env แล้วกรอกค่า:
#   DATABASE_URL=postgresql://...
#   JWT_SECRET=...
#   CORS_ORIGIN=http://localhost:5173
#   NODE_ENV=development

# 3. รัน Backend (Port 3001)
cd backend && npm install && npm run dev

# 4. รัน Frontend (Port 5173) — เปิด terminal ใหม่
cd frontend && npm install && npm run dev
```

> ⚠️ **หมายเหตุเรื่อง Port**:
> - **Local / On-Premises**: ขั้นตอนกำหนด Port 3001 แต่ URL หลักฐานในข้อสอบระบุ `localhost:3000/api/health` ให้ตรวจสอบค่า `PORT` ใน `backend/.env.example` ของ Repository จริง แล้วใช้ port ที่ระบบรันจริง
> - **Render.com**: Backend รันบน **Port 10000** เสมอ (กำหนดใน `render.yaml` และ Render Dashboard) — `VITE_API_URL` ใช้ `https://[api].onrender.com` โดยไม่ต้องระบุ port

#### การตั้งค่า Service / Port จริงที่ใช้ (Rubric 2.1 ข้อ 2)

**✏️ กรอกค่าจริงที่ตั้งบนเครื่องของตนเอง**

| Service | Port ที่รันจริง | ค่า CORS_ORIGIN ที่ตั้ง | ค่า VITE_API_URL ที่ตั้ง |
|---------|---------------|------------------------|------------------------|
| Backend API |3001 |http://localhost:5173 | — |
| Frontend |5173 | — |http://localhost:3001/api |

#### ผล Smoke Test — On-Premises

**✏️ ทดสอบหลังรัน Backend + Frontend สำเร็จ แล้วทำเครื่องหมายผล**

| ทดสอบ | URL | ผลลัพธ์ที่คาดหวัง | ผ่าน/ไม่ผ่าน |
|-------|-----|-----------------|-------------|
| Backend Health Check | `http://localhost:[port]/api/health` | `{"status":"ok"}` | ☐ |
| Frontend Login | `http://localhost:5173` | หน้า Login แสดงผลสำเร็จ | ☐ |

#### หลักฐาน On-Premises

**รูปที่ 8 — Backend Health Check (`/api/health` ตอบ `{"status":"ok"}`)**
![alt text](image-12.png)
`![On-Premises Backend Health](./tests/reports/onprem-backend-health.png)`

**รูปที่ 9 — Frontend Login สำเร็จ**

`![On-Premises Frontend Login](./tests/reports/onprem-frontend-login.png)`
![alt text](image-13.png)
---

#### Staging Environment (Docker Compose)
> **ส่วนที่ 4.2 — ติดตั้งด้วย Docker Compose (8 คะแนน)**

**สิ่งที่ต้องแก้ไขใน `docker-compose.yml`:**

**✏️ ทำเครื่องหมาย ✅ เมื่อแก้ไขเสร็จแล้ว**

- [✅ ] เพิ่ม Environment Variables ครบถ้วน (`DATABASE_URL`, `JWT_SECRET`, `CORS_ORIGIN`, `VITE_API_URL`)
- [ ✅] กำหนด Port Mapping: backend → 3001, frontend → 80
- [ ✅] เพิ่ม Health Check สำหรับ backend service
- [ ✅] กำหนด `depends_on` ให้ frontend รอ backend พร้อมก่อน

#### Environment Variables ที่ตั้งค่าจริงใน `docker-compose.yml` (Rubric 2.2 ข้อ 2)

**✏️ กรอกค่าจริงที่ใส่ใน docker-compose.yml (JWT_SECRET ไม่ต้องระบุค่าจริง)**

| Variable | Service | ค่าที่ตั้งจริง |
|----------|---------|--------------|
| `DATABASE_URL` | backend |postgresql://exam-68030273_owner:npg_HnDV7MECRd5v@ep-nameless-feather-aoq62l8o-pooler.c-2.ap-southeast-1.aws.neon.tech/exam-68030273?sslmode=require&channel_binding=require |
| `JWT_SECRET` | backend | (ตั้งค่าแล้ว — ไม่ระบุค่าจริงเพื่อความปลอดภัย) |
| `CORS_ORIGIN` | backend |https://restaurant-management-system-exam-2-sand.vercel.app |
| `NODE_ENV` | backend |production |
| `VITE_API_URL` | frontend |https://rms-backend-68030273.onrender.com/api |

#### Multi-stage Build (Rubric 2.5 ข้อ 2)

**✏️ ตรวจสอบ Dockerfile ของแต่ละ service แล้วระบุผล**

| Service | มี Multi-stage Build | Stage ที่ใช้ (เช่น builder → runner) |
|---------|--------------------|------------------------------------|
| Backend | ✅ มี / ☐ ไม่มี |deps → builder → runner |
| Frontend | ✅ มี / ☐ ไม่มี |builder → nginx:alpine |

**รูปที่ 10 — Dockerfile แสดง Multi-stage build**

`![Multi-stage Dockerfile](./tests/reports/dockerfile-multistage.png)`
![alt text](image-14.png)
#### Volume Mapping (Rubric 2.5 ข้อ 4)

**✏️ ระบุ Volume ที่กำหนดใน docker-compose.yml (ถ้าไม่มีให้ระบุ "ไม่มี Volume mapping")**

| Volume Name / Path | Host Path | Container Path | วัตถุประสงค์ |
|-------------------|-----------|----------------|-------------|
|ไม่มี Volume mapping | | | |

#### Network Configuration (Rubric 2.5 ข้อ 5)

**✏️ ระบุ Network ที่กำหนดใน docker-compose.yml**

| Network Name | Driver | Services ที่อยู่ใน Network นี้ |
|-------------|--------|-------------------------------|
|default |bridge |backend (rms-backend), frontend (rms-frontend) |

#### คำสั่งรัน Staging

```bash
docker compose up --build
```

#### ผล Smoke Test — Staging

**✏️ ทดสอบหลัง `docker compose up` สำเร็จ**

| ทดสอบ | URL | ผลลัพธ์ที่คาดหวัง | ผ่าน/ไม่ผ่าน |
|-------|-----|-----------------|-------------|
| Backend Health Check | `http://localhost:3001/api/health` | `{"status":"ok"}` | ✅ |
| Frontend | `http://localhost:80` | หน้า Login แสดงผลสำเร็จ | ✅ |

#### หลักฐาน Staging

**รูปที่ 11 — `docker compose ps` แสดงทุก Container สถานะ `running`**

`![Docker Compose PS](./tests/reports/staging-docker-ps.png)`
![alt text](image-16.png)
---

### Neon.tech Database Setup
> ส่วนที่ 5.1

**ขั้นตอน:**
1. ไปที่ https://console.neon.tech → Create Project → PostgreSQL 16
2. คัดลอก Connection String รูปแบบ: `postgresql://user:pass@ep-xxx.neon.tech/db?sslmode=require`
3. นำไปใช้เป็นค่า `DATABASE_URL` ใน Backend

**✏️ Connection String ที่ใช้จริง (เบลอ password ก่อนบันทึก):**

`postgresql://exam-68030273_owner:xxxxxxxxxx@ep-nameless-feather-aoq62l8o-pooler.c-2.ap-southeast-1.aws.neon.tech/exam-68030273?sslmode=require&channel_binding=require
`

---

### Render + Vercel Deployment Steps
> ส่วนที่ 5.2 & 5.3

#### Backend บน Render.com

> 📌 Repository มีไฟล์ `render.yaml` ที่ root — สามารถใช้ **New Blueprint** บน Render Dashboard เพื่อ Deploy อัตโนมัติจากไฟล์นี้แทนการตั้งค่าทีละอย่าง

```
Build Command:  docker build -t rms-backend ./backend
Dockerfile:     ./backend/Dockerfile
PORT:           10000  ← Render กำหนดให้ใช้ port นี้สำหรับ Docker service
```

> ⚠️ **PORT บน Render = 10000** เสมอ ไม่ใช่ 3001 — ต้องตั้งค่า `PORT=10000` ใน Environment Variables บน Render Dashboard ด้วย

#### Frontend บน Vercel

```
Root Directory: frontend
Framework:      Vite
Build Command:  npm run build
```

---

### Environment Variables Table

**✏️ กรอก URL จริงที่ได้หลัง Deploy (ใช้สำหรับตั้งค่าใน Render และ Vercel)**

| Variable | Service | ค่าที่ตั้งจริงบน Cloud |
|----------|---------|----------------------|
| `PORT` | Backend (Render) | `10000` |
| `DATABASE_URL` | Backend (Render) |postgresql://exam-68030273_owner:npg_HnDV7MECRd5v@ep-nameless-feather-aoq62l8o-pooler.c-2.ap-southeast-1.aws.neon.tech/exam-68030273?sslmode=require&channel_binding=require |
| `JWT_SECRET` | Backend (Render) | (ตั้งค่าแล้ว — ไม่ระบุ) |
| `CORS_ORIGIN` | Backend (Render) | `https://restaurant-management-system-exam-2-sand.vercel.app` |
| `NODE_ENV` | Backend (Render) | `production` |
| `VITE_API_URL` | Frontend (Vercel) | `https://rms-backend-68030273.onrender.com/api` |

---

### Smoke Test Results
> ส่วนที่ 5.4 — ทดสอบ 4 Feature หลักบน Production

**✏️ ทดสอบบน Production URL จริง แล้วกรอกผลและแนบภาพหลักฐาน**

| # | Feature | ขั้นตอนทดสอบ | ผลลัพธ์ที่คาดหวัง | ผ่าน/ไม่ผ่าน |
|---|---------|------------|-----------------|-------------|
| 1 | Health Check | GET `/api/health` | `{"status":"ok"}` | ✅ |
| 2 | Login | Login ด้วย admin บน Frontend URL | เข้าระบบสำเร็จ | ✅ |
| 3 | Open Order & Add Item | เปิดโต๊ะ → เพิ่มสินค้า → Confirm | ออเดอร์ถูกบันทึก | ✅ |
| 4 | Payment | ชำระเงิน → ตรวจสอบ change | คำนวณเงินทอนถูกต้อง | ✅ |

**✏️ Production Smoke Test ผ่าน:** 4 / 4 รายการ

**รูปที่ 12 — Smoke Test Feature 1: Health Check**

`![Smoke Test Health](./tests/reports/smoke-1-health.png)`
![alt text](image-17.png)
**รูปที่ 13 — Smoke Test Feature 2: Login**
![alt text](image-18.png)
`![Smoke Test Login](./tests/reports/smoke-2-login.png)`

**รูปที่ 14 — Smoke Test Feature 3: Open Order**

`![Smoke Test Order](./tests/reports/smoke-3-order.png)`
![alt text](image-19.png)
**รูปที่ 15 — Smoke Test Feature 4: Payment**

`![Smoke Test Payment](./tests/reports/smoke-4-payment.png)`
![alt text](image-20.png)
---

## CI/CD Pipeline + Newman Pass Rate

> ส่วนที่ 5.5

### สิ่งที่แก้ไขใน `.github/workflows/cicd.yml`

**✏️ ทำเครื่องหมาย ✅ เมื่อแก้ไขและทดสอบ Pipeline สำเร็จแล้ว**

- [✅ ] เพิ่ม trigger เมื่อมีการ push ไปที่สาขาหลัก (`main` / `master`)
- [✅ ] เพิ่ม `actions/setup-node` สำหรับ Node.js version 22
- [ ✅] เพิ่ม step รัน Unit Test ของ Backend (`npm test`)
- [✅ ] เพิ่ม step ติดตั้งและรัน Newman
- [✅ ] เพิ่ม step `npm audit --audit-level=high` ทั้ง backend และ frontend

### Newman Pass Rate จาก CI/CD Pipeline

**✏️ กรอกตัวเลขจาก GitHub Actions log หลัง Pipeline รันสำเร็จ**

| Metric | ค่าจริง |
|--------|--------|
| Total Tests |26 |
| Tests Passed |22 |
| Tests Failed |4 |
| **Pass Rate** | 84.62%** |

**รูปที่ 16 — GitHub Actions Pipeline สำเร็จ (แสดง Newman Pass Rate ใน log)**

`![CI/CD Pipeline](./tests/reports/cicd-pipeline-success.png)`
![alt text](image-21.png)
---

*Template สร้างจากข้อสอบปฏิบัติการทดสอบและติดตั้งระบบซอฟต์แวร์เชิงธุรกิจ — PRIME-BSD Model*