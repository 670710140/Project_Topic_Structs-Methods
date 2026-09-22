# Rust Tutorial Project — Principles of Programming Languages

> **สำหรับนักศึกษา:** ใช้ไฟล์นี้เป็น Template สำหรับจัดทำบทเรียน Rust ของกลุ่ม  
> **Topic No.:** `8`
> **Topic Name:** `[Structs & Methods]`
> **Group No.:** `8`

---

## 1. Members

| #   | Name                    | Student ID    | GitHub Username | Main Responsibility          |
| --- | ----------------------- | ------------- | --------------- | ---------------------------- |
| 1   | `[นายพงศ์ชยุตม์ หัวใจเพ็ชร์]` | `[670710137]` | `@[username]`   | Concept + Code               |
| 2   | `[นายพชรพล อาจม่วง]`     | `[670710138]` | `@[670710138]`  | Code + Demo                  |
| 3   | `[นายพิชัยพร พลบเนียม]`    | `[670710139]` | `@[username]`   | Rust vs Other Language + PPL |
| 4   | `[นายภัทรดนัย คนชม]`      | `[ุ670710140]` | `@[670710140]`  | Exercises + Common Mistakes  |

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

| Syntax / Rule   | Meaning      | Example    |
| --------------- | ------------ | ---------- |
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

### Example 1 — `[ชื่อ การสร้าง Struct และการเรียกระหว่าง Associated Function กับ Methods]`

**Purpose:** `[สาธิตการประกาศ Struct, การสร้าง Associated Function (new), การใช้ Method อ่าน/แก้ไขข้อมูล (&self, &mut self), และการใช้ Method ที่ย้าย Ownership (self)]`

```rust
#[derive(Debug)]
struct UserAccount {
    username: String,
    balance: f64,
    active: bool,
}

impl UserAccount {
    fn new(username: &str, initial_balance: f64) -> Self {
        Self {
            username: username.to_string(),
            balance: initial_balance,
            active: true,
        }
    }

    fn get_balance(&self) -> f64 {
        self.balance
    }

    fn deposit(&mut self, amount: f64) {
        if amount > 0.0 {
            self.balance += amount;
            println!("ฝากเงินสำเร็จ: +${:.2} | ยอดคงเหลือปัจจุบัน: ${:.2}", amount, self.balance);
        } else {
            println!("จำนวนเงินฝากต้องมากกว่า 0");
        }
    }

    fn withdraw(&mut self, amount: f64) -> Result<f64, String> {
        if amount <= 0.0 {
            Err("จำนวนเงินถอนต้องมากกว่า 0".to_string())
        } else if amount > self.balance {
            Err("ยอดเงินคงเหลือไม่เพียงพอ".to_string())
        } else {
            self.balance -= amount;
            Ok(self.balance)
        }
    }

    fn close_account(self) -> f64 {
        println!("ปิดบัญชีของ {} สำเร็จ คืนเงินคงเหลือ: ${:.2}", self.username, self.balance);
        self.balance
    }
}

fn main() {
    let mut my_account = UserAccount::new("Alice", 100.0);
    println!("เริ่มต้นบัญชี: {:?}", my_account);

    println!("ยอดเงินเริ่มต้น: ${:.2}", my_account.get_balance());

    my_account.deposit(50.0);

    match my_account.withdraw(30.0) {
        Ok(new_balance) => println!("ถอนเงินสำเร็จ ยอดคงเหลือ: ${:.2}", new_balance),
        Err(e) => println!("เกิดข้อผิดพลาด: {}", e),
    }

    let refunded = my_account.close_account();
    println!("เงินคืนเข้ามือ: ${:.2}", refunded);
}
```

**Expected Output**

```text
เริ่มต้นบัญชี: UserAccount { username: "Alice", balance: 100.0, active: true }
ยอดเงินเริ่มต้น: $100.00
ฝากเงินสำเร็จ: +$50.00 | ยอดคงเหลือปัจจุบัน: $150.00
ถอนเงินสำเร็จ ยอดคงเหลือ: $120.00
ปิดบัญชีของ Alice สำเร็จ คืนเงินคงเหลือ: $120.00
เงินคืนเข้ามือ: $120.00
```

**Explanation**

