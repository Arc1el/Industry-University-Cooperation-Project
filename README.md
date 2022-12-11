# 2022학년도 한밭대학교 SW중심대학 산학협력프로젝트
#### 애완 동물 건강 상태 모니터링 센서 모듈 (Health Monitoring Sensor Module for Pets)


<img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"><img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white"><img src="https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=Express&logoColor=white"><img src="https://img.shields.io/badge/Javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=white"><img src="https://img.shields.io/badge/WebRTC-333333?style=for-the-badge&logo=webrtc&logoColor=white"><img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"><img src="https://img.shields.io/badge/Espressif-E7352C?style=for-the-badge&logo=espressif&logoColor=white">

**참여 인력**
- 연구 책임자 : 이현빈 (한밭대학교)
- 기업 연구원 : 윤섭 (㈜우레)
- 대학원생 연구원 : 이보석 (한밭대학교)
- 대학원생 연구원 : 한재흔 (한밭대학교)
- 학부생 연구원 : 김현민 (한밭대학교)
- 학부생 연구원 : 박종호 (한밭대학교)

- ### 과제 필요성 및 목표
  - 과제 개요
    - 마이크와 앰프, 아두이노를 활용하여 심박소리를 디지털 신호로 받아 이를 외부로 출력하는 앱을 개발하여, 기존 유선방식 청진기의 단점에서 벗어나 선의 길이에 구애 받지 않고 환자 혹은 의사가 편하게 사용할 수 있도록 함. 또한 전송된 심박소리(데이터)는 서버를 통해 저장되어 사용자의 요청에 따라 이전데이터를 출력해보고 시각화 하는등의 편의 기능을 제공하고자 함. 
    - 비접촉식 IR 체온센서와 로드셀(장력측정)센서를 활용하여 체온과 호흡수를 측정하여 지속적으로 모니터링이 필요한 특수한 상황에 대해 사람이 수동적으로 특정 주기마다 생체 데이터를 수집하는것이 아닌 센서를 통한 자동 수집기능 구현을 목표로 함. 수집된 데이터는 데이터베이스 연계를 통해 서버에 저장되고 사용자의 요청에따라 출력이 용이하도록 구현하고자 함.
  - 과제 필요성
    - 현재 동물병원에서는 주기적으로 입원한 반려동물에 대해 생체정보를 시트에 기록한다. 주로 기록하는 내용은 체온, 심박수, 호흡수 이다. 체온은 직장에 체온계를 넣어서 기록하고, 심박수는 청진기를 활용, 호흡수는 직접 1분간 아랫배가 올라오고 내려옴을 눈으로 확인하여 총 2회 실시하고 평균값을 사용한다. 반려동물 한 마리마다 수분의 시간이 걸리며, 전문테크니션 여러명이 동시에 달라붙어 측정한다. 해당 행위를 1시간 주기로 해주어야 한다.
    - 물론 한 마리라면 문제가 없겠지만 여러마리의 경우에는 이야기가 달라진다. 반려동물 한 마리를 측정하는데 5분이라고 가정하면 열두마리를 측정한다고 하였을 때 마지막 개체를 측정하면 또다시 첫 번째 개체의 생체데이터를 수집해야한다. 때문에 동물병원에서는 이를 수집하고 기록하는 일만 전담으로 하는 전문 테크니션을 고용하기도 한다. 대형병원의 경우에는 이에 따른 인건비가 만만치 않다.
    - 때문에 동물병원에서 이를 자동으로 측정해주는 모듈을 개발하려고 한다. 해당 기기를 통해 동물병원에서의 인건비를 줄이고, 데이터를 자동으로 측정하여 이를 문서화하여 테크니션들의 업무 부담을 줄이고자 한다.
  - 과제 목표
    - 정량적 목표는 센서를 통해 수동적으로 측정한 데이터에 못지 않는 정확한 센싱 데이터를 얻는 것을 목표로한다. 얻을 수 있는 데이터의 신뢰도를 가장 높게 끌어올리는 것을 목표로 한다. 
    - 정성적 목표는 해당 디바이스들과 시스템을 활용하여 사람 혹은 동물병원에서 실제로 적용할 수 있는가와 만약 실제로 사용했을때의 사용자의 만족도를 높이는 것을 목표로한다. 이를 위해 손쉽게 사용할 수 있고, 시스템의 경우 직관적이며 유저친숙한 GUI를 구성하여 처음 이용하는 사용자도 손쉽게 활용할 수 있도록 하는 것이 목표이다.

