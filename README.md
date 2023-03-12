# Ref
- [https://github.com/docker/awesome-compose/tree/master/sparkjava]

# Wakatime project
- [https://wakatime.com/@spcn16/projects/cvfbjcxdgf?start=2023-03-05&end=2023-03-11]

##  ขั้นตอนการติดตั้งอยู่ใน swarm01 ก่อนถึงการสร้าง images เข้า dockerhub
- [https://github.com/Nattiya18/swarm01]
##  สร้าง image สำหรับการเตรียม push ขึ้น Docker hub

         sudo docker images
         
* Login Docker
         
           docker login
           
* กำหนด tag

           docker tag swarm02-sparkjava:latest nattiya18/sparkjava:sparkjava

* Push ขึ้นไปที่ Docker Hub

           docker push nattiya18/sparkjava:sparkjava