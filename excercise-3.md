# Excercise 3 Built a new image  
reference: [[มาสร้าง Docker Image กันเถอะ!](https://medium.com/i-gear-geek/%E0%B9%80%E0%B8%82%E0%B8%B5%E0%B8%A2%E0%B8%99-docker-file-%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B9%84%E0%B8%94%E0%B9%89-docker-image-d2dedd10361e), [multistage-build](https://docs.docker.com/develop/develop-images/multistage-build/)]  

## 1. สร้าง Direcotory ใหม่สำหรับเป็น Dockerfile
```
mkdir my-images
```

## 2. สร้าง Dockerfile 

Dockerfile เป็น Script หรือ Configuration ที่ใช้สำหรับสร้าง Image ใหม่ขึ้นมา  
ภายใน Dockerfile มีส่วนประกอบด้วย  
1. Base Image 
2. Command
   * COPY <src> <dest>
   * ADD <src> <dest>
   * RUN <command>
   * WORKDIR
   * etc.
3. ENTRYPOINT (จุดเริ่มทำงานของ Docker)


สร้าง Dockerfile ด้วยคำสั่ง vim Dockerfile และคัดลอก Config ต่อไปนี้ลงไป
```

```
## 3. Built Docker 
```
docker build -t imageName:tagName .
```
