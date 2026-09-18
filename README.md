# คู่มือการติดตั้ง OWLGrEd

OWLGrEd คือโปรแกรมแก้ไข OWL Ontology แบบกราฟิก ที่สร้างบนพื้นฐานของตัวแก้ไขไดอะแกรมสไตล์ UML

## ความต้องการของระบบ

- ระบบปฏิบัติการ Windows
- Java Runtime Environment (JRE) — มี JRE แบบ bundled อยู่ใน `OWLGrEd-1.6.11/Bin/jre/` แล้ว

## การติดตั้ง

OWLGrEd เป็นโปรแกรมแบบ portable ไม่ต้องติดตั้ง

1. ไปที่ [https://owlgred.lumii.lv](https://owlgred.lumii.lv) แล้วดาวน์โหลดเวอร์ชันล่าสุด
2. แตกไฟล์ (unzip) ไฟล์ `.zip` ที่ดาวน์โหลดมาไปยังตำแหน่งที่ต้องการ
3. เข้าไปในโฟลเดอร์ `OWLGrEd-1.6.11`
4. ดับเบิลคลิกที่ `owlgred.exe` เพื่อเปิดโปรแกรม

## โครงสร้างโฟลเดอร์

```
OWLGrEd-1.6.11/
├── owlgred.exe          # ไฟล์โปรแกรมหลัก
├── Bin/                 # ไฟล์ไบนารี, DLL และ JRE แบบ bundled
├── AvailablePlugins/    # ปลั๊กอินเสริม (เช่น RDB2OWL, UML_Plus)
├── Projects/            # โปรเจกต์ OWLGrEd ที่บันทึกไว้
├── sample ontologies/   # ไฟล์ OWL ตัวอย่าง (เช่น pizza.owl)
└── Tools/               # เครื่องมือเพิ่มเติม
```

## การเปิด Ontology ตัวอย่าง

1. เปิด OWLGrEd (`owlgred.exe`)
2. ไปที่ **File > Open**
3. เลือกไปที่ `OWLGrEd-1.6.11/sample ontologies/` แล้วเปิดไฟล์ `pizza.owl`

## ปลั๊กอิน

ปลั๊กอินเพิ่มเติมอยู่ในโฟลเดอร์ `AvailablePlugins/`:

| ปลั๊กอิน | คำอธิบาย |
|---|---|
| RDB2OWL | แมปฐานข้อมูลเชิงสัมพันธ์ไปยัง OWL Ontology |
| UML_Plus | รองรับไดอะแกรม UML แบบขยาย |
| OWLGrEd_Schema | แก้ไข Ontology แบบ Schema-based |
| RefactoringServices | เครื่องมือ Refactoring สำหรับ Ontology |

ในการเปิดใช้งานปลั๊กอิน ให้เปิด OWLGrEd แล้วไปที่ **Plugins > Manage Plugins**

## แหล่งข้อมูลอย่างเป็นทางการ

- เว็บไซต์: [http://owlgred.lumii.lv](http://owlgred.lumii.lv)
- เอกสาร: [http://owlgred.lumii.lv/documentation](http://owlgred.lumii.lv/documentation)