- **`struct UserAccount`**: การนิยามโครงสร้างข้อมูลเพื่อเก็บสเตตของผู้ใช้ ประกอบด้วย `username`, `balance`, และ `active`
- **`#[derive(Debug)]`**: ช่วยให้สามารถพิมพ์ค่าของ Struct ออกมาทางหน้าจอโดยใช้ฟอร์แมต `{:?}` เพื่อการ Debugging ได้สะดวก
- **`impl UserAccount`**: บล็อกสำหรับเขียนฟังก์ชันเฉพาะของ Struct
- **`fn new(...)`**: เป็น **Associated Function** (ไม่ได้รับ `self`) ทำหน้าที่เป็น Constructor เพื่อสร้าง Instance ใหม่ของ Struct
- **`fn get_balance(&self)`**: เป็น **Immutable Method** ยืมอ่านค่าฟิลด์ `balance` โดยไม่มีการเปลี่ยนแปลงข้อมูลภายใน
- **`fn deposit(&mut self, ...)` & `fn withdraw(&mut self, ...)`**: เป็น **Mutable Methods** ยืมสิทธิ์เข้าถึงเพื่อปรับแต่งแก้ไขค่า `balance` ภายใน Struct
- **`fn close_account(self)`**: เป็น **Ownership Consumer Method** โดยรับ `self` ไปตรง ๆ ทำให้ Instance นั้นถูกย้าย Ownership (Move) และย้อนกลับมาใช้งานอีกไม่ได้หลังจบคำสั่ง เพื่อความปลอดภัยด้านหน่วยความจำ

---

### Example 2 — `[ชื่อ การคำนวณพื้นที่และการปรับขนาดรูปทรงสี่เหลี่ยม (Rectangle Structure)]`

**Purpose:** `[สาธิตการใช้ Struct เก็บขนาดวัตถุ, การสร้าง Associated Function (new), การใช้ Method คำนวณค่า (&self), การใช้ Method ปรับเปลี่ยนข้อมูลภายใน (&mut self), และการย้าย Ownership เพื่อคืนค่ากลับ (self)]`

```rust
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn new(width: u32, height: u32) -> Self {
        Self { width, height }
    }

    fn area(&self) -> u32 {
        self.width * self.height
    }

    fn scale(&mut self, factor: u32) {
        self.width *= factor;
        self.height *= factor;
    }

    fn square_up(self) -> Self {
        let max_side = if self.width > self.height {
            self.width
        } else {
            self.height
        };
        Self {
            width: max_side,
            height: max_side,
        }
    }
}

fn main() {
    let mut rect = Rectangle::new(10, 5);
    println!("เริ่มต้นรูปทรง: {:?}", rect);

    println!("พื้นที่รูปทรง: {} ตารางหน่วย", rect.area());

    rect.scale(2);
    println!("หลังขยายสเกล 2 เท่า: {:?}", rect);
    println!("พื้นที่ใหม่: {} ตารางหน่วย", rect.area());

    let square = rect.square_up();
    println!("ปรับรูปทรงเป็นจัตุรัส: {:?}", square);
    println!("พื้นที่จัตุรัส: {} ตารางหน่วย", square.area());
}
```

**Expected Output**

```text
เริ่มต้นรูปทรง: Rectangle { width: 10, height: 5 }
พื้นที่รูปทรง: 50 ตารางหน่วย
หลังขยายสเกล 2 เท่า: Rectangle { width: 20, height: 10 }
พื้นที่ใหม่: 200 ตารางหน่วย
ปรับรูปทรงเป็นจัตุรัส: Rectangle { width: 20, height: 20 }
พื้นที่จัตุรัส: 400 ตารางหน่วย
```

**Explanation**

- **`struct Rectangle`**: การนิยามโครงสร้างข้อมูลสำหรับเก็บขนาดสี่เหลี่ยม โดยมีฟิลด์ width และ height เป็นชนิดข้อมูล u32

- **`#[derive(Debug)]`**: คำสั่งอนุญาตให้แสดงผลข้อมูลใน Struct ออกทางหน้าจอผ่านฟอร์แมต {:?} ได้

- **`impl Rectangle`**: บล็อกสำหรับนิยามการทำงานทั้งหมดของ Struct

- **`fn new(...)`**: เป็น Associated Function ทำหน้าที่เป็น Constructor สำหรับสร้าง Instance ใหม่

