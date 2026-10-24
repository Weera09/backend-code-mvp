
# Database Design — Mactile MVP

## 1. ภาพรวม
ระบบ Mactile เป็นระบบเช่ากล้องถ่ายรูปและรับจองงานถ่ายภาพ

## 2. ตาราง users
| Field | Description |
|---|---|
| id | รหัสผู้ใช้ |
| name | ชื่อผู้ใช้ |
| email | อีเมล |
| password_hash | รหัสผ่านที่เข้ารหัส |
| role | customer, provider, admin |

## 3. ตาราง cameras
| Field | Description |
|---|---|
| id | รหัสกล้อง |
| owner_id | เจ้าของกล้อง |
| name | ชื่อกล้อง |
| brand_model | ยี่ห้อและรุ่น |
| description | รายละเอียด |
| image_url | รูปภาพ |
| rental_price | ราคาเช่า |
| status | สถานะกล้อง |

## 4. ตาราง camera_rentals
| Field | Description |
|---|---|
| id | รหัสการเช่า |
| camera_id | รหัสกล้อง |
| customer_id | รหัสลูกค้า |
| start_at | วันเริ่มเช่า |
| end_at | วันคืน |
| status | สถานะการเช่า |

## 5. ตาราง photography_services
| Field | Description |
|---|---|
| id | รหัสบริการ |
| photographer_id | รหัสช่างภาพ |
| title | ชื่อบริการ |
| category | ประเภทงาน |
| description | รายละเอียด |
| price_from | ราคาเริ่มต้น |

## 6. ตาราง photography_bookings
| Field | Description |
|---|---|
| id | รหัสการจอง |
| service_id | รหัสบริการ |
| customer_id | รหัสลูกค้า |
| event_at | วันเวลาถ่ายภาพ |
| location | สถานที่ |
| details | รายละเอียดงาน |
| status | สถานะการจอง |

## 7. ความสัมพันธ์
- users สามารถมีรายการกล้องได้หลายรายการ
- users สามารถส่งคำขอเช่าได้หลายครั้ง
- cameras มีประวัติการเช่าได้หลายรายการ
- photographers สามารถมีบริการถ่ายภาพได้หลายบริการ
- photography_services สามารถมีรายการจองได้หลายรายการ

## 8. กฎของระบบ
- อีเมลผู้ใช้ต้องไม่ซ้ำ
- วันคืนต้องมากกว่าวันเริ่มเช่า
- กล้องเดียวกันต้องไม่ถูกจองซ้ำในช่วงเวลาที่ทับซ้อน
- ผู้ใช้ต้องมีสิทธิ์ก่อนจัดการข้อมูล
- รหัสผ่านต้องไม่จัดเก็บเป็นข้อความธรรมดา

