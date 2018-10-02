
# Stateless & Stateful



## Stateless Widget

Stateless Widget จะมี method `build` เป็นตัวสร้าง Widget สำหรับนำไปแสดงผล

```dart
class NextflowTraining extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      child: Text('อบรม Google Flutter'),
    );
  }
}
```

## Stateful Widget

Stateful Widget จะมี 2 ส่วน

1. ส่วนของ Class
2. ส่วนของ State

### ส่วนของ State Class

- เราสามารถใช้ method `setState()` เพื่อบอกให้ระบบ Render ตัว Widget ใหม่ได้
- การนำ property มาใช้ใน Widget สามารถทำผ่าน syntax `${property}`

```dart
import 'package:flutter/material.dart';

class HomePage extends StatefulWidget {
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {

  String name;

  void updateName(){
      setState((){
          // update 'name' property here...
      });
  }  



  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: Text('Hello'),
        ),
        body: Column(
          children: <Widget>[
            ...
            Text("${name}")
          ],
        ));
  }
}

```