# เคมีในชีวิตประจำวัน (GitHub Pages + Firebase)

## 1) ตั้งค่า Firebase (ฟรี)
1. เข้า https://console.firebase.google.com แล้วกด Add project
2. Build > **Authentication** > Get started > เปิด **Email/Password** > แท็บ Users > Add user (อีเมล+รหัสผ่านของครู)
3. Build > **Firestore Database** > Create database (โหมด production)
4. แท็บ **Rules** วางเนื้อหาจาก `firestore.rules` (แก้อีเมลครูให้ตรง) แล้ว Publish
5. Project settings > Your apps > กด `</>` (Web) > คัดลอก `firebaseConfig` ไปใส่ใน `firebase-config.js` และแก้ `TEACHER_EMAIL`
6. Authentication > Settings > **Authorized domains** > เพิ่ม `ชื่อผู้ใช้.github.io`

## 2) อัปขึ้น GitHub Pages
1. สร้าง repository ใหม่ (Public) บน github.com
2. Add file > Upload files > ลากไฟล์ `index.html`, `firebase-config.js`, `icon.svg`, `manifest.webmanifest` (ไม่ต้องอัป firestore.rules ก็ได้) > Commit
3. Settings > Pages > Source: Deploy from a branch > `main` / root > Save
4. รอ 1-2 นาที เว็บจะอยู่ที่ `https://ชื่อผู้ใช้.github.io/ชื่อ-repo/`

## การใช้งาน
- นักเรียน: เปิดลิงก์ ดูรูปได้ทันที ไม่ต้องล็อกอิน
- ครู: กด "เข้าสู่ระบบครู" ที่มุมขวาบน แล้วจะเห็นปุ่มอัปโหลดและปุ่มลบรูป
- รูปถูกย่อเหลือไม่เกิน ~900KB และเก็บใน Firestore เพื่อไม่ต้องเปิดบิล Firebase Storage
- ความปลอดภัย: ค่า apiKey ของ Firebase เปิดเผยได้ ความปลอดภัยอยู่ที่ `firestore.rules` (เฉพาะอีเมลครูเท่านั้นที่เขียนได้)

## ให้อาจารย์ใช้เหมือนแอป (ไม่ต้องล็อกอินซ้ำ)
- ผู้ดูแลตั้งรหัสผ่านให้อาจารย์ที่ Authentication > Users > Add user (แก้รหัสผ่านภายหลังได้ที่เมนู ⋮ > Reset password)
- อาจารย์ล็อกอินครั้งแรกครั้งเดียว ระบบจำไว้ในเครื่องนั้นจนกว่าจะกด "ออกจากระบบ"
- มือถือ: เปิดเว็บแล้วเลือก "เพิ่มลงหน้าจอหลัก" (iPhone: ปุ่มแชร์ > Add to Home Screen, Android: เมนู ⋮ > ติดตั้งแอป) จะมีไอคอนให้กดเข้าได้เลย
- ถ้ารหัสผ่านรั่ว ให้เปลี่ยนรหัสผ่านใน Firebase Console ได้ทันที
