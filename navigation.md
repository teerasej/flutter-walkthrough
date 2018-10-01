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