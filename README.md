# Testing Logfiles

This repository contains logfiles from EVerest charging session on different hardware with real cars.
Usually it includes EVerest session logs, tcp dumps as well as OCPP logs (if it was used).
This repository does not include all cars tested with EVerest, but only log files from dedicated test events at Pionix.
Charging sessions were performed with EvseV2G module as HLC implementation unless otherwise noted in the foldername.
Qualcomm QCA7k was used as PLC unless noted (some are with Lumissil CG5317).

Legend:

:heavy_check_mark: works correctly, logs included in case of HLC

❌ supported by car but not working with EVerest

:black_square_button: not supported by car

🔄 supports (unofficially) bidirectional charging with EVerest energy manager (limits given in table)

❓ no logfiles in this repository or support unknown

## Fully electric vehicles (European markets)

|     | Manufacturer  | Model, fw version           | AC BASIC                                      | DIN SPEC 70121 DC                                                | ISO15118-2 DC                             | ISO15118-2 AC                   | Comments                                                                                                                                  |
| --- | ------------- | --------------------------- | --------------------------------------------- | ---------------------------------------------------------------- | ----------------------------------------- | ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | VW            | id.buzz fw 3.2              | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:🔄(up to 60 seconds)                           | ❓                                        | ❓                              | random MAC, 60s timeout in CurrentDemand                                                                                                  |
| 2   | VW            | id.4 PRO fw 2.3.0           | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:🔄(up to 60 seconds)                           | :heavy_check_mark:🔄(up to 60 seconds)    | :heavy_check_mark:              | random MAC, 60s timeout in CurrentDemand                                                                                                  |
| 3   | VW            | id.4 fw 3.5                 | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | :heavy_check_mark:                        | :heavy_check_mark:              | random MAC, 60s timeout in CurrentDemand                                                                                                  |
| 4   | VW            | id.3 pure fw 0561           | :heavy_check_mark: 2ph/16A                    | :heavy_check_mark:🔄(up to 60 seconds)                           | :heavy_check_mark:🔄(up to 60 seconds)    | :heavy_check_mark:              | random MAC, 60s timeout in CurrentDemand                                                                                                  |
| 5   | Skoda         | Enyaq fw 3.0                | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark: 🔄(up to 60 seconds)                          | ❓🔄(up to 60 seconds)                    | :heavy_check_mark:              | random MAC, 60s timeout in CurrentDemand                                                                                                  |
| 6   | BMW           | iX fw 11/2022.64            | :heavy_check_mark: 3ph/32A                    | :heavy_check_mark:🔄(up to 5 minutes)                            | :heavy_check_mark:🔄(up to 5 minutes)     | ❓                              |                                                                                                                                           |
| 7   | BMW           | iX                          | :heavy_check_mark: 3ph/32A                    | :heavy_check_mark:                                               | :black_square_button:                     | ❓                              | probably older car FW                                                                                                                                           |
| 8   | BMW           | i4                          | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | ❓                                        | ❓                              |                                                                                                                                           |
| 9   | Tesla         | Model Y v11.1(2023.6.8)     | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:🔄(limited to about 5kWh)                      | :black_square_button:                     | :black_square_button:           |                                                                                                                                           |
| 10  | Tesla         | Model 3                     | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:🔄(limited to about 5kWh)                      | :black_square_button:                     | :black_square_button:           |                                                                                                                                           |
| 11  | Hyundai       | Kona 2017                   | :heavy_check_mark: 1ph/32A                    | :heavy_check_mark:🔄                                             | :black_square_button:                     | :black_square_button:           |                                                                                                                                           |
| 12  | Hyundai       | Ioniq 5                     | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:🔄(verified 63% to 36%)                        | :heavy_check_mark:🔄                      | :black_square_button:           |                                                                                                                                           |
| 13  | Kia           | EV6                         | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:🔄(verified 35% to 20%)                        | :heavy_check_mark:🔄                      | :black_square_button:           |                                                                                                                                           |
| 14  | Opel          | Corsa-e                     | :heavy_check_mark: 3ph/16A                    | ❓🔄                                                             | :black_square_button:                     | :black_square_button:           | Charger fw crashes with ISO-2 AC                                                                                                          |
| 15  | Opel          | Ampera-e                    | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | :black_square_button:                     | :black_square_button:           |                                                                                                                                           |
| 16  | Opel          | Mokka-e 42.03.31.32_NAC-r0  | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | :heavy_check_mark:                        | :black_square_button:           |                                                                                                                                           |
| 17  | Renault       | Zoe 1 (43kW AC OBC version) | :heavy_check_mark: 3ph/63A                    | :black_square_button:                                            | :black_square_button:                     | :black_square_button:           | high DC residual current, >10mA                                                                                                           |
| 18  | Renault       | Zoe Z50 R135 | ❓ (not tested)                   | heavy_check_mark:                                            | :black_square_button:                     | :black_square_button:           |                                                                              |
| 19  | Nissan        | NV200 (old Chademo version) | :heavy_check_mark: 3ph/16A                    | :black_square_button:                                            | :black_square_button:                     | :black_square_button:           | Chademo not supported with EVerest yet                                                                                                    |
| 20  | Polestar      | Polestar 2 78kWh fw P2.7    | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:🔄 (verified 80% to 20%)                       | :heavy_check_mark:🔄 (verified 80% to 20%)| :black_square_button:           | ISO-2 AC: Car selects AC_single_phase_core and stops after ChargeParameterDiscoveryRes                                                    |
| 21  | Porsche       | Taycan                      | :heavy_check_mark: 3ph/16A or 32A, both sides | :heavy_check_mark: 🔄(up to 30 seconds)                          | :heavy_check_mark:                        | :heavy_check_mark: (both sides) | DC: <20s timeout in CableCheck, 30s timeout in CurrentDemand<br>Tested model had only AC port on drivers side and 800VDC+AC on other side |
| 22  | Mercedes-Benz | EQC                         | :heavy_check_mark: 3ph/16A or 32A             | :heavy_check_mark: 🔄(limited to approx 3.6kW, stops after 5 min)| :black_square_button:                     | :black_square_button:           | Discharging more then 3.6kW: car tries to limit discharging and eventually stops                                                          |
| 23  | Mercedes-Benz | EQE                         | :heavy_check_mark: 3ph/16A or 32A             | :heavy_check_mark:                                               | :heavy_check_mark:                        | :heavy_check_mark:              |                                                                                                                                           |
| 24  | BYD           | Atto 3                      | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | :heavy_check_mark:                        | :black_square_button:           |                                                                                                                                           |
| 25  | Subaru        | Solterra                    | :heavy_check_mark: 3ph/16A or 3ph/32A         | :heavy_check_mark:                                               | :heavy_check_mark:                        | :black_square_button:           |
| 26  | MG            | MG4 electric                | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | :heavy_check_mark:                        | :black_square_button:           |
| 27  | Audi          | Q4                          | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | :heavy_check_mark:                        | :heavy_check_mark:              |
| 28  | Xpeng         | P7 performance              | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | :heavy_check_mark:                        | :black_square_button:           |
| 29  | Seres         | Seres 3                     | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | :heavy_check_mark:                        | :black_square_button:           | On AC ISO15118-2, the EV sends a CableCheck req in AC    |
| 30  | Citroen       | EC4                         | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | :heavy_check_mark:                        | :black_square_button:           |
| 31  | Fiat          | Scudo                       | :heavy_check_mark: 3ph/16A                    | :heavy_check_mark:                                               | :heavy_check_mark:                        | ❓                              |