- **`fn area(&self)`**: เป็น Immutable Method ดึงค่า width และ height จาก Instance มาคำนวณพื้นที่โดยไม่มีการแก้ไขข้อมูล

- **`fn scale(&mut self, ...)`**: เป็น Mutable Method ทำการปรับเปลี่ยนค่าฟิลด์ภายใน Instance เดิมโดยการคูณขยายขนาด

- **`fn square_up(self)`**: เป็น Ownership Consumer Method รับ self เพื่อทำลาย/แปลง Instance เดิม แล้วส่งคืน Instance ของสี่เหลี่ยมจัตุรัสรูปใหม่กลับไป

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

## 4 มิติหลักที่ Structs & Methods เกี่ยวข้องกับ Type System

Structs & Methods ใน Rust ไม่ได้เป็นเพียงแค่โครงสร้างแบบ OOP ดั้งเดิม แต่ทำงานร่วมกับ Type System ในมิติหลัก ดังนี้:

### 1. การเป็นรากฐานของ Product Type (Data Structuring)

* **Product Type ($A \times B$):** ในทาง Algebraic Data Types (ADTs) ตัว `struct` ทำหน้าที่เป็น Product Type ที่เกิดจากการรวมเซตข้อมูลของแต่ละ Field เข้าด้วยกัน

* **Nominal Typing:** Rust ใช้ระบบ Type แบบระบุชื่อ (Nominal Typing) ในการตรวจ Struct ซึ่งหมายความว่าแม้ Struct 2 ตัวจะมี Field เหมือนกันทุกประการ แต่ Type System จะถือว่าเป็น Type คนละตัวกัน เพื่อป้องกันความผิดพลาดเชิง Semantics

* **Zero-Cost Abstraction:** Struct ใน Rust ทำหน้าที่เพียงกำหนด **Memory Layout** ณ เวลา Compile-time โดยค่าของ Field จะวางเรียงกันใน Memory โดยตรง ไม่มี Class Metadata หรือ Object Header เหมือนภาษาอย่าง Java หรือ Python

### 2. การบังคับใช้กฎ Ownership & Borrowing ผ่าน Receiver (`self`)

Rust แยก Data (`struct`) และ Behavior (`impl`) ออกจากกันอย่างเด็ดขาด โดย Method ไม่ใช่สิ่งพิเศษที่สิงอยู่ใน Object แต่มันคือ **Standalone Function** ที่รับ `self` เป็น Parameter ตัวแรก

ชนิดของ `self` ใน Method Receiver เป็นตัวกำหนดสิทธิ์ใน **Affine Type System** ของ Rust ณ เวลา Compile-time:

| การระบุ `self` ใน Method | ความหมายใน Type System | ผลลัพธ์ด้าน Memory & Safety |
| :--- | :--- | :--- |
| **`fn foo(self)`** | ย้าย **Ownership** (Move) | Struct ถูกทำลายหรือย้ายสิทธิ์ออกไป ตัวแปรเดิมใช้ต่อไม่ได้อีก |
| **`fn foo(&self)`** | ยืมแบบ **Immutable Borrow** | อ่านข้อมูลได้หลายจุดพร้อมกัน (Aliasing) แต่ห้ามแก้ไข |
| **`fn foo(&mut self)`** | ยืมแบบ **Mutable Borrow** | แก้ไขข้อมูลได้ แต่ต้องเป็น Unique Reference เท่านั้น (ห้ามมี Alias อื่น) |

> **PL Insight:** Type Checker จะตรวจสอบสิทธิ์เหล่านี้ ณ เวลา Compile-time ทำให้การันตีเรื่อง **Data Race Freedom** และ **Memory Safety** โดยไม่ต้องใช้ Garbage Collector (GC)

### 3. การเป็นตัวเชื่อม Ad-hoc Polymorphism (Traits)

Rust ไม่ใช้ Inheritance (การสืบทอด Class) ในการทำ Polymorphism แต่ใช้ **Traits** (คล้ายกับ Typeclasses ใน Haskell) ซึ่งแยกการนิยามโครงสร้างข้อมูลกับพฤติกรรมออกจากกัน และควบคุม Dispatching ผ่าน Type System:

