# Excercise 1 : การสร้าง Container

### 1. ดาวน์โหลด Docker image

```
docker pull  docker/getting-started
```

### 2. สร้าง Docker container 

#### สร้าง container ชื่อ ```first-docker```

```
docker run -d -p 80:80 --name first-docker docker/getting-started 
```
เปิดเว็บหน้า http://127.0.0.1:80

### 3. ดู Docker container 

ดู docker process ยังมีสถานะ ``up``` อยู่
```
docker ps 
```

ดู docker process ทั้งหมด (ทั้ง ```up``` และ ```down```)
```
docker ps -a
```

ดู logs ของ docker 
```
docker logs first-docker
```

ดู ข้อมูลของ ของ docker 
```
docker inspect first-docker
```

### 4. หยุด Run Container ```first-docker```

```
docker stop first-docker
```

ดู Process docker ทั้งหมดที่อยู่ในเครื่อง
```
docker ps -a
```

### 5. ลบ Container ```first-docker```

```
docker rm first-docker
```

ดู Process docker ที่ยังเหลืออยู่ในเครื่อง
```
docker ps first-docker
```
