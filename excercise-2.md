# สร้าง container ด้วยคำสั่ง docker-compose

## 1. ติดตั้ง Docker Compose 

[Reference](https://docs.docker.com/compose/install/)

## 2. เตรียมไฟล์สำหรับใช้กับ Docker-compose

```
mkdir my-project
cd my-project
vim docker-compose.yml
```

คัดลอก configuration วางในไฟล์ ```docker-compose.yml```
```
version: '3.1'
services:
  mysql:
    image: mysql:5.7
    ports:
      - 3308:3306
    volumes:
      - "./data:/var/lib/mysql"
    environment:
      MYSQL_ROOT_PASSWORD: 1234
      MYSQL_DATABASE: testhaha
  mongo:
    image: mongo
    restart: always
    volumes:
      - "./datamongo:/data/db"
    ports:
      - 27017:27017
  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    ports:
      - 8000:80
    environment:
      PMA_PASSWORD: 1234
      PMA_USER: root
      PMA_HOSTS: mysql
```

<b>*** สังเกตว่า บันทัดที่ 26 มีการอ้างอิงถึง container ชื่อ ```mysql``` ที่ defined ไว้ในบันทัดที่ 3 </b>

## 3. สร้าง container ด้วยคำสั่ง docker-compose

เข้าไป Directory เดียวกับที่ไฟล์ ```docker-compose.yml``` วางอยู่แลัว run คำสั่งต่อไปนี้
```
docker-compose up -d
```

ดู list containers ที่ run ด้วยคำสั่ง docker-compose ด้วยคำสั่งต่อไปนี้
```
docker-compose ps
```

ดู list containers ที่ run อยู่ทั้งหมดด้วยคำสั่งต่อไปนี้
```
docker ps
```

## 4. แก้ไขไฟล์ docker compose

แก้ไฟล์ ```docker-compose.yml``` โดยแก้ Port ของ phpmyadmin จาก 8000 เป็น 8080 แล้ว run คำสั่งต่อไปนี้
```
docker-compose up -d
```

## 5. หยุดการทำงานของ Docker ที่สร้างโดย docker-compose

```
docker-compose down
```
