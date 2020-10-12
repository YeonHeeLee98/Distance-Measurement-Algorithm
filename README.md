# 저전력 무선 센서 디바이스를 활용한 거리측정 알고리즘

</br>



## 개요

저전력 무선 센서 디바이스인 Beacon의 신호를 통해 수신되는 RSSI 값을 교정하여 측위 정확도를 개선하는 거리 측정 알고리즘을 제안한다. 

제안하는 알고리즘의 검증을 위해 BLE(Bluetooth Low Energy) 기술을 활용한 센서 디바이스를 구현하여 제안하는 알고리즘의 실효성을 검증한다. 

제안하는 알고리즘을 통해 측위 정확도 향상 및 물체 위치 측정 기능 개선을 기대할 수 있다.

</br>

## 시스템 구조

<img src="./images/구조.png" width="80%">

</br>

## 개발 내용

저전력 무선 센서 디바이스를 활용한 거리 측정 알고리즘을 제안한다. 

제안하는 알고리즘의 실효성을 검증하기 위해 저전력 무선 센서 디바이스 및 센서 태그 수신기를 구현한다.

</br>

- **알고리즘 개발을 위한 데이터 교정**

  <img src="./images/RSSI값.png" width="90%">

  </br>   

  

  - **노이즈 기준 설정**
    - RSSI 값 수신시 장애물, 이상치 등 노이즈로 판단되는 기준을 설정한다. RSSI 값 측정시 N회 이내에 노이즈 기준과 부합하는 값이 발생되면 해당 값의 교정은 RSSI 값 측정에 영향을 미치지 않도록 설정한다.
  - **비정상적인 값인 이상치 예외처리**
    - RSSI 수신시 비정상적인 값이 반복되어 출력될 경우 해당 값을 예외처리한다. 비정상적인 값은 음수, 0으로 설정하여 해당 값은 예외처리(제거 및 수정)한다.
  - **딜레이 구간 설정 및 평균 값 계산**
    - RSSI 값 수신시 일정한 딜레이 구간(Parameter)을 설정하여 해당 구간의 RSSI 값을 측정한 뒤 구간의 평균을 계산하여 거리 측정 값을 산출한다.  

</br>

- **알고리즘 실험** 

  <img src="./images/수신과정.png" width="60%">

  </br>

  

  - **저전력 무선 센서 디바이스(BLE Beacon) 개발**

    - 싱글보드 하드웨어인 Raspberry pi를 이용하여 저전력 무선 센서 디바이스 개발

    - 무선 센서 디바이스의 고유 ID와 RSSI 값을 이용하며 해당 디바이스의 실시간 위치 파악을 위해 사용

      </br>

  - **Sensor Tag Receiver** **개발**

    - 싱글보드 하드웨어인 Raspberry pi를 이용하여 Sensor Tag Receiver 개발

    - Sensor Tag Receiver는 무선 센서 디바이스의 위치 정보를 수신하여 무선 링크를 통해 센서의 정보를 웹 서버로 실시간 전송

      </br>

  - **Web Server** **구축**
    - 무선 센서 디바이스의 위치 정보를 저장하기 위한 데이터 베이스와 센서 디바이스 데이터 수신 및 서비스 제공을 위한 웹 서버 구축

</br>

## 진행 사항

- **2020년 10월 (진행 중)**
  - Raspberry Pi 개발환경 세팅, BLE Beacon 구현, Sensor Tag Receiver 구현
  - 수신 데이터 관리를 위한 서버 환경 구축

- **2020년 11월 (진행 예정)**
  - Bluetooth 통신 안정성 확립 및 데이터 수집
  - Receiver와의 Wi-Fi 통신 및 Server 기능 구현
  - 실험을 통한 구현 알고리즘 검증

