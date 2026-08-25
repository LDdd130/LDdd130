<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:1F6FEB,100:8250DF&height=105&section=header" width="100%" alt="Header wave"/>

<img src="./asset/profile_header.svg" width="100%" alt="LEE JAEUN — firmware, embedded, RTL profile header"/>

<br/>

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&pause=1100&color=58A6FF&center=true&vCenter=true&width=760&lines=STM32+%2F+AVR+firmware;FreeRTOS+%2F+bare-metal+scheduling;Verilog+RTL+%2F+AXI4-Lite+%2F+MicroBlaze;Timers+%2F+interrupts+%2F+state+machines" alt="Firmware and RTL topics"/>

<br/>

<p><strong>센서를 읽고, 시간을 맞추고, 상태를 나눠 실제 하드웨어를 움직이는 코드를 작성합니다.</strong></p>

<p>STM32·AVR 펌웨어와 Verilog RTL을 주로 다룹니다.<br/>
동작 영상, 구조도, 구현 내용과 확인된 제한 사항은 각 프로젝트 README에 기록했습니다.</p>

</div>

---

## `toolbox`

### Firmware

<p>
  <img src="https://skillicons.dev/icons?i=c&theme=dark" height="36" alt="C"/>
  &nbsp;
  <img src="https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" height="36" alt="STM32"/>
  &nbsp;
  <img src="https://img.shields.io/badge/FreeRTOS-3C9C35?style=for-the-badge&logo=freertos&logoColor=white" height="36" alt="FreeRTOS"/>
  &nbsp;
  <img src="https://img.shields.io/badge/ATmega128A-C4001D?style=for-the-badge&logo=microchip&logoColor=white" height="36" alt="ATmega128A"/>
</p>

### RTL / SoC

<p>
  <img src="https://img.shields.io/badge/Verilog_HDL-1E4C8A?style=for-the-badge" height="36" alt="Verilog HDL"/>
  &nbsp;
  <img src="https://img.shields.io/badge/Artix--7-E01F27?style=for-the-badge&logo=amd&logoColor=white" height="36" alt="Artix-7"/>
  &nbsp;
  <img src="https://img.shields.io/badge/MicroBlaze_RISC--V-0071C5?style=for-the-badge&logo=amd&logoColor=white" height="36" alt="MicroBlaze RISC-V"/>
  &nbsp;
  <img src="https://img.shields.io/badge/Vivado_%2F_Vitis-E01F27?style=for-the-badge&logo=amd&logoColor=white" height="36" alt="Vivado and Vitis"/>
</p>

### Tools / Host

<p>
  <img src="https://skillicons.dev/icons?i=python,cmake,git,github,vscode&theme=dark" height="36" alt="Python, CMake, Git, GitHub and VS Code"/>
  &nbsp;
  <img src="https://img.shields.io/badge/STM32CubeIDE-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" height="36" alt="STM32CubeIDE"/>
  &nbsp;
  <img src="https://img.shields.io/badge/PySide6-41CD52?style=for-the-badge&logo=qt&logoColor=white" height="36" alt="PySide6"/>
</p>

---

## `workbench`

```text
firmware  Timer · ISR · peripheral driver · FreeRTOS task
control   Sensor · motor · servo · watchdog
rtl       Synchronous logic · AXI4-Lite · testbench
host      UART protocol · telemetry · PySide6 dashboard
```

---

## `projects`

| Project | 구현 내용 | Stack |
|:--|:--|:--|
| [**PR_CAR**](https://github.com/LDdd130/PR_CAR) | SensorTask → 값 복사 큐 → MotorTask 구조의 RC카. ToF·IMU·엔코더를 주행 입력으로 사용하고, 신선한 센서 프레임 수신 시에만 IWDG 갱신 | `STM32F411CEU6` `FreeRTOS` `C` |
| [**Mission SoC**](https://github.com/LDdd130/SOC_Project) | `heartbeat_monitor → fault_manager → safety_controller` Custom IP 연결. MicroBlaze는 설정·IRQ 수집, PySide6는 모니터링 담당 | `Basys 3` `Verilog` `C` `Python` |
| [**MimicArm**](https://github.com/LDdd130/MimicArm) | Teach & Playback 로봇 팔. D-FF 자세 저장, ±1° 증분 보간, 상수·곱셈 기반 서보 PWM | `Artix-7` `Verilog` |
| [**Smart Fan**](https://github.com/LDdd130/Smart_Fan) | DHT11 팬 듀티, 조이스틱 2축 서보, UART 카운트다운을 Timer2 기반 협력식 주기 실행으로 구성 | `ATmega128A` `C` `CMake` |
| [**Elevator On-Device**](https://github.com/LDdd130/Elevater) | 초음파 2채널 층 판정, 문 인터록, 스텝모터 이동, Bluetooth 층 호출 | `STM32F411RE` `HAL` `C` |

<br/>

<div align="center">

<a href="https://github.com/LDdd130">
  <img src="https://img.shields.io/badge/GitHub-LDdd130-0D1117?style=for-the-badge&logo=github&logoColor=white" alt="LDdd130 GitHub profile"/>
</a>

<br/><br/>

<sub>프로젝트 설명과 수치는 각 저장소의 소스 및 설정값을 기준으로 작성했습니다.</sub>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:1F6FEB,100:8250DF&height=110&section=footer" width="100%" alt="Footer wave"/>

</div>