## 과제 수행 결과
  * ESP32를 활용한 센서데이터 무선 수집, WiFi Provisioning 사용
    * 모듈의 성능/기능을 고려하여 Espressif 사의 IoT 임베디드 SoC 칩 ESP32 사용
    * ESP32의 듀얼코어를 통해 데이터 수집과 송신을 동시에 수행
    * ESP32의 WiFi모듈을 통해 인터넷 환경에 연결
    * WiFi Provisioning을 구현하여 사용자가 시스템에서 손쉽게 IT 인프라를 설정 할 수 있도록 함
        
  * 호흡수, 체온 측정기능 구현. 데이터베이스 저장
    * RFID리더 모듈을 활용하여 반려동물의 생체 인식칩을 인식함
    * 장력측정(로드셀:hx711)을 활용하여 모듈의 밴드부분의 장력을 측정, 이를 활용하여 호흡수를 검출
    * 적외선 온도센서(gy906)를 활용하여 모듈 하우징 아랫부분의 체온을 측정, 이를 활용하여 반려동물의 체온을 검출
    * 검출된 센싱데이터는 수집과 동시에 json화 하게되고, 일정 주기에 따라 API서버로 전송됨.
      
  * 3D프린터를 활용한 하우징 제작
    * <img src="https://user-images.githubusercontent.com/8403172/206904207-3b2ee388-299d-4d3d-a258-060841c020d0.png" width="30%" height="30%">
      
  * MySQL을 사용하는 데이터베이스 구현
    * MySQL과 phpMyAdmin(DBMS)를 활용하여 센싱데이터, 반려동물 정보를 저장
      
  * 데이터베이스서버와 WAS서버 간 데이터 교환을 위한 API서버 구현
    * Node.js의 프레임워크중 하나인 Express를 활용하여 api서버 구현
    * api서버는 모듈에서 전송해온 데이터를 데이터베이스 서버에 저장
    * api서버는 WAS서버에서 요청해오는 데이터를 데이터베이스를 호출하여 전송

  * 모니터링 시스템을 구현하는 WAS서버 제작
    * Node.js의 프레임워크중 하나인 Express를 활용하여 api서버 구현
    * 반려동물 등록 기능은 모듈을 통해 데이터베이스 서버에 저장된 반려동물의 RFID값을 참조
    * 반려동물 모니터링 기능은 데이터베이스 서버에 저장된 반려동물 정보와 센싱데이터 정보를 JOIN하여 테이블로 출력
    * 테이블 외에 도넛차트, 꺾은선 그래프를 통해 반려동물의 정상/비정상 여부를 시각화
      
- ### System Dependencies
  - API Server
    * (Hardware) Raspberry Pi4. However, it can run on any Linux os
    * node >= v16.14.2
    * express >= v4.16.1
    * npm >= v16.14.2
    * mysql >= v2.18.1 (mysql-connector)

  - Web Application Server (WAS)
    * (Hardware) Raspberry Pi4. However, it can run on any Linux os
    * node >= v16.14.2
    * express >= v4.17.1
    * npm >= v16.14.2
    * mediasoup >= v3.11.3
    * mediasoup-client >= v3.6.37
    * socket.io >= 4.1.3

  - DB Server
    * (Hardware) Raspberry Pi4. However, it can run on any Linux os
    * mysql-server (8.0.31-0ubuntu0.22.04.1)
  - Module
    * NodeMCU-32S Lua WiFi (ESP-32)
      
## Installing and Running
  - Install API server and WAS
  ```sh
  cd {Project Directory Path(API or WAS)}
  npm install
  ```
  - Running Application
  ```sh
  npm start
  ```

## Conclusion
  - ### 웨어러블 모듈
    <img src="https://user-images.githubusercontent.com/8403172/205635133-46872ecc-ec18-43c0-af1b-6fb22083978d.jpg" width="22%" height="22%">  
    <img src="https://user-images.githubusercontent.com/8403172/205685603-2df895d7-8547-4cfb-b384-1304420206f2.gif" width="30%" height="30%">  
    <img src="https://user-images.githubusercontent.com/8403172/205685638-5606ba37-9869-4f4c-b674-55e4721618d7.gif" width="30%" height="30%">  
  - ### 모니터링 시스템
    <img src="https://user-images.githubusercontent.com/8403172/205635469-149729bb-95a2-4c0d-9fa4-495818c8fee2.jpg" width="30%" height="30%">  
    <img src="https://user-images.githubusercontent.com/8403172/205686786-5abd97ab-b3ef-4395-921f-71ba0e198f2f.png" width="48%" height="48%">
   
## Reference List
  - 이진홍, 유성희(2020), 「코로나19 사태로 비추어 본 반려동물 원격진료 도입 가능성에 대한 법적 고찰」, 『의생명과학과법』23, 법학연구소(원광대), pp.113-134 
  - 정한조, 이정훈, 이지형, 김세윤, 정지원(2020), 「웨어러블 디바이스를 이용한 반려동물 원격 모니터링 시스템」, 『한국컴퓨터정보학회 학술발표논문집』28, 한국컴퓨터정보학회, pp. 281-282
  - 이민형, 유래현, 김수연, 김경호(2021), 「반려동물 생체신호 측정 시스템에 관한 연구」, 『대한전기학회 학술대회 논문집』, 대한전기학회, pp. 405-406
  - 박주연, 윤지윤, 이예진, 박서영, 김두열, 이기석(2021), 「반려동물 생체인식 앱」, 『한국컴퓨터정보학회 학술발표논문집』29, 한국컴퓨터정보학회, pp. 351-354
  - 이병규, 박재곤, 유채은, 유하정(2018), 「IoT를 이용한 반려동물 Healthcare System」, 『한국정보과학회 학술발표논문집』, 한국정보과학회, pp.2226-2228
  - 유경근(2016), 「반려동물 자가진료 금지에 대한 올바른 이해 - 반려동물 자가진료 금지의 의미와 범위, 그리고 목적」, 『대한수의사회지 제 52권』8, 대한수의사회, pp.462-466
  - 김종수. 무선 청진기를 포함하는 웨어러블 장치(WEARABLE DEVICE HAVING WIRELESS STETHOSCOPE), 특허 출원번호 1020180128023, 출원일 2018.10.25., 등록일 2019.03.05.
  - 주식회사 케어식스, 심전도와 심탄도 동시 측정이 가능한 반려견용 심장운동 측정 장치(Dog cardiometry device for simultaneous measurement of EKG and ECG), 특허 출원번호 1020190128260
  - 주식회사 케어식스, 반려견의 활동량과 심박호흡등 생체신호 그리고 임상신호에 기반한 질병예측 방법 및 장치(Disease Prediction Method and Apparatus Based on the Activity of Dogs, Bio-signal), 특허 출원번호 1020190128299


