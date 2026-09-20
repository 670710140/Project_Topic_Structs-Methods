# Rust Tutorial Project — Principles of Programming Languages

> **สำหรับนักศึกษา:** ใช้ไฟล์นี้เป็น Template สำหรับจัดทำบทเรียน Rust ของกลุ่ม  
> **Topic No.:** `8`
> **Topic Name:** `[Structs & Methods]`
> **Group No.:** `8`

---

## 1. Members

| # | Name | Student ID | GitHub Username | Main Responsibility |
|---|---|---|---|---|
| 1 | `[นายพงศ์ชยุตม์ หัวใจเพ็ชร์]` | `[670710137]` | `@[username]` | Concept + Code |
| 2 | `[นายพชรพล อาจม่วง]` | `[670710138]` | `@[username]` | Code + Demo |
| 3 | `[นายพิชัยพร พลบเนียม]` | `[670710139]` | `@[username]` | Rust vs Other Language + PPL |
| 4 | `[นายภัทรดนัย คนชม]` | `[ุ670710140]` | `@[670710140]` | Exercises + Common Mistakes |

---

## 2. Learning Objectives

หลังจากศึกษา Topic นี้แล้ว ผู้เรียนสามารถ:

1. `[อธิบายแนวคิดสำคัญได้]`
2. `[เขียนโปรแกรม Rust ที่เกี่ยวข้องได้]`
3. `[วิเคราะห์พฤติกรรม/กฎของภาษาได้]`
4. `[เปรียบเทียบ Rust กับภาษาอื่นได้]`

---

## 3. Introduction

อธิบายว่า Topic นี้คืออะไร มีความสำคัญอย่างไร และใช้แก้ปัญหาอะไรในการเขียนโปรแกรม

`[เขียนเนื้อหาที่นี่]`

---

## 4. Key Concepts

### 4.1 `[Concept 1]`

**คำอธิบาย**

`[อธิบายแนวคิด]`

**ตัวอย่าง**

```rust
fn main() {
    println!("Hello, Rust!");
}
```

**Explanation**

`[อธิบายว่า code ทำงานอย่างไร]`

---

### 4.2 `[Concept 2]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.3 `[Concept 3]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.4 `[Concept 4 — ถ้ามี]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.5 `[Concept 5 — ถ้ามี]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

## 5. Important Syntax / Rules

| Syntax / Rule | Meaning | Example |
|---|---|---|
| `[syntax/rule]` | `[ความหมาย]` | `[ตัวอย่าง]` |
| `[syntax/rule]` | `[ความหมาย]` | `[ตัวอย่าง]` |
| `[syntax/rule]` | `[ความหมาย]` | `[ตัวอย่าง]` |

### Important Rules

1. `[กฎสำคัญข้อที่ 1]`
2. `[กฎสำคัญข้อที่ 2]`
3. `[กฎสำคัญข้อที่ 3]`

---

## 6. Runnable Code Examples

> **ข้อกำหนด:** Code ทุกตัวต้อง Compile และ Run ได้จริงก่อนนำมาใส่ในเอกสาร

### Example 1 — `[ชื่อ Example]`

**Purpose:** `[ต้องการสาธิตอะไร]`

```rust
fn main() {
    // Write your runnable Rust code here
}
```

**Expected Output**

```text
[expected output]
```

**Explanation**

`[อธิบาย code ทีละส่วนที่สำคัญ]`

---

### Example 2 — `[ชื่อ Example]`

**Purpose:** `[ต้องการสาธิตอะไร]`

```rust
fn main() {
    // Write your runnable Rust code here
}
```

**Expected Output**

```text
[expected output]
```

**Explanation**

`[อธิบาย code]`

---

## 7. Common Mistakes

### Mistake 1 — `[ลืม &self ใน Method]`

**Problem**

`[อธิบายปัญหา]`
สร้าง Method ที่ต้องการเข้าถึงข้อมูลของ Struct แต่ไม่ได้ใส่ &self

**Incorrect Code**

```rust
struct Student {
    name: String,
    age: i32,
}
    impl Student {
        fn show_info(!!!!) {
            println!("ชื่อ: {}", self.name);
            println!("อายุ: {}", self.age);
        }
    }
```