* **Static Dispatch (Monomorphization):** เมื่อใช้ Generic Bounds (`T: Trait`) Type System จะสร้างโค้ดเจาะจงตาม Concrete Type ตอนคอมไพล์ ทำให้ไม่มี Runtime Cost

* **Dynamic Dispatch (`dyn Trait`):** เมื่อต้องการ Dynamic Dispatch ณ เวลา Runtime ตัว Type System จะบังคับให้เปลี่ยน Representation ของ Struct เป็น **Fat Pointer** (Pointer ชี้ Data + Pointer ชี้ vtable) ชี้ให้เห็นขอบเขตเรื่อง Memory อย่างชัดเจน

### 4. การรองรับ State Machine ณ ระดับ Type (Type-state Pattern)

การใช้ Generic Struct ร่วมกับ Method ช่วยให้เราสร้าง **Deterministic Finite Automaton (DFA) ณ ระดับ Type System** ได้

```rust
struct Draft;
struct Published;

struct Post<State> {
    state: State,
    content: String,
}

impl Post<Draft> {
    fn publish(self) -> Post<Published> {
        Post {
            state: Published,
            content: self.content,
        }
    }
}
```

* เราสามารถกำหนดให้ Method บางตัวเรียกได้เฉพาะตอนที่ Struct อยู่ใน Type-State ที่ถูกต้องเท่านั้น (เช่น `Post<Draft>` แปลงร่างเป็น `Post<Published>`)

* หากพยายามเรียก Method ผิด State คอมไพเลอร์จะปฏิเสธและแจ้ง Error ทันที ป้องกัน Bug ทาง Logic ได้ตั้งแต่ยังไม่ทันรันโปรแกรม

## ตารางเปรียบเทียบเชิง PL Theory

| ประเด็น | ภาษา OOP ดั้งเดิม (เช่น Java/C++) | ภาษา Rust |
| :--- | :--- | :--- |
| **Data & Behavior** | ผูกติดกันใน Class เดียวกัน | แยก Struct (Data) และ `impl` (Behavior) ออกจากกัน |
| **Abstraction Mechanism** | Inheritance / Subtyping | Composition + Traits (Ad-hoc Polymorphism) |
| **Method Dispatch** | Dynamic Dispatch เป็นค่าเริ่มต้น (Virtual Tables) | Static Dispatch เป็นค่าเริ่มต้น (Monomorphization) |
| **Safety Guarantees** | พึ่งพา Runtime checks / Garbage Collector | พึ่งพา Borrow Checker (Affine Type System) ณ Compile-time |

## บทสรุป

Structs & Methods ใน Rust **ไม่ได้เป็นแค่การเขียนโปรแกรมเชิงวัตถุ (OOP)** แต่เป็นการเอา **โครงสร้างข้อมูล (Product Type)** มาเรียงต่อกับ **กฎสิทธิ์การเข้าถึง memory (Self Borrowing)** และ **อินเทอร์เฟซ (Traits)** เพื่อให้ **Type Checker ตรวจสอบความปลอดภัยทั้งหมดได้จบตั้งแต่ตอน Compile-time**

### 9.4 Memory / Resource Management


## มุมมองทาง Programming Languages (PL) และ Memory / Resource Management

## 1. การจัดวางข้อมูลในหน่วยความจำ (Memory Layout & Allocation)

ในเชิงภาษาระบบ (Systems Programming Language) ตัว Struct ใน Rust เป็นรากฐานของการรวมกลุ่มข้อมูล (Data Aggregation) ซึ่งส่งผลต่อการบริหารจัดการ RAM โดยตรง:

* **Value Semantics (Stack-First Allocation):**
  * Struct ใน Rust เป็น **Value Type** โดยสมบูรณ์ ต่างจากภาษาอย่าง Java หรือ C# ที่ประเภท Class/Object จะถูกบังคับให้จองพื้นที่บน Heap เสมอ
  * เมื่อประกาศ Struct ภายในฟังก์ชัน ข้อมูลทั้งหมดจะถูกจองบน **Stack** โดยตรง ทำให้เข้าถึงข้อมูลได้เร็วระดับ Machine Instruction และถูกป๊อป (Pop) ออกจาก Stack ทันทีที่จบ Scope โดยไม่มี Overhead ของ Garbage Collector (GC)
  * หากต้องการเก็บไว้บน Heap จะต้องระบุผ่าน **Smart Pointers** อย่างชัดเจน เช่น `Box<T>`, `Rc<T>`, หรือ `Arc<T>`

