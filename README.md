# my-c-side

ATmega128 MCU와 PC 간의 시리얼 통신을 기반으로 날씨 정보와 시간 정보를 LCD에 출력하는 미니프로젝트

---

## 폴더 구조

```plaintext
my-c-side/
├── mcu-src/          # MCU에서 작동할 C 코드 (main.c 포함)
│   └── lib/          # UART, LCD 제어 코드
├── pc-tools/         # PC에서 날씨, 시간을 가져오는 코드 (weather_sender.c, time_sender.c)
├── sql/
│   ├── table.sql     # MySQL에서 UserInfo 테이블 생성용 스크립트
│   └── weather.sql   # WeatherDB 생성, 사용자 권한 설정 스크립트
├── platformio.ini    # MCU 빌드 설정 파일
└── README.md
```

---

## 주요 기능

- PC에서 실시간 시간, 날씨 정보를 받아와 시리얼 통신으로 MCU에 전송
- ATmega128 보드에서 수신한 데이터를 LCD에 출력
- I2C, UART, LCD, SQLite, OpenWeatherMap API 사용

---

## 실행하는 방법

### 먼저 PC 코드 2개 실행 후 MCU 프로그램 빌드 및 업로드

- gcc time_sender.c -o time_sender `mysql_config --cflags --libs`
- ./time_sender
- gcc pc-tools/weather_sender.c -o weather_sender
- ./weather_sender
