# flutter-walkthrough

## รายชื่อของ Extension สำหรับการพัฒนาแอพด้วย Flutter

1. [Flutter](https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter)

## วิธีสร้างโปรเจค Flutter ใน Visual Studio Code

1. เปิดโปรแกรม Visual Studio Code
2. เรียกใช้งาน Command Palette โดยไปที่เมนู **View \> Command Palette**
3. เรียกคำส่ัง **Flutter: New Project**
4. ตั้งชื่อโปรเจคในกล่องข้อความให้เรียบร้อย
5. เลือกโฟลเดอร์ที่จะสร้างโปรเจคเก็บไว้
6. รอจนระบบสร้างโปรเจคจนเสร็จ

## วิธีรันทดสอบแอพพลิเคชั่นจาก Visual Studio Code

1. เลือกโหมด **Debug**
2. จากเมนู Dropdown ที่แสดงว่า **No Configuration** ให้เลือกคำสั่ง **Add Configuration**
3. จะมีการสร้างไฟล์ `launch.json` ซึ่งจะเป็นการตั้งค่าสำหรับโปรเจค Flutter
4. จาก Command Palette ให้ใช้คำสั่ง **Flutter: Select Device** เพื่อเลือกชื่ออุปกรณณ์ที่เชื่อมต่อกับคอมพิวเตอร์ หรือ Simulator ที่ต้องการ
5. กดปุ่ม **Start Debug**

## เริ่มต้นจาก 0 เพื่อเข้าใจแนวคิดของ Flutter

### 1. ล้างโค้ดทั้งหมด

ล้างโค้ดในไฟล์ `lib/main.dart` ทั้งหมด
จากนั้นสร้างเขียนโค้ดใหม่เป็น

```dart
void main() {
	print('hello...');
}
```

### 2. comment test code

เปิดไฟล์ `test/widget_test.dart` และ comment โค้ดทั้งหมดไว้ก่อน

### 3. ทดสอบแอพ

จากนั้นรันทดสอบแอพพลิเคชั่น
สำหรับ Visual Studio Code ให้เปิดดูในส่วนของ Debug Console 
หลังจากกระบวนการทุกอย่างเสร็จสิ้น เราควรจะเห็นข้อความว่า 

```dart
flutter: hello...
```

## เริ่มสร้าง Material App

1. ลบ `print('hello...');` ออกจาก `main()` 
2. เขียนคำสั่ง `import 'package:flutter/material.dart';` เพื่อเรียกใช้คำส่ังที่จำเป็นในการสร้าง Material App
3. ใน `main()` เขียนคำสั่ง `runApp()`

```dart
runApp(MaterialApp(
    title: 'My Flutter'
));
```

เจ้านี่คือตัวโครงแอพพลิเคชั่นของเรา สังเกตผลว่าเกิดอะไรขึ้นถ้าเรารันทดสอบแอพตอนนี้ 

## สร้างหน้าแรกของแอพพลิเคชั่น 

ให้เพิ่มส่วนของ `:home` เข้าไปใน `MeterialApp()`

```dart
runApp(MaterialApp(
    title: 'My Flutter',
    home: Scaffold(
      appBar: AppBar(
        title: Text('OK'),
      ),
      body: Text('hello'),
    ),
  ));
```

จากนั้นให้รันทดสอบแอพพลิเคชั่น 

สังเกตว่า Widget ที่ช่ื่อ `Scaffold()` เป็นโครงหน้าของแอพพลิเคชั่น โดยประกอบไปด้วย Widget ดังนี้
1. `AppBar()` กำหนดให้กับ `appBar:`
2. `Text()` ที่กำหนดให้กับ `body:`

## กำหนด Theme สีให้ App

ให้เพิ่ม `theme:` เข้าไปใน `MaterialApp()` 

```dart
runApp(MaterialApp(
    ...
    theme: ThemeData(
      primarySwatch: Colors.red
    ),
	...
```

รันทดสอบแอพพลิเคชั่น และให้สังเกตการเปลี่ยนแปลงของแอพพลิเคชั่น

Property ชื่อ `theme:` ของ `MaterialApp()` นั้นรับค่า `ThemeData()` ซึ่งเราสามารถกำหนดค่าสีเพื่อใช้งานกับทั้งแอพพลิเคชั่นได้ 

