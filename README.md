# 🚌 서울시내버스 운행기록 프로그램 (Seoul_Bus_Drive_Recorder)
<br>

> [!CAUTION]
> **<ins>주의 : 이 프로그램을 사용하기 위해서는 반드시 공공데이터포털</ins> (https://www.data.go.kr) <ins>OPEN API 사용신청을 해야합니다.</ins>**
<br>

## 📥 다운로드 및 설치

* 💻 **Windows :** [EXE 파일 다운로드 (v1.15)](https://github.com/ggoyong2-ctrl/Bus_Recorder/releases/download/Downloads/Seoul_Bus_Drive_Recorder_v1_15.exe)
* 🍎 **macOS :** [ZIP 파일 다운로드 (v1.15)](https://github.com/ggoyong2-ctrl/Bus_Recorder/releases/download/Downloads/Seoul_Bus_Drive_Recorder_v1_15.macOS.zip)
#### 🛠️ macOS 사용자 필수 설정 안내
macOS 환경에서는 보안 설정(Gatekeeper)으로 인해 앱 실행 시 권한 허용이 필요합니다. 아래 두 가지 단계를 꼭 진행해 주세요.

**(1) 앱 실행 권한 격리 속성 제거**
터미널(Terminal)을 열고 아래 명령어를 입력합니다. (`/app_file 경로` 부분은 지우고, 다운받은 앱 파일을 터미널 창에 드래그 앤 드롭하면 경로가 자동 입력되어 편리합니다.)
```bash
xattr -d com.apple.quarantine /app_file 경로
```
**(2) 맥os operation not permitted 에러 해결**
시스템설정 ➔ 개인정보 보호 및 보안 ➔ 전체 디스크 접근 권한 ➔ +버튼 클릭 ➔ Seoul_Bus_Drive_Recorder_v1.09.app 적용
<br>

## 📖 사용 방법

**1.** 🔑 공공데이터포털에서 발급받은 **인증키를 프로그램에 입력**합니다.
**2.** 🚌 기록하고자 하는 **노선 검색 및 노선 설정**을 진행합니다.
**3.** ▶️ **[기록 시작]** 버튼을 클릭합니다.
**4.** 📡 해당 노선의 운행 출발과 운행 종료 데이터를 프로그램이 **자동으로 수집**합니다.
**5.** 📊 실행 파일이 위치한 경로에 저장된 **엑셀 파일을 확인 및 사용**합니다.
**6.** ⏻ 프로그램을 종료하면 **모든 작동 및 데이터 기록이** <ins>**중단**</ins>됩니다.
<br>

## 👨‍💻 소스 코드 및 일러두기

* 🐍 **파이썬 코드 :** Seoul_Bus_Drive_Recorder_v1_15.py [소스코드 보러가기](https://github.com/ggoyong2-ctrl/Bus_Recorder/blob/main/Seoul_Bus_Drive_Recorder_v1_15.py)
> 💡 **개발자 코멘트**
> 저는 프로그래밍 전문가가 아니라, 평범한 시내버스 운전직 노동자입니다. 현업에서 필요성을 느껴 Claude와 Gemini AI의 도움을 받아 작성한 코드이기에, 얼마든지 오류나 버그가 존재할 수 있습니다. **<ins>자유롭게 본인의 필요에 맞게 이 코드를 수정해서 쓰셔도 됩니다.</ins>** 여러분의 업무에 작은 도움이라도 되기를 바랍니다!
<br>

## 🔑 인증키 발급 및 Open API 사용신청 방법

**1.** 공공데이터포털 (https://www.data.go.kr) 에서 회원가입을 진행해주세요.

**2.** 아래 페이지에 각각 접속하여 API 활용신청을 하면, 인증키가 발급됩니다.
* **인증키 확인방법:** 로그인 ➔ 마이페이지 ➔ 개인 API인증키
* ⚠️ **참고:** 발급된 인증키는 보통 매주 월요일에 사용 승인됩니다. (사용 승인되기 전에는 발급된 인증키를 입력하더라도 사용 불가)

  * 📌 서울특별시_버스도착정보조회 서비스: https://www.data.go.kr/data/15000314/openapi.do
  * 📌 서울특별시_정류소정보조회 서비스: https://www.data.go.kr/data/15000303/openapi.do
  * 📌 서울특별시_버스위치정보조회 서비스: https://www.data.go.kr/data/15000332/openapi.do
  * 📌 서울특별시_노선정보조회 서비스: https://www.data.go.kr/data/15000193/openapi.do

**3.** 각각의 API 호출명 당 일일 **1,000 트래픽**이 부여됩니다.

* 호출명 당 1,000건의 제한은 이 프로그램을 사용하는데 다소 부족할 수 있습니다. 
* 데이터 갱신 주기를 약 70초 내외로 느리게 설정하면 1,000건 이내에서 1개 노선의 하루 데이터를 받을 수 있습니다.
* 갱신주기가 70초라면 실제의 차량의 움직임과 데이터 간의 오차는 최대 70초가 되겠습니다.
* 70초 이내에 출발을 판정하는 최초 2개의 정류소를 모두 통과해서 3번째 정류소에 이미 도착했다면 데이터 누락 가능성이 존재합니다.

**4.** 오픈소스로 공개해드린 파이썬 코드를 참고하여 자신만의 프로그램을 새롭게 작성하신 경우, 본인의 프로그램을 활용사례로 신청하시면 각각의 API 호출명 당 일일 트래픽이 **10,000건**으로 상향됩니다.
* 10,000건이면 여러 노선을 하루종일 촘촘하게, 적은 오차값으로 모니터링 가능합니다.

**5.** API 호출 트래픽이 부족할 때, **트래픽 상향을 위한 활용사례 신청 방법**
> 공공데이터포털 (https://www.data.go.kr) 로그인 ➔ 마이페이지 ➔ 데이터 활용 ➔ Open API ➔ 활용신청 현황 ➔ 각각 활용신청 했던 서비스 클릭 ➔ **활용신청 버튼** ➔ 본인의 활용 사례 입력 (개발한 프로그램 스크린샷, 사이트 주소 등)

<br>

## 🔄프로그램 작동 원리

```text
http://ws.bus.go.kr/api/rest/buspos/getBusPosByRtid?ServiceKey=[ 인증키 ]&busRouteId=100100389

출발판정용 API 호출 및 응답 예시, 서울광역버스 9401번 
(100100389 : 9401번 노선의 아이디)

상기 페이지를 호출해서 <lastStnId>값이 첫번째 혹은 두번째정류소 ID라면 운행시작으로 판단

<itemList>
    <busType>0</busType>                    (저상여부)
    <congetion>41</congetion>               (혼잡도)
    <dataTm>20260326103621</dataTm>         (API서버에서 데이터를 보내온 시각)
    <fullSectDist>1.011</fullSectDist>      (다음 정류소까지의 거리 km)
    <gpsX>127.108866</gpsX>                 (경도좌표)
    <gpsY>37.340015</gpsY>                  (위도좌표)
    <isFullFlag>0</isFullFlag>              (만차여부)
    <islastyn>0</islastyn>                  (막차여부)
    <isrunyn>1</isrunyn>                    (운행여부)
    <lastStTm>8756</lastStTm>               (운행종료까지 예상소요시간)
    <lastStnId>206000498</lastStnId>        (마지막통과정류소, 구미동차고지앞 07476)
    <nextStId>206000245</nextStId>          (다음정류소, 성우스타우스 47167)
    <nextStTm>1062</nextStTm>               (다음정류소까지 예상소요시간)
    <plainNo>서울74사2186</plainNo>          (버스번호)
    <posX>209645.78913126272</posX>         (맵매칭X좌표 GRS80)
    <posY>426761.506289626</posY>           (맵매칭Y좌표 GRS80)
    <rtDist>72.36</rtDist>                  (노선 총 연장 km)
    <sectDist>0.667</sectDist>              (이전 정류소에서 이동한 거리 km)
    <sectOrd>1</sectOrd>                    (통과한 정류소의 정류소 순번)
    <sectionId>206900793</sectionId>        (구간 ID)
    <stopFlag>0</stopFlag>                  (정류소정차여부)
    <trnstnid>101000005</trnstnid>          (회차지 정류소 ID)
    <vehId>107017461</vehId>                (차량 ID)
</itemList>
```

```text
http://ws.bus.go.kr/api/rest/buspos/getBusPosByRouteSt?ServiceKey=[ 인증키 ]&busRouteId=100100022&startOrd=1&endOrd=113

도착판정용 API 호출 및 응답 예시, 서울시내버스 143번 
(100100022 : 143번 노선의 아이디, startOrd=1 첫정류소순번, endOrd=113 마지막정류소 순번 - 143번은 113번째 정류소에서 운행종료)

상기 페이지를 호출해서 <lastStnId>값이 마지막정류소 ID라면 운행종료로 판단

<itemList>
    <busType>1</busType>                    (저상여부)
    <congetion>0</congetion>                (혼잡도)
    <dataTm>20260326102405</dataTm>         (API서버에서 데이터를 보내온 시각)
    <isFullFlag>0</isFullFlag>              (만차여부)
    <lastStnId>107000246</lastStnId>        (마지막통과정류소, 대진여객차고지 08344)
    <plainNo>서울74사3382</plainNo>          (버스번호)
    <posX>200070.35528265714</posX>         (맵매칭X좌표 GRS80)
    <posY>457570.75495593995</posY>         (맵매칭Y좌표 GRS80)
    <routeId>100100022</routeId>            (노선 ID)
    <sectDist>342</sectDist>                (이전 정류소에서 이동한 거리 m)
    <sectOrd>113</sectOrd>                  (통과한 정류소의 정류소 순번)
    <sectionId>107702001</sectionId>        (구간 ID)
    <stopFlag>0</stopFlag>                  (정류소정차여부)
    <tmX>127.000797</tmX>                   (경도좌표)
    <tmY>37.617689</tmY>                    (위도좌표)
    <vehId>107012142</vehId>                (차량 ID)
</itemList>
```

<br>

## 📊 저장되는 엑셀 데이터 예시
<img width="947" height="1392" alt="2026-03-26 10 02 58" src="https://github.com/user-attachments/assets/5a48dd50-391c-4e3e-a524-c0f55fc3e0b1" />
<br>

## 💻 윈도우11 작동 스크린샷
<img width="1352" height="1032" alt="2026-03-26 08 21 47" src="https://github.com/user-attachments/assets/1e483ffd-b6f0-4f4c-9a85-ec75bee07af0" />
<img width="1352" height="1032" alt="2026-03-26 08 22 06" src="https://github.com/user-attachments/assets/7d1cceff-f590-4361-ae9b-0b1257b4b27d" />
<img width="1352" height="1032" alt="2026-03-26 08 22 23" src="https://github.com/user-attachments/assets/bf137721-60e8-4005-9010-4fc9ba8489c4" />
<img width="1352" height="1032" alt="2026-03-26 08 22 40" src="https://github.com/user-attachments/assets/6341062f-408d-46ca-aefa-b6ff25ccd3c2" />
<img width="1352" height="1032" alt="2026-03-26 08 22 59" src="https://github.com/user-attachments/assets/4c8d1ddb-963c-401c-a21a-2907d118226c" />
<br>

## 💻 macOS 작동 스크린샷
<img width="1353" height="876" alt="2026-03-26 08 20 11" src="https://github.com/user-attachments/assets/913a4190-556a-426b-af2e-01eec9144e8c" />