**Correct Code**

```rust
struct Student {
    name: String,
    age: i32,
}
    impl Student {
        fn show_info(&self) {
            println!("ชื่อ: {}", self.name);
            println!("อายุ: {}", self.age);
        }
    }
```

**Why?**

`[อธิบายสาเหตุ]`
self หมายถึง ข้อมูลของ Struct ตัวที่กำลังเรียก Method
เมื่อเราเขียน:

student.show_info();

Rust จะส่ง student เข้ามาให้ Method ผ่าน self

ดังนั้นถ้าต้องการใช้:

self.name
self.age

เราต้องประกาศ:

fn show_info(&self)

&self หมายถึง Method สามารถ อ่านข้อมูลของ Struct ได้ โดยไม่ต้องเป็นเจ้าของข้อมูล

---

### Mistake 2 — `[ลืม mut เมื่อ Method แก้ไขข้อมูล]`

**Problem**

`[อธิบายปัญหา]`
สร้าง Method ที่ต้องการเปลี่ยนแปลงข้อมูลภายใน Struct แต่ไม่ได้ใช้ &mut self หรือไม่ได้ประกาศตัวแปรด้วย mut

**Incorrect Code**

```rust
struct Student {
    name: String,
    age: i32,
}
impl Student {
    fn birthday(&mut self) {
        self.age += 1;
    }
}
fn main() {
    let student = Student { //ไม่มี mut บอกว่า Method นี้ต้องการแก้ไขข้อมูลของ student
        name: "John".to_string(),
        age: 20,
    };
student.birthday(); }
```

**Correct Code**

```rust
struct Student {
    name: String,
    age: i32,
}
impl Student {
    fn birthday(&mut self) {
        self.age += 1;
    }
}
fn main() {
    let mut student = Student { //มี mut อนุญาตให้ student ถูกแก้ไข
        name: "John".to_string(),
        age: 20,
    };
student.birthday(); }
```

**Why?**

`[อธิบายสาเหตุ]`
ถ้า Method ต้องการ แก้ไขข้อมูลของ Struct ต้องใช้ &mut self

fn birthday(&mut self)

และตัวแปรที่นำไปเรียก Method ก็ต้องประกาศด้วย mut

let mut student = Student { ... };

จำง่าย ๆ:

อ่านข้อมูล
&self

แก้ไขข้อมูล
&mut self
+
mut ตัวแปร
---

## 8. Exercises

> จัดทำแบบฝึกหัด **2 ข้อ** ที่สอดคล้องกับ Topic และมีระดับความยากเหมาะสม

### Exercise 1 — `[เก็บข้อมูลนักเรียน]`

**Problem**

`[เขียนโจทย์]`
`[ให้สร้าง struct Student สำหรับเก็บข้อมูลนักเรียน โดยมีข้อมูลดังนี้

    - ชื่อ (name) เป็น String
    - อายุ (age) เป็น i32

จากนั้นสร้าง Method ชื่อ show_info() เพื่อแสดงข้อมูลของนักเรียน]`

ผลลัพธ์ที่ต้องการ:
    ชื่อ: John
    อายุ: 20

**Hint**

`[คำใบ้]`
- ใช้ struct Student
- สร้าง Method ภายใน impl Student
- Method show_info() ให้ใช้ &self
- ใน main() ให้สร้าง Student 1 คน แล้วเรียกใช้ show_info()

**Solution**

```rust
struct Student {
    name: String,
    age: i32,
}
impl Student {
    fn show_info(&self) {
        println!("ชื่อ: {}", self.name);
        println!("อายุ: {}", self.age);
    }
}
fn main() {
    let student = Student {
        name: "John".to_string(),
        age: 20,
    };
    student.show_info();
}
```

**Explanation**

`[อธิบายแนวทางแก้]`
สร้าง struct Student เพื่อเก็บข้อมูลของนักเรียน:

struct Student {
    name: String,
    age: i32,
}

จากนั้นใช้ impl Student เพื่อสร้าง Method ให้กับ Student

impl Student {
    fn show_info(&self) {
        // ...
    }
}