`Colors` เป็นคลาสที่มีค่าสีต่างๆ ให้เราเลือกนั่นเอง

> ลองกำหนดค่าสีใหม่ๆ และทดสอบแอพพลิเคชั่นดู ให้สังเกตการเปลี่ยนแปลงของแอพพลิเคชั่น ตามสีที่กำหนด

จากนั้นทดสอบ ค่า theme อีกแบบหนึ่ง

```dart
runApp(MaterialApp(
    ...
    theme: ThemeData(
      brightness: Brightness.dark
    ),
	...
```

รันทดสอบแอพพลิเคชั่น ให้สังเกตการเปลี่ยนแปลงของแอพพลิเคชั่น 

นี่คือ Dark theme นั่นเอง

## เข้าใจ Stateless และ Stateful Widget

กลไกการทำงานของ Widget ใน Flutter แบ่งออกเป็น 2 พวกใหญ่ๆ นั่นคือ

1. Stateless Widget ที่ไม่จำเป็นต้องถูกเรนเดอร์ใหม่
2. Stateful Widget ที่คาดว่าจะมีการเรนเดอร์ใหม่เรื่อยๆ จากการอัพเดตข้อมูล หรือกลไกต่างๆ 

การเข้าใจวิธีใช้กลุ่ม Widget 2 ประเภทนี้ ก็จะเข้าใจกลไกกว่า 50% ของ Flutter แล้ว
## การสร้าง Page ใหม่

1. สร้างโฟลเดอร์ใหม่ใน `lib/` และตั้งชื่อว่า `pages`
2. สร้างไฟล์ `home_page.dart`
3. เขียนโค้ดสร้าง class `HomePage` โดย extends class ชื่อ `StatelessWidget` 

```dart
import 'package:flutter/material.dart';

class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container();
  }
}
```

4. เปิดไฟล์ `main.dart` และย้ายโค้ดในส่วน `Scaffold()` มาไว้ใน `home_page.dart`

```dart
import 'package:flutter/material.dart';

class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('My App'),
      ),
      body: Text('hello'),
    );
  }
}
```

5. ในไฟล์ `main.dart` เราจึงปรับให้ส่วนของ `body:` เป็นหน้า home page ที่สร้างแยกไว้ได้แทน (ให้สังเกตคำสั่ง import จากไฟล์ `home_page.dart`)

```dart
import 'package:flutter/material.dart';
import 'package:mytest/pages/home_page.dart';

void main() {
  runApp(MaterialApp(
    title: 'My Flutter',
    theme: ThemeData(
      primarySwatch: Colors.blue
    ),
    home: HomePage()
  ));
}   
```

บันทึกไฟล์ และทดสอบแอพพลิเคชั่น สังเกตการเปลี่ยนแปลง

## Action Button

1. เปิดไฟล์ `home_page.dart` 
2. ทำการใส่ widget `RaiseButton()` ลงใน `body:`

```dart
body: RaisedButton(
          onPressed: () {
            
          },
          child: Text('Open Page 2'),
        )
```

สังเกตว่า เราสามารถกำหนดข้อความของปุ่มผ่านทาง `child:` property ด้วย Text widget

สังเกตว่า `onPressed` เป็น event ที่ต้องการ function ในการทำงาน เราสามารถเขียน code ที่ต้องการให้ทำงานเมื่อกดปุ่มได้

เช่นการสั่ง print ข้อความทาง console

```dart
RaisedButton(
  onPressed: () {
     print('Oh key....');
  },
  ...
)
```

## การทำระบบ Navigation

1. สร้างไฟล์ `pages/detail_page.dart`
2. เขียนสร้าง class `DetailPage`

```dart

import 'package:flutter/material.dart';

class DetailPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      child: Scaffold(
        appBar: AppBar(
          title: Text('Page 2'),
        ),
        body: Container()
        )
    );
  }
}
```

3. กลับมาที่ไฟล์ `home_page.dart` ใน `RaiseButton` widget ให้เพิ่มคำสั่ง Navigator ใน event `onPressed`

```dart
onPressed: () {
   Navigator.push(context, MaterialPageRoute(builder: (context) {
     return DetailPage();
   }));
},
```

ทดสอบแอพพลิเคชั่น และสังเกตการเปลี่ยนแปลง
