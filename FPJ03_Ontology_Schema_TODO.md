# TODO — FPJ03 Ontology Schema Design

## 🔴 Phase 1 — เกลา Class ให้จบก่อน

- [ ] ทบทวน Domain / Scope ว่าเราจะครอบคลุมอะไร
- [ ] ทบทวน `AIResearchWork` ว่าเป็น Class หลักเหมาะสมหรือไม่
- [ ] ไล่ Class ทีละตัวว่า "จำเป็นจริงไหม?"
- [ ] ตัด Class ที่เป็น Metadata เกินความจำเป็น
- [ ] ตรวจว่าอะไรควรเป็น Class / Subclass / Instance
- [ ] ตรวจ `is-a` ว่า Subclass ทุกตัวเป็น "ประเภทหนึ่งของ" Parent จริง
- [ ] ทำ Class Hierarchy ฉบับสุดท้าย
- [ ] เขียนคำอธิบายภาษาไทยให้ทุก Class

## 🟠 Phase 2 — วาง Object Properties

หลัง Class นิ่งแล้วค่อยคิดว่า **"Class ไหนสัมพันธ์กับ Class ไหน?"**

- [ ] ลิสต์ความสัมพันธ์จาก `AIResearchWork`
- [ ] หา ObjectProperty ที่จำเป็น
- [ ] กำหนด Domain
- [ ] กำหนด Range
- [ ] ตรวจชื่อให้เป็น camelCase
- [ ] ตรวจว่าความสัมพันธ์ไหนซ้ำกัน
- [ ] พิจารณา Inverse Property ที่มีประโยชน์
- [ ] วาด Graph ความสัมพันธ์
- [ ] เลือก ObjectProperty ที่สามารถนำไปทำ Reasoning ได้

ตัวหลักที่เรามีตอนนี้ (**ยังไม่ถือว่าเป็น final**):

```
AIResearchWork
 ├── createdBy
 ├── hasTopic
 ├── usesModel
 ├── usesMethod
 ├── usesDataset
 └── evaluatedBy
```

## 🟡 Phase 3 — วาง Data Properties

คำถามหลักคือ **"แต่ละ Class ต้องเก็บข้อมูลอะไรที่เป็นค่าข้อมูลจริง?"**

- [ ] ลิสต์ข้อมูลที่จำเป็นของแต่ละ Class
- [ ] แยกว่าอะไรควรเป็น DataProperty
- [ ] กำหนด Domain
- [ ] กำหนด Range เช่น `xsd:string`, `xsd:gYear`
- [ ] ตรวจว่าข้อมูลบางอย่างควรเป็น ObjectProperty แทนหรือไม่
- [ ] หลีกเลี่ยง DataProperty ที่เป็นแค่ข้อมูลซ้ำกับ Instance/Relationship

ตัวอย่าง:

```
AIResearchWork
 ├── workTitle
 ├── publicationYear
 └── abstract

Researcher
 └── researcherName

Dataset
 └── datasetName
```

## 🟢 Phase 4 — ออกแบบ Instances

อันนี้สำคัญมาก เพราะจะเป็นตัวทดสอบว่า Schema เรา **ใช้ได้จริงหรือเปล่า**

- [ ] เลือกงานวิจัยตัวอย่าง 2–3 งาน
- [ ] สร้าง Researcher
- [ ] สร้าง ResearchTopic
- [ ] สร้าง AIModel
- [ ] สร้าง Method
- [ ] สร้าง Dataset
- [ ] สร้าง Evaluation
- [ ] สร้าง Venue
- [ ] เชื่อมทุก Instance ด้วย ObjectProperty
- [ ] เติม DataProperty
- [ ] ตรวจว่า Instance สามารถสร้างเป็น Graph ที่สมเหตุสมผล

เป้าหมายคือได้ประมาณนี้:

```
ResearchWork_A
 ├── hasTopic → NLP
 ├── usesModel → BERT
 ├── usesMethod → FineTuning
 ├── usesDataset → Dataset_A
 ├── evaluatedBy → Evaluation_A
 └── createdBy → Researcher_A
```

ถ้าตรงนี้ทำไม่ได้ง่าย ๆ → กลับไปแก้ Schema

## 🔵 Phase 5 — OWL / Reasoning

ค่อยทำหลัง Instance ใช้งานได้

- [ ] เลือก OWL Property ที่เหมาะกับ Domain
- [ ] ทำอย่างน้อย 3 รูปแบบ
- [ ] กำหนดข้อจำกัดที่มีเหตุผล
- [ ] ทดลอง Reasoner
- [ ] แยกให้ได้ว่าอะไรคือข้อมูลที่ใส่เอง
- [ ] อะไรคือข้อมูลที่ Reasoner อนุมานเพิ่ม
- [ ] เตรียมตัวอย่าง Before / After Reasoning

## 🟣 Phase 6 — เตรียม SPARQL / Competency Questions

- [ ] กำหนด Competency Questions
- [ ] CQ → ObjectProperty ที่ใช้ตอบ
- [ ] CQ → DataProperty ที่ใช้ Filter
- [ ] ทำ Basic Query
- [ ] ทำ Filter
- [ ] ทำ Multiple Conditions
- [ ] ทำ Object Property Traversal
- [ ] ทำ Query หลัง Reasoning