&self ใช้สำหรับให้ Method เข้าถึงข้อมูลของ Student ตัวที่เรียก Method

เช่น:

self.name
self.age

ใน main() สร้าง Student:

let student = Student {
    name: String::from("John"),
    age: 20,
};

แล้วเรียก Method:

student.show_info();

---

### Exercise 2 — `[ข้อมูลหนังสือ]`

**Problem**

`[เขียนโจทย์]`
ให้สร้าง struct Book สำหรับเก็บข้อมูลหนังสือ โดยมีข้อมูลดังนี้

    title เป็น String
    author เป็น String
    price เป็น f64

จากนั้นสร้าง Method ชื่อ show_info() เพื่อแสดงข้อมูลหนังสือ

ผลลัพธ์ที่ต้องการ:

ชื่อหนังสือ: Rust Programming
ผู้เขียน: John
ราคา: 599

**Hint**

`[คำใบ้]`
- ใช้ struct Book
- สร้าง Method ภายใน impl Book
- Method show_info() ให้ใช้ &self
- ใช้ println!() เพื่อแสดงข้อมูล
- ใน main() ให้สร้างหนังสือ 1 เล่ม แล้วเรียก show_info()

**Solution**

```rust
struct Book {
    title: String,
    author: String,
    price: f64,
    }
impl Book {
    fn show_info(&self) {
        println!("ชื่อหนังสือ: {}", self.title);
        println!("ผู้เขียน: {}", self.author);
        println!("ราคา: {}", self.price);
        }
}
fn main() {
    let book = Book {
        title: "Rust Programming".to_string(),
        author: "John".to_string(),
        price: 599.0,
        };
    book.show_info();
}
```

**Explanation**

`[อธิบายแนวทางแก้]`
สร้าง struct Book เพื่อเก็บข้อมูล 3 อย่าง:

struct Book {
    title: String,
    author: String,
    price: f64,
}

จากนั้นใช้ impl Book เพื่อสร้าง Method:

impl Book {
    fn show_info(&self) {
        // ...
    }
}

&self ทำให้ Method สามารถอ่านข้อมูลของ book ได้ เช่น:

self.title
self.author
self.price

ใน main() สร้างหนังสือ:

let book = Book {
    title: "Rust Programming".to_string(),
    author: "John".to_string(),
    price: 599.0,
};

แล้วเรียก Method:

book.show_info();

ผลลัพธ์:

ชื่อหนังสือ: Rust Programming
ผู้เขียน: John
ราคา: 599
---

## 9. PPL Perspective

> **ส่วนนี้เป็นหัวใจของรายวิชา Principles of Programming Languages**

วิเคราะห์ Topic นี้ในมุมมองของ Programming Languages

### 9.1 Syntax

`[Topic นี้เกี่ยวข้องกับ syntax อย่างไร]`

### 9.2 Semantics

`[คำสั่ง/construct เหล่านี้มีความหมายหรือพฤติกรรมอย่างไร]`

### 9.3 Type System

`[เกี่ยวข้องกับ type system อย่างไร ถ้ามี]`

### 9.4 Memory / Resource Management

`[เกี่ยวข้องกับ memory หรือ resource management อย่างไร ถ้ามี]`

### 9.5 Abstraction / Other PPL Concepts

`[อธิบาย abstraction, scope, binding, paradigm หรือแนวคิด PPL อื่นที่เกี่ยวข้อง]`

### 9.6 Why Rust?

`[Rust ใช้แนวคิดนี้เพื่อเพิ่ม safety, reliability หรือ performance อย่างไร]`

---

## 10. Rust vs. Other Language

**Comparison Language:** `[Python / C / C++ / Java / Kotlin / ...]`

| Aspect | Rust | Other Language |
|---|---|---|
| Syntax | `[อธิบาย]` | `[อธิบาย]` |
| Semantics / Behavior | `[อธิบาย]` | `[อธิบาย]` |
| Type System | `[อธิบาย]` | `[อธิบาย]` |
| Memory Management | `[อธิบาย]` | `[อธิบาย]` |
| Safety | `[อธิบาย]` | `[อธิบาย]` |

### Rust Example

```rust
// Rust code
```

### `[Other Language]` Example

```python
# Other language code
```

