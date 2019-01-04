# minio 실습 목차

>[minio 환경설정]

>[minio docker 이미지 다운로드]

>[minio docker 컨테이너 만들기 및 실행]

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


# minio docker 이미지 다운로드
Docker 허브에 등록 되어 있는 minio 이미지를 받습니다.
![](https://github.com/ddmsme/minio/blob/master/img/1.%EC%9D%B4%EB%AF%B8%EC%A7%80%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C.png)

이미지가 정상적으로 다운로드 되었는지 확인합니다.
![](https://github.com/ddmsme/minio/blob/master/img/3.%EC%9D%B4%EB%AF%B8%EC%A7%80%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C%ED%99%95%EC%9D%B8.png)



# minio docker 컨테이너 만들기 및 실행
------

```
sudo docker run -p 9000:9000 --name minio1 \
  -e "MINIO_ACCESS_KEY=AKIAIOSFODNN7EXAMPLE" \
  -e "MINIO_SECRET_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY" \
  -v D:\data:/data \
  -v D:\minio\config:/root/.minio \
  minio/minio server /data
```
결과확인
![](https://github.com/ddmsme/minio/blob/master/img/minio1.png)



# minio iptables & 방화벽 설정
-----
iptables 추가
![](https://github.com/ddmsme/minio/blob/master/img/5.iptabes--INPUT.png)

iptables 추가 리스트확인
![](https://github.com/ddmsme/minio/blob/master/img/6.iptabes--list.png)

iptables 재시작
![](https://github.com/ddmsme/minio/blob/master/img/7.iptables%20%EC%9E%AC%EC%8B%9C%EC%9E%91.png)

방화벽 허용
![](https://github.com/ddmsme/minio/blob/master/img/8%EB%B0%A9%ED%99%94%EB%B2%BD%ED%97%88%EC%9A%A9.png)
![](https://github.com/ddmsme/minio/blob/master/img/9%EB%B0%A9%ED%99%94%EB%B2%BD%ED%97%88%EC%9A%A9.png)
![](https://github.com/ddmsme/minio/blob/master/img/10%EB%B0%A9%ED%99%94%EB%B2%BD%ED%97%88%EC%9A%A9.png)
![](https://github.com/ddmsme/minio/blob/master/img/11%EB%B0%A9%ED%99%94%EB%B2%BD%ED%97%88%EC%9A%A9.png)


# minio Browser 결과확인
-----
로그인화면
![](https://github.com/ddmsme/minio/blob/master/img/12%EC%99%84%EB%A3%8C.PNG)

로그인 후 버킷만들기
![](https://github.com/ddmsme/minio/blob/master/img/12.%EB%A1%9C%EA%B7%B8%EC%9D%B8%ED%9B%84%20%ED%99%94%EB%A9%B4%20%EB%B2%84%ED%82%B7%EB%A7%8C%EB%93%A4%EA%B8%B0.PNG)
![](https://github.com/ddmsme/minio/blob/master/img/13.%EB%B2%84%ED%82%B7%EB%A7%8C%EB%93%A4%EA%B8%B0.png)

파일 업로드
![](https://github.com/ddmsme/minio/blob/master/img/14.testbucket_fileupload.png)
