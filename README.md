<p align="center">
  <img src="./asset/profile_header.svg" width="100%"
       alt="LDdd130 — STM32F4, ATmega128A, Artix-7을 다루는 firmware, embedded, RTL 개발자 프로필">
</p>

<p align="center">
  <code>C</code>&nbsp;&nbsp;
  <code>Verilog HDL</code>&nbsp;&nbsp;
  <code>FreeRTOS</code>&nbsp;&nbsp;
  <code>STM32</code>&nbsp;&nbsp;
  <code>AVR</code>&nbsp;&nbsp;
  <code>FPGA</code>
</p>

센서를 읽고, 시간을 맞추고, 상태를 나눠 실제 하드웨어를 움직이는 코드를 작성합니다.  
STM32·AVR 펌웨어와 Verilog RTL을 주로 다룹니다.

동작 영상, 구조도, 구현 세부사항과 확인된 제한 사항은 각 프로젝트 README에 정리했습니다.

## Stack

```text
target      STM32F411 · ATmega128A · Artix-7 / Basys 3 · MicroBlaze
language    C · Verilog HDL · Python
runtime     FreeRTOS / CMSIS-RTOS2 · bare metal
peripheral  UART · I²C / TWI · ADC · PWM · Timer Input Capture · 1-Wire · GPIO
tooling     STM32CubeIDE · Vivado / Vitis · CMake · arm-none-eabi-gcc · avr-gcc · Git
```

## Projects

### [01. PR_CAR](https://github.com/LDdd130/PR_CAR)

`STM32F411CEU6` `FreeRTOS` `C`

복도형 트랙을 주행하는 RC카 펌웨어입니다.

- `SensorTask → value-copy queue → MotorTask`로 측정과 모터 출력을 분리했습니다.
- 전방 초음파, 좌우 ToF, IMU, 엔코더를 주행 상태 머신의 입력으로 사용합니다.
- 신선한 센서 프레임을 받은 경우에만 IWDG를 갱신합니다.

### [02. SOC_Project](https://github.com/LDdd130/SOC_Project)

`Basys 3` `Verilog` `MicroBlaze RISC-V` `C` `PySide6`

Heartbeat 감시와 고장 대응을 Custom IP로 구성한 FPGA SoC입니다.

- `heartbeat_monitor → fault_manager → safety_controller`를 RTL 신호로 직접 연결했습니다.
- MicroBlaze는 설정과 IRQ 수집, PC 대시보드는 모니터링과 명령을 담당합니다.
- 안전 상태 전이는 CPU나 UART 동작 여부와 분리했습니다.

### [03. MimicArm](https://github.com/LDdd130/MimicArm)

`Artix-7` `Verilog` `Vivado`

보드 입력으로 자세를 저장하고 재생하는 Teach & Playback 로봇 팔입니다.

- 자세 8개를 `25-bit × 8` D-FF 레지스터 뱅크에 저장합니다.
- 현재 각도를 목표 각도에 ±1°씩 접근시켜 나눗셈 없이 보간합니다.
- 서보 PWM도 미리 계산한 상수와 곱셈으로 변환합니다.

### [04. Smart_Fan](https://github.com/LDdd130/Smart_Fan)

`ATmega128A` `C` `CMake` `avr-gcc`

DHT11, 조이스틱, 서보, UART 타이머를 묶은 선풍기 제어기입니다.

- 온습도로 팬 듀티를 계산하고 목표값까지 단계적으로 변경합니다.
- Timer2 ISR와 `system_millis`를 기준으로 센서·팬·서보·카운트다운 작업을 나눴습니다.
- Timer1의 OC1A는 팬, OC1B는 수평 서보가 공유합니다.

### [05. Elevator On-Device](https://github.com/LDdd130/Elevater)

`STM32F411RE` `C` `STM32 HAL`

물리 버튼과 Bluetooth 호출을 받는 3층 엘리베이터 모형 제어기입니다.

- TIM3 Input Capture 초음파 2채널로 실제 층 도착을 판정합니다.
- 문이 닫힌 뒤에만 이동을 시작하도록 서보 상태 머신과 인터록을 구성했습니다.
- 스텝모터·문·부저는 HAL tick 기반으로 처리하고, Bluetooth 수신은 USART1 인터럽트를 사용합니다.

---

<sub>프로젝트 설명과 수치는 각 저장소의 소스 및 설정값을 기준으로 작성했습니다.</sub>
