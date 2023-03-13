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
           
           
## Add Stack ใน Portainer



![image](https://user-images.githubusercontent.com/119166253/224613008-322aea6f-f1a2-431d-9e64-5dcab533d240.png)

           
 ## Create stack deploy
 * Create file docker=coompose.yml in swarm path
```

         version: '3.3' 
                  services:
                    web: 
                      image: nattiya18/sparkjava:sparkjava
                      networks: 
                      - webproxy
                      logging:
                        driver: json-file
                      container_name: spcn16java
                      deploy: 
                        replicas: 1 
                        labels: 
                          - traefik.docker.network=webproxy
                          - traefik.enable=true
                          - traefik.http.routers.spcn16java-https.entrypoints=websecure 
                          - traefik.http.routers.spcn16java-https.rule=Host("spcn16java.xops.ipv9.xyz")
                          - traefik.http.routers.spcn16java-https.tls.certresolver=default
                          - traefik.http.services.spcn16java.loadbalancer.server.port=8080
                        resources: 
                          reservations: 
                            cpus: '0.1'
                            memory: 10M
                          limits: 
                            cpus: '0.4'
                            memory: 100M
                  networks: 
                    webproxy: 
                      external: true
                      
 
                     
![image](https://user-images.githubusercontent.com/119166253/224612644-0e15ded9-2cfa-4fc8-83b6-67229dbd0fdb.png)



* stack de ploy on portainer

* go to view result
```
-[https://spcn16java.xops.ipv9.xyz/]

![image](https://user-images.githubusercontent.com/119166253/224612793-691ba9ea-052f-444b-a7f7-fe02cf0d293b.png)
