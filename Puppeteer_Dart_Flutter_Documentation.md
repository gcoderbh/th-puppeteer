
# Puppeteer สำหรับ Dart Flutter

[Puppeteer Documentation](https://pub.dev/documentation/puppeteer/latest/puppeteer/puppeteer-library.html)

## บทนำ
Puppeteer คือไลบรารีสำหรับควบคุม Web Browser ผ่านโปรแกรม ซึ่ง Puppeteer สามารถทำงานได้กับ Browser ที่เป็น Chromium-based เช่น Google Chrome โดยสามารถใช้ในการทดสอบเว็บอัตโนมัติ การสแกนเว็บ การสร้างสกรีนช็อต และอื่น ๆ

## การติดตั้ง
สามารถติดตั้ง Puppeteer สำหรับ Dart Flutter ได้โดยการเพิ่ม dependencies ใน `pubspec.yaml`:

```yaml
dependencies:
  puppeteer: ^3.11.0
```

## การใช้งานพื้นฐาน
นี่คือตัวอย่างการใช้งานพื้นฐานของ Puppeteer ใน Dart:

```dart
import 'package:puppeteer/puppeteer.dart';

void main() async {
  var browser = await puppeteer.launch();
  var page = await browser.newPage();
  await page.goto('https://example.com');
  print(await page.title);
  await browser.close();
}
```

## ฟังก์ชันที่น่าสนใจ
1. **การเปิด Browser**: `puppeteer.launch()` - ใช้เพื่อเปิด Browser ใหม่
2. **การเปิดหน้าใหม่**: `browser.newPage()` - ใช้เพื่อเปิดหน้าใหม่ใน Browser
3. **การไปยัง URL**: `page.goto('https://example.com')` - ใช้เพื่อเปิด URL ที่กำหนด
4. **การอ่าน Title ของหน้าเว็บ**: `page.title` - ใช้เพื่อดึง Title ของหน้าเว็บ
5. **การปิด Browser**: `browser.close()` - ใช้เพื่อปิด Browser

## การใช้งานขั้นสูง
### การสร้าง Screenshot

```dart
import 'package:puppeteer/puppeteer.dart';

void main() async {
  var browser = await puppeteer.launch();
  var page = await browser.newPage();
  await page.goto('https://example.com');
  await page.screenshot(path: 'example.png');
  await browser.close();
}
```

### การประมวลผล HTML ของหน้าเว็บ

```dart
import 'package:puppeteer/puppeteer.dart';

void main() async {
  var browser = await puppeteer.launch();
  var page = await browser.newPage();
  await page.goto('https://example.com');
  var html = await page.content;
  print(html);
  await browser.close();
}
```

## รายการ Methods

### Browser Methods

#### launch
เปิด Browser ใหม่

```dart
var browser = await puppeteer.launch();
```

#### close
ปิด Browser ที่เปิดอยู่

```dart
await browser.close();
```

#### newPage
เปิดหน้าใหม่ใน Browser

```dart
var page = await browser.newPage();
```

### Page Methods

#### goto
ไปยัง URL ที่กำหนด

```dart
await page.goto('https://example.com');
```

#### screenshot
สร้าง screenshot ของหน้าเว็บ

```dart
await page.screenshot(path: 'example.png');
```

#### content
ดึง HTML content ของหน้าเว็บ

```dart
var html = await page.content;
print(html);
```

#### title
ดึง title ของหน้าเว็บ

```dart
var title = await page.title;
print(title);
```

#### evaluate
รัน JavaScript ใน context ของหน้าเว็บ

```dart
var result = await page.evaluate('() => document.title');
print(result);
```

#### click
คลิกที่องค์ประกอบที่ระบุ

```dart
await page.click('#buttonId');
```

#### type
พิมพ์ข้อความในองค์ประกอบที่ระบุ

```dart
await page.type('#inputId', 'Hello World');
```

#### waitForSelector
รอจนกว่าจะเจอ selector ที่ระบุ

```dart
await page.waitForSelector('#elementId');
```

#### waitForTimeout
รอเป็นเวลาที่กำหนด

```dart
await page.waitForTimeout(Duration(seconds: 5));
```

#### setViewport
กำหนดขนาดของ viewport

```dart
await page.setViewport(DeviceViewport(width: 1280, height: 800));
```

#### pdf
สร้าง PDF จากหน้าเว็บ

```dart
await page.pdf(format: PdfFormat.a4, path: 'example.pdf');
```

#### focus
โฟกัสที่องค์ประกอบที่ระบุ

```dart
await page.focus('#inputId');
```

#### hover
เอา mouse ไป hover ที่องค์ประกอบที่ระบุ

```dart
await page.hover('#elementId');
```

#### select
เลือก option ใน select element

```dart
await page.select('#selectId', 'optionValue');
```

#### tap
คลิกที่องค์ประกอบที่ระบุ (เหมือน click แต่สำหรับ touch devices)

```dart
await page.tap('#buttonId');
```

#### url
ดึง URL ของหน้าเว็บปัจจุบัน

```dart
var currentUrl = await page.url;
print(currentUrl);
```

#### waitForNavigation
รอจนกว่าจะมีการนำทางไปยังหน้าใหม่

```dart
await page.waitForNavigation();
```

#### setRequestInterception
กำหนดให้ดักจับ request ทั้งหมด

```dart
await page.setRequestInterception(true);
page.onRequest.listen((request) {
  if (request.url().contains('ads')) {
    request.abort();
  } else {
    request.continueRequest();
  }
});
```

#### on
ตั้ง listener สำหรับ events ต่าง ๆ ของหน้าเว็บ

```dart
page.onConsole.listen((consoleMessage) {
  print(consoleMessage.text());
});
```

#### waitForResponse
รอจนกว่าจะได้รับ response ที่ตรงกับเงื่อนไขที่กำหนด

```dart
await page.waitForResponse((response) => response.url().contains('example'));
```

### ElementHandle Methods

#### click
คลิกที่องค์ประกอบ

```dart
var element = await page.$('#buttonId');
await element.click();
```

#### type
พิมพ์ข้อความในองค์ประกอบ

```dart
var input = await page.$('#inputId');
await input.type('Hello World');
```

#### hover
เอา mouse ไป hover ที่องค์ประกอบ

```dart
var element = await page.$('#elementId');
await element.hover();
```

#### focus
โฟกัสที่องค์ประกอบ

```dart
var input = await page.$('#inputId');
await input.focus();
```

#### screenshot
สร้าง screenshot ขององค์ประกอบ

```dart
var element = await page.$('#elementId');
await element.screenshot(path: 'element.png');
```

#### boundingBox
ดึงขอบเขตขององค์ประกอบ

```dart
var element = await page.$('#elementId');
var box = await element.boundingBox();
print(box);
```

#### scrollIntoView
เลื่อนหน้าเว็บจนกว่าองค์ประกอบจะอยู่ใน view

```dart
var element = await page.$('#elementId');
await element.scrollIntoView();
```

#### evaluate
รัน JavaScript ใน context ขององค์ประกอบ

```dart
var element = await page.$('#elementId');
var result = await element.evaluate('el => el.textContent');
print(result);
```

### Frame Methods

#### goto
ไปยัง URL ที่กำหนดใน frame

```dart
var frame = page.frames[1];
await frame.goto('https://example.com');
```

#### evaluate
รัน JavaScript ใน context ของ frame

```dart
var frame = page.frames[1];
var result = await frame.evaluate('() => document.title');
print(result);
```

#### content
ดึง HTML content ของ frame

```dart
var frame = page.frames[1];
var html = await frame.content();
print(html);
```

#### title
ดึง title ของ frame

```dart
var frame = page.frames[1];
var title = await frame.title();
print(title);
```

#### click
คลิกที่องค์ประกอบที่ระบุใน frame

```dart
var frame = page.frames[1];
await frame.click('#buttonId');
```

#### type
พิมพ์ข้อความในองค์ประกอบที่ระบุใน frame

```dart
var frame = page.frames[1];
await frame.type('#inputId', 'Hello World');
```

#### waitForSelector
รอจนกว่าจะเจอ selector ที่ระบุใน frame

```dart
var frame = page.frames[1];
await frame.waitForSelector('#elementId');
```

#### waitForTimeout
รอเป็นเวลาที่กำหนดใน frame

```dart
var frame = page.frames[1];
await frame.waitForTimeout(Duration(seconds: 5));
```

หวังว่านี่จะเป็นประโยชน์สำหรับการใช้งาน Puppeteer ของคุณครับ!
