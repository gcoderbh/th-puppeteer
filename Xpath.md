# XPath ฟีเจอร์ทั้งหมด

### **1. XPath ไวยากรณ์**
   - **เส้นทางสัมบูรณ์:** เริ่มจากโหนดราก
     - ตัวอย่าง: `/html/body/div`
   - **เส้นทางสัมพันธ์:** เริ่มจากโหนดปัจจุบัน
     - ตัวอย่าง: `div/span`

### **2. การเลือกโหนด**
   - **โหนดองค์ประกอบ:** เลือกทุกโหนดที่มีชื่อที่ระบุ
     - ตัวอย่าง: `//div` เลือกทุกองค์ประกอบ `<div>`
   - **โหนดแอตทริบิวต์:** เลือกแอตทริบิวต์ของโหนด
     - ตัวอย่าง: `//div[@id]` เลือกทุกองค์ประกอบ `<div>` ที่มีแอตทริบิวต์ `id`
   - **โหนดข้อความ:** เลือกเนื้อหาข้อความของโหนด
     - ตัวอย่าง: `//div/text()`
   - **โหนดเนมสเปซ:** เลือกโหนดที่มีเนมสเปซเฉพาะ
     - ตัวอย่าง: `//*:name` เลือกโหนดที่มีชื่อเฉพาะในเนมสเปซใด ๆ

### **3. แกน**
   - **child::** เลือกลูกของโหนดปัจจุบัน
     - ตัวอย่าง: `child::div`
   - **parent::** เลือกพ่อแม่ของโหนดปัจจุบัน
     - ตัวอย่าง: `parent::node()`
   - **ancestor::** เลือกบรรพบุรุษทั้งหมด (พ่อแม่, ปู่ย่าตายาย, ฯลฯ) ของโหนดปัจจุบัน
     - ตัวอย่าง: `ancestor::div`
   - **descendant::** เลือกลูกหลานทั้งหมด (ลูก, หลาน, ฯลฯ) ของโหนดปัจจุบัน
     - ตัวอย่าง: `descendant::span`
   - **following::** เลือกทุกสิ่งในเอกสารหลังจากแท็กปิดของโหนดปัจจุบัน
     - ตัวอย่าง: `following::div`
   - **preceding::** เลือกทุกโหนดที่ปรากฏก่อนโหนดปัจจุบันในเอกสาร
     - ตัวอย่าง: `preceding::div`
   - **self::** เลือกโหนดปัจจุบัน
     - ตัวอย่าง: `self::node()`
   - **descendant-or-self::** เลือกโหนดปัจจุบันและลูกหลานทั้งหมด
     - ตัวอย่าง: `descendant-or-self::div`
   - **ancestor-or-self::** เลือกโหนดปัจจุบันและบรรพบุรุษทั้งหมด
     - ตัวอย่าง: `ancestor-or-self::div`

### **4. เงื่อนไข (Predicates)**
   - **ค่าแอตทริบิวต์:** เลือกโหนดที่มีค่าแอตทริบิวต์เฉพาะ
     - ตัวอย่าง: `//div[@id='main']`
   - **ตำแหน่ง:** เลือกโหนดตามตำแหน่ง
     - ตัวอย่าง: `//div[1]` เลือกองค์ประกอบ `<div>` แรก
   - **Contains:** เลือกโหนดที่มีข้อความเฉพาะ
     - ตัวอย่าง: `//div[contains(text(), 'example')]`
   - **Starts-with:** เลือกโหนดที่ค่าแอตทริบิวต์เริ่มต้นด้วยข้อความเฉพาะ
     - ตัวอย่าง: `//div[starts-with(@class, 'header')]`

### **5. ฟังก์ชัน (Functions)**
   - **last()**: เลือกโหนดสุดท้าย
     - ตัวอย่าง: `//div[last()]`
   - **position()**: เลือกโหนดตามตำแหน่งของมัน
     - ตัวอย่าง: `//div[position()<3]` เลือกสององค์ประกอบ `<div>` แรก
   - **count()**: นับจำนวนโหนด
     - ตัวอย่าง: `count(//div)`
   - **local-name()**: เลือกโหนดตามชื่อท้องถิ่น
     - ตัวอย่าง: `//*[local-name()='div']`
   - **namespace-uri()**: เลือกโหนดตาม URI ของเนมสเปซ
     - ตัวอย่าง: `//*[namespace-uri()='http://example.com']`
   - **name()**: เลือกโหนดตามชื่อ
     - ตัวอย่าง: `//*[name()='div']`

### **6. ตัวดำเนินการเชิงบูลีน (Boolean Operators)**
   - **and:** รวมสองเงื่อนไขและคืนค่าจริงถ้าทั้งสองเป็นจริง
     - ตัวอย่าง: `//div[@id='main' and @class='content']`
   - **or:** รวมสองเงื่อนไขและคืนค่าจริงถ้าเงื่อนไขใดเป็นจริง
     - ตัวอย่าง: `//div[@id='main' or @class='content']`
   - **not():** ปฏิเสธเงื่อนไข
     - ตัวอย่าง: `//div[not(@class='content')]`

### **7. อักขระตัวแทน (Wildcards)**
   - **Node Wildcard:** เลือกโหนดใด ๆ
     - ตัวอย่าง: `//*`
   - **Attribute Wildcard:** เลือกแอตทริบิวต์ใด ๆ
     - ตัวอย่าง: `//@*`

### **8. ตัวดำเนินการ XPath (XPath Operators)**
   - **| (Union):** รวมผลลัพธ์จากสองนิพจน์ XPath
     - ตัวอย่าง: `//div | //span`
   - **+ (Addition):** เพิ่มค่าตัวเลข
     - ตัวอย่าง: `5 + 2`
   - **- (Subtraction):** ลบค่าตัวเลข
     - ตัวอย่าง: `5 - 2`
   - *** (Multiplication):** คูณค่าตัวเลข
     - ตัวอย่าง: `5 * 2`
   - **div (Division):** หารค่าตัวเลข
     - ตัวอย่าง: `5 div 2`
   - **mod (Modulus):** คืนค่าที่เหลือจากการหาร
     - ตัวอย่าง: `5 mod 2`