## Plug in hybrid vehicles (European markets)
|     | Manufacturer | Model, fw version            | AC BASIC                   | DIN SPEC 70121 DC     | ISO15118-2 DC         | ISO15118-2 AC         | Comments                                                               |
| --- | ------------ | ---------------------------- | -------------------------- | --------------------- | --------------------- | --------------------- | ---------------------------------------------------------------------- |
| 32  | Hyundai      | Hyundai Ioniq plug in hybrid | :heavy_check_mark: 1ph/14A | :black_square_button: | :black_square_button: | :black_square_button: | Charger stops if 5% PWM presented and does not recover until replugged |

## Prototype cars (Charin Testival Arnhem April 2023)

EVerest is tested on prototype cars or series cars with unreleased firmware versions on testivals in regular intervals (e.g. organized by Charin e.V.). The logfiles of these tests are not published here. Test results for unreleased features (e.g. PnC, ISO-20) are also not published.

|     | Manufacturer  | Model, fw version | AC BASIC                   | DIN SPEC 70121 DC  | ISO15118-2 DC      | ISO15118-2 AC         | Comments |
| --- | ------------- | ----------------- | -------------------------- | ------------------ | ------------------ | --------------------- | -------- |
| 33  | Lotus         | Prototype         | :heavy_check_mark: 3ph/16A | :heavy_check_mark: | :heavy_check_mark: | :black_square_button: |          |
| 34  | Lucid         | Prototype         | :heavy_check_mark: 3ph/16A | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:    |          |
| 35  | Renault       | Prototype         | :heavy_check_mark: 3ph/16A | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:    |          |
| 36  | Hyundai       | Prototype 1       | :heavy_check_mark: 3ph/16A | :heavy_check_mark: | :heavy_check_mark: | :black_square_button: |          |
| 37  | Hyundai       | Prototype 2       | :heavy_check_mark: 3ph/16A | :heavy_check_mark: | :heavy_check_mark: | :black_square_button: |          |
| 38  | Mercedes-Benz | Prototype 1       | :heavy_check_mark: 3ph/16A | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:    |          |
| 39  | Volvo         | Prototype 1       | :heavy_check_mark: 3ph/16A | :heavy_check_mark: | :heavy_check_mark: | :black_square_button: |          |
| 40  | Volvo         | Truck Prototype 2       | :heavy_check_mark: 3ph/63A | :heavy_check_mark: | :heavy_check_mark: | :black_square_button: |          |
| 41  | Scania        | Truck Prototype 1       | :black_square_button:      | :heavy_check_mark: | :heavy_check_mark: | :black_square_button: |          |


