# Excercise 1 : การสร้าง Container

### 1. ดาวน์โหลด Docker image ด้วยคำสั่ง "docker pull"

Run คำสั่งต่อไปนี้เพื่อ Download docker images ชื่อ ```getting-started``` ที่อยู่ใน Registry ของ docker 
```
docker pull  docker/getting-started:latest
```
 
ดูรายการของ Images ทั้งหมดที่มีอยู่ในเครื่องด้วยคำสั่ง ```docker images```

```
docker images
```

จะได้ผลลับต่อไปนี้

```
REPOSITORY                           TAG                                              IMAGE ID            CREATED             SIZE
mysql                                5.7                                              2c9028880e58        5 days ago          447MB
mongo                                latest                                           07630e791de3        6 days ago          449MB
docker/getting-started               latest                                           3ba8f2ff0727        8 weeks ago         27.9MB
...
```

<b>*** สังเกตว่า มี Field TAG ซึ่งมีลักษณะเดียวกับ TAG ของ git สามารถใช้ refence ถึง version ของ Images ได้</b>

### 2. สร้าง Docker container 

สร้าง container ชื่อ ```first-docker``` ด้วยคำสั่ง ```docker run```

```
docker run -d -p 80:80 --name first-docker docker/getting-started 
```
เปิดเว็บหน้า http://127.0.0.1:80

### 3. ตรวจสอบสถานะของ container (Check container status)

เรียกดูรายการ container ยังมีสถานะ ``up``` อยู่
```
docker ps 
```

เรียกดูรายการ container ทั้งหมด (ทั้ง ```up``` และ ```down```)
```
docker ps -a
```

เรียกดู logs ของ container 
```
docker logs first-docker
```

เรียกดูข้อมูลของของ container 
```
docker inspect first-docker
``` 

### 4. การ Run คำสั่งใน Container ด้วย "docker exec"

เรียกดูไฟล์ที่ working directory ของ container ด้วยคำสั่งนี้
```
docker exec -it first-docker ls 
```

ลอง shell เข้าไปใน container (ถ้า container นั้นมีคำสั่ง shell ให้ใช้)
```
docker exec -it first-docker ls 
```

### 5. หยุด Run Container "first-docker"

```
docker stop first-docker
```

ดู Process docker ทั้งหมดที่อยู่ในเครื่อง
```
docker ps -a
```

### 6. ลบ Container "first-docker"

```
docker rm first-docker
```

ดู Process docker ที่ยังเหลืออยู่ในเครื่อง
```
docker ps first-docker
```

### 6. ลบ Docker images ด้วยคำสั่ง ```docker rmi```

```
docker rmi getting-started
```
ตรวจสอบ image list ที่ยังเหลืออยู่ด้วยคำสั่ง ```docker images```
```
docker images
```

*** ถ้าลดไม่ได้อาจจะเป็นเพราะ container ที่สร้างด้วย Image นี้ยังไม่ถูกลบ