* **Field Reordering Optimization:**
  * ภาษา C จะจัดวาง Field ในหน่วยความจำตามลำดับที่เขียน ทำให้อาจเกิดพื้นที่ว่างเปล่า (**Padding Space**) เพื่อให้ตรงกับ CPU Alignment
  * คอมไพเลอร์ Rust (`rustc`) มีฟีเจอร์ **Dynamic Field Reordering** โดยจะสลับลำดับของ Field ใน Memory ให้อัตโนมัติเพื่อบีบอัด Padding ให้เหลือน้อยที่สุด ช่วยประหยัด RAM และเพิ่มอัตรา CPU Cache Hit Rate (เว้นแต่จะระบุ `#[repr(C)]` เพื่อบังคับแบบภาษา C)

---

## 2. พฤติกรรมของ Method Receiver (`self`) กับระบบ Ownership

จุดเด่นสำคัญของ Rust คือการนำระบบ **Ownership** และ **Borrowing** มาผูกเข้ากับชนิดของ **Method Receiver (`self`)** ทำให้คอมไพเลอร์การันตีความปลอดภัยของ Memory ได้ตั้งแต่ช่วง Compile-Time:

### A. `fn method(self)` — Move Semantics (Ownership Transfer)
* **กลไก Memory:** เกิดการ **Move** สิทธิ์ความเป็นเจ้าของ (Ownership) เข้ามาใน Method
* **การจัดการ Resource:** เมื่อ Method นี้ทำงานจบลง ขอบเขต (Scope) ของ `self` จะสิ้นสุดลง คอมไพเลอร์จะสั่งทำลายและคืน Memory/Resource ทันทีตามหลัก **RAII**
* **PL Safety:** เหมาะกับคำสั่งเปลี่ยนสถานะหรือทำลาย Resource (เช่น `builder.build()` หรือ `socket.close()`) ซึ่งช่วยป้องกันปัญหา **Use-After-Free** หรือการนำออบเจกต์ที่ปิดไปแล้วมาเรียกใช้ซ้ำ เพราะคอมไพเลอร์จะไม่อนุญาตให้ใช้ตัวแปรเดิมอีกต่อไป

### B. `fn method(&self)` — Shared Borrowing
* **กลไก Memory:** ส่งเพียง Pointer (ขนาด 8 bytes บน 64-bit) ชี้ไปยัง Struct เดิมโดยไม่มีการ Copy ข้อมูลขนาดใหญ่
* **PL Safety:** สามารถแชร์การอ่านข้อมูลได้หลายจุดพร้อมกัน แต่**ห้ามแก้ไขข้อมูล**โดยเด็ดขาด คอมไพเลอร์จะตรวจสอบ **Lifetime** เพื่อให้มั่นใจว่า Struct ต้นทางจะไม่ถูก Deallocate ไปก่อนที่ Method จะทำงานเสร็จ (ป้องกันปัญหา **Dangling Pointer**)

### C. `fn method(&mut self)` — Exclusive Borrowing
* **กลไก Memory:** ส่ง Pointer ไปยัง Struct เพื่อทำการแก้ไขข้อมูล
* **PL Safety (Aliasing XOR Mutability):** การันตีว่าขณะที่ Method นี้ทำงาน จะ**ไม่มี Pointer อื่นใดชี้มายัง Struct นี้พร้อมกัน** ช่วยป้องกันปัญหา **Data Race** ในการทำงานแบบภาพขนาน (Concurrency) โดยไม่ต้องใช้ Lock/Mutex ในระดับชั้น Application

---

## 3. การคืน Resource แบบคาดเดาเวลาได้ (RAII & `Drop` Trait)

ภาษา Rust ไม่ใช้ Garbage Collector (GC) แต่ใช้แนวคิด **RAII (Resource Acquisition Is Initialization)** ผ่านระบบ Trait:

* **Automatic & Deterministic Cleanup:**
  เมื่อ Struct หลุดออกนอก Scope คอมไพเลอร์จะแทรกการเรียกโค้ด `Drop::drop(&mut self)` ให้โดยอัตโนมัติ ณ ตำแหน่งนั้นทันที ทำให้คืน Heap Memory, File Descriptors, Database Connections หรือ Network Sockets ได้ตรงเวลา 100%
