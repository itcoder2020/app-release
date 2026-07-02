# CloudPhoneTH — App Release

ที่เก็บไฟล์อัปเดตของแอพ CloudPhoneTH — แอพจะดึง `version.json` จากที่นี่มาเทียบเวอร์ชัน

## วิธีปล่อยเวอร์ชันใหม่

1. เพิ่ม `versionCode` + `versionName` ใน `app/build.gradle.kts` ของโปรเจกต์แอพ แล้ว build:
   ```
   ./gradlew assembleRelease
   ```
2. อัปโหลด apk ขึ้น GitHub Release (tag เช่น `v0.2.0`)
3. แก้ `version.json` ที่ repo นี้ให้ `versionCode` ตรงกับที่ build + เปลี่ยน `apkUrl` เป็นลิงก์ release ใหม่
4. commit + push — ผู้ใช้จะเห็นการแจ้งอัปเดตตอนเปิดแอพครั้งถัดไป

## รูปแบบ version.json

| field | ความหมาย |
|-------|----------|
| `versionCode` | เลขเวอร์ชันที่แอพใช้เทียบ (ต้องเพิ่มขึ้นเสมอ) |
| `versionName` | ชื่อเวอร์ชันที่โชว์ให้ผู้ใช้ |
| `apkUrl` | ลิงก์ดาวน์โหลด apk จาก GitHub Release |
| `changelog` | สิ่งที่เปลี่ยน (ขึ้นบรรทัดด้วย `\n`) |
| `forceUpdate` | `true` = บังคับอัปเดต ปิด modal ไม่ได้ |