### Analysis

`[อธิบายความแตกต่างที่สำคัญ และเหตุผลด้านการออกแบบภาษา]`

---

## 11. Teach Your Topic

การนำเสนอมีสมาชิก **4 คน คนละประมาณ 5 นาที**

| Member | Responsibility | Time |
|---|---|---:|
| Member 1 | Concept + Short Code Illustration | 5 min |
| Member 2 | Detailed Code + Live Demo | 5 min |
| Member 3 | Rust vs Other Language + PPL Analysis | 5 min |
| Member 4 | Exercises + Common Mistakes + Challenge | 5 min |

### Individual Contribution

**Member 1**

`[สิ่งที่รับผิดชอบ]`

**Member 2**

`[สิ่งที่รับผิดชอบ]`

**Member 3**

`[สิ่งที่รับผิดชอบ]`

**Member 4**

`[สิ่งที่รับผิดชอบ]`

> สมาชิกทุกคนต้องสามารถอธิบาย Code ของกลุ่มได้ ไม่ใช่เฉพาะส่วนที่ตนเองเขียน

---

## 12. References

> แนะนำให้มีอย่างน้อย **4 แหล่งอ้างอิง** และควรใช้เอกสารทางการเป็นหลัก

1. `[The Rust Programming Language — Rust Book]`
2. `[Rust by Example / Rust Reference]`
3. `[Official documentation ที่เกี่ยวข้องกับ Topic]`
4. `[แหล่งอ้างอิงเพิ่มเติม]`

---

## 13. AI Usage Declaration

สามารถใช้ AI เป็นเครื่องมือช่วยเรียนรู้และพัฒนาได้ แต่สมาชิกทุกคนต้องเข้าใจและสามารถอธิบายผลงานของกลุ่มได้

| AI Tool | Purpose | How the Result Was Verified |
|---|---|---|
| `[เช่น ChatGPT]` | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]` |
| `[AI tool]` | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]` |

### Declaration

- [ ] Code ทุกส่วนที่นำเสนอได้รับการ Compile และทดสอบแล้ว
- [ ] สมาชิกทุกคนสามารถอธิบาย Code ที่นำเสนอได้
- [ ] ตรวจสอบข้อมูลจากแหล่งอ้างอิงที่น่าเชื่อถือแล้ว
- [ ] ระบุการใช้ AI อย่างโปร่งใส

**รายละเอียดการใช้ AI**

`[อธิบายว่าใช้ AI ในขั้นตอนใด และสมาชิกตรวจสอบผลลัพธ์อย่างไร]`

---

## 14. GitHub Contribution

| Member | Issues | Commits | Pull Requests | Code Reviews | Contribution |
|---|---:|---:|---:|---:|---|
| Member 1 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 2 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 3 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 4 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |

### Teamwork Reflection

**How did your team collaborate?**

`[อธิบายกระบวนการทำงานร่วมกัน]`

**Problems encountered**

`[ปัญหาที่พบ]`

**How did you solve them?**

`[วิธีแก้ปัญหา]`

---

## 15. Final Checklist

- [ ] Learning Objectives ครบ 3–4 ข้อ
- [ ] Key Concepts ครบถ้วน
- [ ] Syntax / Rules
- [ ] Runnable Code Examples
- [ ] Code Compile และ Run ได้จริง
- [ ] Common Mistakes
- [ ] Exercises 2 ข้อ พร้อม Solutions
- [ ] PPL Perspective
- [ ] Rust vs Other Language
- [ ] References อย่างน้อย 4 แหล่ง
- [ ] AI Usage Declaration
- [ ] GitHub Contribution
- [ ] สมาชิกทั้ง 4 คนมีส่วนร่วม
- [ ] สมาชิกทั้ง 4 คนพร้อมนำเสนอคนละ 5 นาที
- [ ] สมาชิกทุกคนสามารถอธิบาย Code ของกลุ่มได้

---

## Submission Information

**Repository:** `[GitHub repository URL]`

**Chapter Path:** `[เช่น chapters/01-introduction/]`

**Final PR:** `#[PR number]`

**Submitted by:** `[Group XX]`

**Date:** `[YYYY-MM-DD]`
