# TrueNAS 실행 파일 만들기 
하드웨어 정보 
Server : HPE ProLiant Gen8 DL360 
Drive : HDD 128GB * 8EA 
Raid : Raid5 (3EA) Boot Drive / Raid5 (5EA) Storage Drive 
TrueNAS ip : 192.168.0.33

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

## 3. Language Set
System -> General Settings -> Localization

<img width="1915" height="897" alt="image" src="https://github.com/user-attachments/assets/1f2980b0-eade-480c-b246-8e5c36f98d5f" />

## 4. Pool Create
<img width="1612" height="823" alt="image" src="https://github.com/user-attachments/assets/59161bc6-af2b-414a-ba9e-51c4b85ea85e" />

1. General Info 에서 Pool Name을 설정

2. Data에서 사용할 Raid, Disk 설정

<img width="960" height="843" alt="image" src="https://github.com/user-attachments/assets/ad91839f-1267-4a38-b337-e3f63c214e7a" />

3. Create Pool 

## 5. Datasets
Datasets에서 Pool의 디렉터리 파일 생성 

<img width="1447" height="846" alt="image" src="https://github.com/user-attachments/assets/2980da1c-ffbb-4df7-bdc4-03575d535823" />

Name : 사용할 디렉터리의 이름 
<img width="997" height="845" alt="image" src="https://github.com/user-attachments/assets/7daeb63c-8efc-4084-93b0-521c3401bb51" />

고급옵션 - ACL 유형 : SMB / NFSv4 (모바일 접속 가능 ※ CX파일탐색기 APP 다운로드 받아야함) 

<img width="997" height="848" alt="image" src="https://github.com/user-attachments/assets/091391d3-2b18-4060-b9d8-2f19b521b0e4" />

## 6. User / Group Add 
Credentials -> Users / Groups -> Add

<img width="1919" height="857" alt="image" src="https://github.com/user-attachments/assets/3ac7504f-13af-4409-a64a-26757a0ef682" />

Username / password 설정 

<img width="986" height="843" alt="image" src="https://github.com/user-attachments/assets/d99328ba-b569-4007-a30e-32f61be57abf" />

1. Datasets에서 만들었던 디렉터리를 자신이 사용할 home 디렉터리로 지정 
2. Permissions 설정 
3. Primary Group 설정 
4. Save 

<img width="996" height="830" alt="image" src="https://github.com/user-attachments/assets/9589d758-082d-4873-8914-45a204bbe8d1" />

## 7. Windows(SMB) Shares
Shares -> SMB Shares Add 

추가할 SMB 디렉터리 지정 
Name 설정 
<img width="598" height="835" alt="image" src="https://github.com/user-attachments/assets/a9141a24-074b-4c83-b907-f3e95f4cbf31" />

Purpose : Multi-Protocol (NFSv4/SMB) Shares     //모바일로 볼 수 있게 사용하기위함 

<img width="602" height="835" alt="image" src="https://github.com/user-attachments/assets/33479ff7-ad41-44dc-a1d9-7700f0fdc053" />

## 8. Webdav download
App -> Discover Apps -> Webdav 검색 후 Download 

<img width="1917" height="905" alt="image" src="https://github.com/user-attachments/assets/62b4f640-9b0b-4849-a2a8-139504a29a8e" />

### Webdav 설정 
User and Group Configuration (권한 설정)

<img width="477" height="316" alt="image" src="https://github.com/user-attachments/assets/8bc0d873-6205-4398-a265-93a3bcee1c37" />

Network Configuration (사용할 Port 설정)

<img width="819" height="712" alt="image" src="https://github.com/user-attachments/assets/2c4e3157-c990-4728-ab20-2691a63bcf67" />

Storage Configuration 
Share Name : 모바일에서 접속할 파일 이름 ex) Share Name : arkarkark  -----> 121.165.211.174/arkarkark 이런식으로 접속
HostPath : 공유할 디렉터리 설정 

<img width="777" height="840" alt="image" src="https://github.com/user-attachments/assets/51033e89-059b-42b0-8209-227eff2a425d" />


## 사설 인증서 만들기 
### 1. Certification Authorities -> Add 

<img width="1592" height="676" alt="image" src="https://github.com/user-attachments/assets/639c9c61-b8e2-401c-a354-b60926290335" />

### 2. 인증서 및 기관 추가 

<img width="588" height="819" alt="image" src="https://github.com/user-attachments/assets/51a7f56d-85b8-41d0-b34e-d96e9eb24b05" />
**Identifier and Type **
1. Name : 인증서 사용할 이름 
2. Type : Internal CA
3. Profile : 빈칸 

**Certificate Options**
1. Key Type : RSA
2. Key Length : 2048 
3. Digest Algorithm : SHA256
4. Life time : 3650 (10년)

### 3. Certificates -> Add 
1. Name : 사용할 이름 
2. Type : Internal Certificate 
3. Profile : RSA 

**Certificate Options**
1. Signing Certificate Authority : 2번에서 만들었던 인증서 선택 
2. Key Type : RSA 
3. Key Length : 2048
4. Digest Algorithm : SHA256
5. Life time : 3650


## 고정 IP에서 외부 IP 접속 허용 하는 방법 
1. 고정 IP의 대역의 ipTIME 공유기의 포트포워딩 설정 메뉴로 접속
ex) 나의 IP가 192.168.0.100이라면 --> 192.168.0.1 URL에 접속 or 공인IP주소 URL에 입력 

<img width="1093" height="796" alt="image" src="https://github.com/user-attachments/assets/58319dc3-bedb-4930-ba45-7a3c8d963ec0" />


2. 포트포워딩의 
규칙 이름 : trunas 
내부 IP주소 : 나의 IP주소 192.168.0.33
프로토콜 : TCP
외부포트 : 8080
내부포트 : 8080

3. 외부 인터넷에서 접속할 때
http://<공유기 공인 IP>:8080 ------> http://121.165.211.174:8080
공인 IP는 iptime 접속하면 바로 나와있다.
