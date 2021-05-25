# Excercise 3 Built a new image  
reference: [[มาสร้าง Docker Image กันเถอะ!](https://medium.com/i-gear-geek/%E0%B9%80%E0%B8%82%E0%B8%B5%E0%B8%A2%E0%B8%99-docker-file-%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B9%84%E0%B8%94%E0%B9%89-docker-image-d2dedd10361e), [multistage-build](https://docs.docker.com/develop/develop-images/multistage-build/),[docker-maven](https://codefresh.io/howtos/using-docker-maven-maven-docker/)]  

## 1. Clone node.js code จาก github
```
git clone https://github.com/jitech-th/container-training.jitech.co.th.git container-lab
cd container-lab/exercise-3
```

## 2. สร้าง Dockerfile 

***note
```text
Dockerfile เป็น Script หรือ Configuration ที่ใช้สำหรับสร้าง Image ใหม่ขึ้นมา  
ภายใน Dockerfile มีส่วนประกอบด้วย  
1. Base Image (ฐาน image ที่จะเอามาสร้าง Image ต่อ)
2. Command (คำสั่งเพื่อแก้ไขดัดแปลง Image เดิม โดย Docker จะสร้างเป็น Image Layer ใหม่ทุกบันทัดของคำสั่งจะ )
   * COPY <src> <dest>
   * ADD <src> <dest>
   * RUN <command>
   * WORKDIR 
   * USER
   * EXPOSE (กำหนด port ที่ต้องการให้เข้าถึงได้จากภายนอก)
   * etc.
3. ENTRYPOINT หรือ CMD (เป็นการกำหนดจุดเริ่มทำงานของ container เมื่อ Run Image)
```

สร้าง Dockerfile ด้วยคำสั่ง vim ```Dockerfile``` และคัดลอก Config ต่อไปนี้ลงไป
```
FROM node:10-alpine

ADD ./hello-world /hello-world
RUN chown -R node:node /hello-world
WORKDIR /hello-world
USER node
RUN cd /hello-world; npm install
EXPOSE 3030

CMD [ "node", "app.js" ]
```
## 3. Built Docker 
```
docker build -t hello-world .
```

# 4. Create container from image

```
docker run -d -p 3030:3030 hello-world 
```

# 5. สร้าง Tag เพื่อเตรียม Push ขึ้น Docker Registry
สร้าง Tag เพื่อใช้ำสำหรับ push ขึ้นบน dockerhub.io
```
docker tag hello-world dockerhub.io/pt1988/hello-world:1.0 
```
# 6. Push Image ขึ้น Registry (Dockerhub.io)
login account ของ Dockerhub ด้วยคำสั่ง
```
docker login
```

push image ขึ้น Registry ด้วยคำสั่ง
```
docker push dockerhub.io/pt1988/hello-world:1.0 
```
