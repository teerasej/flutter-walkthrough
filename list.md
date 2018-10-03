
# การสร้างและใช้งาน List

## การสร้าง List แบบ static

ListView สามารถรับ `children` widget ได้เหมือนกับ

จากตัวอย่างเราใช้ `ListTile` widget เพื่อใช้ประโยชน์จาก layout ที่เขาสร้างเตรียมไว้แล้ว

```dart
ListView(
  children: <Widget>[
    ListTile(
      leading: Icon(Icons.map),
      title: Text('Map'),
    ),
    ListTile(
      leading: Icon(Icons.photo_album),
      title: Text('Album'),
    ),
    ListTile(
      leading: Icon(Icons.phone),
      title: Text('Phone'),
    ),
  ],
);
```

## การสร้าง List แบบแนวนอน

เราสามารถกำหนดค่า `scrollDirection` ด้วย `Axis.horizontal` ได้

```dart
ListView(
  // This next line does the trick.
  scrollDirection: Axis.horizontal,
  children: <Widget>[
    Container(
      width: 160.0,
      color: Colors.red,
    ),
    Container(
      width: 160.0,
      color: Colors.blue,
    ),
    Container(
      width: 160.0,
      color: Colors.green,
    ),
    Container(
      width: 160.0,
      color: Colors.yellow,
    ),
    Container(
      width: 160.0,
      color: Colors.orange,
    ),
  ],
)
```

## การสร้าง List แบบ Dynamic 

เราสามารถใช้ `ListView.builder()` ในการสร้าง  ListView แบบ Dynamic ได้

โดย `itemBuilder` จะส่ง `context` และเลข `index` ในการวนลูปเข้ามาให้ใช้งาน 

ตัว method นี้ต้องการ return `Widget` ออกไปใช้งาน

```dart

List<String> items;

ListView.builder(
    itemCount: items.length,
    itemBuilder: (context, index) {
    return ListTile(
        title: Text('${items[index]}'),
    );
    },
),

```
