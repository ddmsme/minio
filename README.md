# minio 실습 목차

>[minio 환경설정]

>[minio docker 이미지 다운로드]

>[minio docker 실행]

>[minio iptables & 방화벽 설정]

>[minio Browser 결과확인]


# minio 환경설정
-----
### 설치파일

```bash
apt-get update
apt-get upgrade -y
sudo apt-get install docker.io //minio 컨테이너 생성시 사용
sudo apt-get install iptables-persistent  // iptables 설정 및 재시작
sudo apt install firewalld // 방화벽 설정
```

==================================================================================

Docker 허브에 등록 되어 있는 minio 이미지를 받습니다.
![](https://github.com/ddmsme/minio/img/1.이미지다운로드.png)

이미지가 정상적으로 다운로드 되었는지 확인합니다.
![](https://github.com/ddmsme/minio/img/3.이미지다운로드확인.png)



# minio docker 컨테이너 만들기 및 실행
------

```
docker run -p 9000:9000 --name minio1 \
  -e "MINIO_ACCESS_KEY=AKIAIOSFODNN7EXAMPLE" \
  -e "MINIO_SECRET_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY" \
  -v D:\data:/data \
  -v D:\minio\config:/root/.minio \
  minio/minio server /data
```



# docker 컨테이너로 접속하기
-----
exec로 접속
![](https://github.com/haneal/DockerRepo/blob/master/img/6.docker_exec.png)

attach로 접속
![](https://github.com/haneal/DockerRepo/blob/master/img/7.attach.png)

# docker 컨테이너간 네트워크 연결
-----
네트워크 그룹과 도커 컨테이너에 생성된 서브넷을 확인합니다.
![](https://github.com/haneal/DockerRepo/blob/master/img/3.2.docker-ls.png)
![](https://github.com/haneal/DockerRepo/blob/master/img/3_3_network%20create%20netowrk-group.png)

각각의 컨테이너 websevser 접속해서 ip정보와 동일한 각서버가 동일한 서브넷에 있는지 확인합니다.
![](https://github.com/haneal/DockerRepo/blob/master/img/8.network_ifconfig_1.png)
![](https://github.com/haneal/DockerRepo/blob/master/img/11.network_ifconfig.png)

ping을 통해 서로간 통신을 확인합니다.
![](https://github.com/haneal/DockerRepo/blob/master/img/13.network_ping_2.png)
![](https://github.com/haneal/DockerRepo/blob/master/img/12.network_ping.png)
