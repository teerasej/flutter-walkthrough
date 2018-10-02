
# วิธีใช้งานรูปภาพแบบต่างๆ 

## A. แบบโหลดจาก Internet (Network Image)

```dart
Image.network('https://nextflow.in.th/wp-content/uploads/2013/04/nextflow-logo-training-service-normal-22.png');
```

สิ่งที่ได้จาก `Image.network()` จะเป็น Widget ตัวหนึ่ง ที่สามารถเอาไปใช้ใน Widget อื่นๆ ได้

```dart
Container(
    child: Image.network('https://nextflow.in.th/wp-content/uploads/2013/04/nextflow-logo-training-service-normal-22.png');
)
```

## B. แบบโหลดจาก Assets ภายใน App

ถึงแม้ว่าเราจะเอาไฟล์รูปภาพไปใส่ไว้ในโปรเจค แต่การจะ **bundle** มันเข้าไปในแอพนั้น ต้องมีการเขียนบอกไว้ในไฟล์ `pubspec.yaml` ด้วย

```yaml
flutter:
  assets:
    - assets/my_icon.png
    - assets/background/nextflow_wallpaper.png
```

ถ้าต้องการเอาทุกไฟล์ที่อยู่ในโฟลเดอร์ ก็ให้ระบุชื่อโฟลเดอร์ แบบมีเครื่องหมาย `/` เช่น

```yaml
flutter:
  assets:
    - assets/
```

### วิธีการโหลดภาพจาก Asset 

```dart
DecoratedBox(
    decoration: BoxDecoration(
      image: DecorationImage(
        image: AssetImage('assets/background/nextflow_wallpaper.png'),
        // ...
      ),
      // ...
    ),
  );
```