* **Cascade Dropping:**
  เมื่อ Struct ถูก Drop ตัว Field ย่อยๆ ทั้งหมดภายใน Struct จะถูกเรียก `Drop` เพื่อคืน Resource ต่อกันเป็นทอดๆ (Cascading Destruction) ช่วยป้องกันปัญหา Resource Leak

---

## 4. ประสิทธิภาพการเรียกใช้ Method (Method Dispatch)

ภาษา Rust ยึดหลัก **Zero-Cost Abstraction** ในการเรียกใช้ Method:

1. **Static Dispatch (Monomorphization - Default):**
   * การเรียก Method ปกติบน Struct จะถูกแปลงเป็น **Direct Function Call** ในระดับ Machine Code / Assembly
   * สามารถทำ **Inlining** (เอาโค้ดของ Method มาวางแทนคำสั่งเรียก) ได้ ทำให้ไร้ Overhead ด้านประสิทธิภาพอย่างสิ้นเชิง เท่ากับการเขียน C style Procedural
2. **Dynamic Dispatch (`dyn Trait`):**
   * หากต้องการทำ Polymorphism ภาษา Rust จะบังคับให้ใช้ Pointer ผ่าน **Fat Pointer** (Pointer ชี้ข้อมูล + Pointer ชี้ VTable)
   * ทำให้ต้นทุนเชิงประสิทธิภาพและ Memory ของ VTable ถูกแยกแยะอย่างชัดเจนและควบคุมได้ในชั้น Type System

---

## สรุปเปรียบเทียบเชิงปฏิบัติการ (Summary Matrix)

| ชนิดของ Receiver | พฤติกรรมด้าน Memory | ผลลัพธ์ต่อการจัดการ Resource |
| :--- | :--- | :--- |
| **`self` (Value)** | **Move:** ย้ายสิทธิ์ Ownership / เตรียม Deallocate | ทำลาย Resource ทันทีหลังจบ Method (ป้องกัน *Use-after-free*) |
| **`&self` (Shared Ref)** | **Shared Borrow:** ส่ง Pointer อ่านอย่างเดียว | ไม่ Copy ข้อมูล ป้องกัน *Dangling Pointer* ด้วยระบบ Lifetime |
| **`&mut self` (Exclusive Ref)** | **Exclusive Borrow:** ส่ง Pointer แก้ไขได้ | การันตีไร้ Aliasing ป้องกัน *Data Race* โดยไม่ต้องใช้ Lock |

---


### 9.5 Abstraction / Other PPL Concepts

`[อธิบาย abstraction, scope, binding, paradigm หรือแนวคิด PPL อื่นที่เกี่ยวข้อง]`

Rust มีแนวคิดทาง Programming Language ที่เกี่ยวข้องกับการใช้ Structs และ Methods ดังนี้

Abstraction: struct ใช้สำหรับรวมข้อมูลที่เกี่ยวข้องกันไว้เป็นกลุ่มเดียว และ methods ใช้สำหรับกำหนดการทำงานของข้อมูลนั้น ทำให้ผู้ใช้สามารถเรียกใช้งานผ่านชื่อ Method โดยไม่จำเป็นต้องรู้รายละเอียดภายในทั้งหมด

Scope: ตัวแปรและข้อมูลใน Rust จะสามารถใช้งานได้ภายใน Scope ที่กำหนด เช่น ตัวแปรที่ประกาศภายใน Function จะสามารถใช้งานได้เฉพาะภายใน Function นั้น

Binding: การประกาศตัวแปรใน Rust เป็นการสร้าง Binding ระหว่างชื่อกับค่าหรือข้อมูล เช่น let student = Student { ... } ซึ่งทำให้ชื่อ student อ้างอิงถึงข้อมูลของ Student

Encapsulation: ข้อมูลและการทำงานสามารถรวมอยู่ภายใน struct และ impl ทำให้โปรแกรมมีโครงสร้างและจัดการข้อมูลได้ง่ายขึ้น
Procedural / Imperative Programming: Rust รองรับการเขียนโปรแกรมแบบลำดับขั้น โดยสามารถใช้ตัวแปร เงื่อนไข Loop และ Function เพื่อกำหนดลำดับการทำงานของโปรแกรม

