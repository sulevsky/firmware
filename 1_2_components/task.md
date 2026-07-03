Завдання
•⁠  ⁠Ознайомитись із взаємодією компонентів:
    * VTX (відеопередавач)
    * FC (flight controller)
    * ESC (регулятор обертів)
    * ELRS (радіоприймач)
    * CAM (камера)
    * MOTOR (двигуни)

Скласти план підключення (послідовність сигналів і протоколів)

•⁠  ⁠CAM → FC
    * Відеосигнал (Analog Video)
    * Протокол: аналоговий (CVBS)
    * CAM Video → FC Video IN
•⁠  ⁠FC → VTX
    * Відеосигнал після OSD
    * Протокол: аналоговий (CVBS)
    * FC Video OUT → VTX Video IN
•⁠  ⁠FC → VTX (керування)
    * Протокол: SmartAudio / Tramp
    * UART (TX пін FC → RX VTX)
•⁠  ⁠ELRS (RX) → FC
    * Протокол: CRSF (Crossfire)
    * UART:
        * RX ELRS → TX FC
        * TX ELRS → RX FC
•⁠  ⁠FC → ESC
    * Сигнали керування моторами
    * Протокол:
        * DShot300 / DShot600 (найчастіше)
    * PWM виходи (Motor 1–4)
•⁠  ⁠ESC → MOTOR
    * Живлення + фази двигуна
    * Протокол: не використовується (пряме керування фазами)
•⁠  ⁠ESC → FC (телеметрія, опційно)
    * Протокол: ESC Telemetry
    * Один провід → UART RX FC
•⁠  ⁠Живлення
    * Акумулятор → ESC (VBAT)
    * ESC → FC (5V / VBAT залежно від плати)
    * FC → ELRS, CAM, VTX (5V / 9V BEC)

Приклад послідовності роботи

•⁠  ⁠ELRS отримує команди → передає по CRSF (UART) у FC
•⁠  ⁠FC обробляє → генерує сигнали DShot → ESC
•⁠  ⁠ESC керує моторами
•⁠  ⁠Камера передає відео → FC (OSD накладається) → VTX
•⁠  ⁠VTX передає відео на окуляри

Опційно

•⁠  ⁠Додати:
    * SmartAudio для зміни каналу VTX
    * Телеметрію ESC
    * Blackbox (логування у FC)

