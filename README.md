# Docker-WordPress

1. `version: '3'`: ระบุเวอร์ชันของ Docker Compose file เป็นเวอร์ชัน 3

2. `services:`: เริ่มต้นการกำหนด services ที่จะใช้ใน Docker Compose

3. `db:`: กำหนด service ชื่อ `db` ซึ่งจะใช้ MySQL image และตั้งค่าต่าง ๆ สำหรับ MySQL server

   - `image: mysql:latest`: ใช้ image ล่าสุดของ MySQL
   - `volumes:`: กำหนดการ mount volumes เพื่อบันทึกข้อมูลฐานข้อมูล
   - `environment:`: ตั้งค่า environment variables สำหรับ MySQL
   - `ports:`: กำหนดการ map ports เพื่อเข้าถึง MySQL server ที่รันบน container

4. `phpmyadmin:`: กำหนด service ชื่อ `phpmyadmin` ซึ่งจะใช้ phpMyAdmin image และกำหนด environment variables สำหรับการเชื่อมต่อกับ MySQL server

   - `image: phpmyadmin/phpmyadmin`: ใช้ image ของ phpMyAdmin
   - `environment:`: ตั้งค่าตัวแปรสภาพแวดล้อมสำหรับการเชื่อมต่อกับ MySQL server
   - `ports:`: กำหนดการ map ports เพื่อเข้าถึง phpMyAdmin ที่รันบน container

5. `wordpress:`: กำหนด service ชื่อ `wordpress` ซึ่งจะใช้ WordPress image และกำหนด environment variables สำหรับการเชื่อมต่อกับ MySQL server

   - `image: wordpress:latest`: ใช้ image ล่าสุดของ WordPress
   - `depends_on:`: ระบุ dependency ที่ต้องมีก่อนในการรัน service นี้ (ในที่นี้คือ `db`)
   - `ports:`: กำหนดการ map ports เพื่อเข้าถึง WordPress ที่รันบน container
   - `environment:`: ตั้งค่าตัวแปรสภาพแวดล้อมสำหรับการเชื่อมต่อกับ MySQL server

6. `volumes:`: กำหนด volumes ที่ใช้ (ในที่นี้คือ `db_data` สำหรับบันทึกข้อมูลฐานข้อมูล)

แต่ละบรรทัดระบุการตั้งค่าและการเชื่อมต่อที่เกี่ยวข้องกับการสร้างและรัน containers ของ MySQL, phpMyAdmin, และ WordPress บน Docker Compose environment ครับ