แนวคิดเหล่านี้ช่วยให้การเขียนโปรแกรมด้วย Rust มีโครงสร้างชัดเจน แยกข้อมูลและการทำงานเป็นส่วน ๆ และทำให้สามารถนำกลับมาใช้ซ้ำได้ง่าย
---
### 9.6 Why Rust?

`[Rust ใช้แนวคิดนี้เพื่อเพิ่ม safety, reliability หรือ performance อย่างไร]`

Rust ใช้แนวคิดเรื่อง Safety, Reliability และ Performance เพื่อให้โปรแกรมทำงานได้อย่างปลอดภัยและมีประสิทธิภาพ

Safety: Rust มีระบบตรวจสอบการจัดการหน่วยความจำ เช่น Ownership และ Borrowing ช่วยลดปัญหาที่อาจเกิดขึ้นจากการใช้หน่วยความจำผิดวิธี

Reliability: Rust ตรวจสอบข้อผิดพลาดหลายอย่างตั้งแต่ตอน Compile ทำให้ช่วยลดโอกาสเกิด Bug ขณะโปรแกรมทำงาน

Performance: Rust เป็นภาษาที่ Compile เป็น Machine Code ทำให้โปรแกรมทำงานได้รวดเร็วและใช้ทรัพยากรอย่างมีประสิทธิภาพ โดยไม่ต้องใช้ Garbage Collector

ดังนั้น Rust จึงเหมาะสำหรับการพัฒนาโปรแกรมที่ต้องการทั้ง ความปลอดภัย ความน่าเชื่อถือ และประสิทธิภาพในการทำงาน
---

## 10. Rust vs. Other Language

**Comparison Language:** `[Python / C / C++ / Java / Kotlin / ...]`

| Aspect               | Rust      | Other Language |
| -------------------- | --------- | -------------- |
| Syntax               | `[อธิบาย]` | `[อธิบาย]`      |
| Semantics / Behavior | `[อธิบาย]` | `[อธิบาย]`      |
| Type System          | `[อธิบาย]` | `[อธิบาย]`      |
| Memory Management    | `[อธิบาย]` | `[อธิบาย]`      |
| Safety               | `[อธิบาย]` | `[อธิบาย]`      |

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

| Member   | Responsibility                          |  Time |
| -------- | --------------------------------------- | ----: |
| Member 1 | Concept + Short Code Illustration       | 5 min |
| Member 2 | Detailed Code + Live Demo               | 5 min |
| Member 3 | Rust vs Other Language + PPL Analysis   | 5 min |
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

| AI Tool         | Purpose       | How the Result Was Verified |
| --------------- | ------------- | --------------------------- |
| `[เช่น ChatGPT]` | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]`           |
| `[AI tool]`     | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]`           |

### Declaration

- [ ] Code ทุกส่วนที่นำเสนอได้รับการ Compile และทดสอบแล้ว
- [ ] สมาชิกทุกคนสามารถอธิบาย Code ที่นำเสนอได้
- [ ] ตรวจสอบข้อมูลจากแหล่งอ้างอิงที่น่าเชื่อถือแล้ว
- [ ] ระบุการใช้ AI อย่างโปร่งใส

**รายละเอียดการใช้ AI**

`[อธิบายว่าใช้ AI ในขั้นตอนใด และสมาชิกตรวจสอบผลลัพธ์อย่างไร]`

---

## 14. GitHub Contribution

| Member   |   Issues |  Commits | Pull Requests | Code Reviews | Contribution  |
| -------- | -------: | -------: | ------------: | -----------: | ------------- |
| Member 1 | `[จำนวน]` | `[จำนวน]` |      `[จำนวน]` |     `[จำนวน]` | `[รายละเอียด]` |
| Member 2 | `[จำนวน]` | `[จำนวน]` |      `[จำนวน]` |     `[จำนวน]` | `[รายละเอียด]` |
| Member 3 | `[จำนวน]` | `[จำนวน]` |      `[จำนวน]` |     `[จำนวน]` | `[รายละเอียด]` |
| Member 4 | `[จำนวน]` | `[จำนวน]` |      `[จำนวน]` |     `[จำนวน]` | `[รายละเอียด]` |

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
