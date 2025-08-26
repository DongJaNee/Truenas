# TrueNAS 실행 파일 만들기 
하드웨어 정보 
Server : HPE ProLiant Gen8 DL360 
ip : 192.168.0.33

## 1. Server에 ISO파일 Mount하기

1. balenaEtcher를 사용하여 TrueNAS-SCALE 24.10.2.4 iso 파일을 담아서 Server 의 Mount 한다. 
<img width="108" height="106" alt="image" src="https://github.com/user-attachments/assets/c0e0c687-4d7a-4ad0-81fa-56f37068e10f" />
<br>
<img width="276" height="28" alt="image" src="https://github.com/user-attachments/assets/10f51ce7-2ae4-49e8-9ea7-3aeb064b3f9b" />

2. TrueNAS에서 할당된 IP 확인

<img width="476" height="286" alt="image" src="https://github.com/user-attachments/assets/b7176c5e-f2fb-4b20-a915-b1bbcc7f91f3" />

## 2. TrueNAS DashBoard 
1. TrueNAS DashBoard에 접속하려면 1번에서 설정했던 ip주소를 url에 입력한다.

<img width="312" height="34" alt="image" src="https://github.com/user-attachments/assets/7aeaf3ad-bf93-4fde-88b2-31ed59ac0105" />

2. 1번에서 ISO파일을 Mount 할 때 생성했던 아이디 : truenas_admin(기본값) 설정했던 pw를 입력하여 로그인한다.

<img width="593" height="830" alt="image" src="https://github.com/user-attachments/assets/3f3a764f-ab46-42ed-87b9-eec007f32f82" />

<img width="1905" height="907" alt="image" src="https://github.com/user-attachments/assets/5512cb95-70e2-48bf-ad01-f6547c8ab65b" />

## 3. Pool 생성




## 사설 인증서 만들기 
### 1. Certification Authorities -> Add 

<img width="1592" height="676" alt="image" src="https://github.com/user-attachments/assets/639c9c61-b8e2-401c-a354-b60926290335" />

### 2. 인증서 및 기관 추가 

<img width="588" height="819" alt="image" src="https://github.com/user-attachments/assets/51a7f56d-85b8-41d0-b34e-d96e9eb24b05" />
**Identifier and Type **
Name : 인증서 사용할 이름 
Type : Internal CA
Profile : 빈칸 

**Certificate Options**
Key Type : RSA
Key Length : 2048 
Digest Algorithm : SHA256
Life time : 3650 (10년)

### 3. Certificates -> Add 
Name : 사용할 이름 
Type : Internal Certificate 
Profile : RSA 

**Certificate Options**
Signing Certificate Authority : 2번에서 만들었던 인증서 선택 
Key Type : RSA 
Key Length : 2048
Digest Algorithm : SHA256
Life time : 3650
