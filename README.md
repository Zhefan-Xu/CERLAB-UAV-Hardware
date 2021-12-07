# building_px4_quadcopter


# Hardware:
- Frame:
  - [F330](https://www.amazon.com/Quadcopter-Frame-Aircraft-Accessory-Integrated/dp/B07D6K51DY/ref=sr_1_2?keywords=f330&qid=1636421247&qsid=140-8186632-2531121&s=toys-and-games&sr=1-2&sres=B08L3JT2Q4%2CB07D6K51DY%2CB075DD16LK%2CB0824RHXZN%2CB085W3VM2K%2CB00P23TYW0%2CB08LSVCSZ4%2CB09FB1XF77%2CB017H7E3VK%2CB06ZZQL33X%2CB08PHTLFFS%2CB00YR6ZGHA%2CB00SYGBQGE%2CB09KQNQ6Z7%2CB09DK3K3HM%2CB09GN7CBT9%2CB08538X9LN%2CB08B5TQ8JL%2CB089ZDLV3K%2CB08T5VCKY1)
  - [Q250](https://hobbyking.com/en_us/hobbykingtm-totem-q250-quadcopter-kit.html)
- Onboard/Companion Computer: 
  - [DJI Manifold 2C/G](https://www.dji.com/manifold-2)
  - [Nvidia Xavier NX](https://store.nvidia.com/en-us/jetson/store/?page=1&limit=9&locale=en-us) (Currently out of stock)
- Flight controller: 
  - [PX4 Pixracer](https://docs.px4.io/v1.12/en/flight_controller/pixracer.html)
  - [CUAV Nora](https://docs.px4.io/v1.12/en/flight_controller/cuav_nora.html)
  - [PX4 Pixhawk](https://docs.px4.io/master/en/flight_controller/pixhawk4.html)
  - [Orange Cube](https://docs.px4.io/master/en/flight_controller/cubepilot_cube_orange.html)

- Telemetry Communication (companion computer with FC): 
  - [USB UART serial port converter](https://www.amazon.com/DSD-TECH-SH-U09C2-Debugging-Programming/dp/B07TXVRQ7V/ref=sr_1_3?crid=2ZVK4AYT03PDX&dchild=1&keywords=short+uart&qid=1635992461&qsid=144-8949687-4547914&sprefix=short+uart+%2Caps%2C73&sr=8-3&sres=B07J64TGS3%2CB07RBKCW3S%2CB07TXVRQ7V%2CB07R8BQYW1%2CB00LODGRV8%2CB00IJXZQ7C%2CB07D6LLX19%2CB07D9R5JFK%2CB01N47LXRA%2CB07R45QJVR%2CB00LZVEQEY%2CB08HLSS5T4%2CB075N82CDL%2CB08FBDTP5G%2CB07WX2DSVB%2CB014GZTCC6).

- LIPO Battery:
  

# Special Notes:
- Battery: 
  - Charging: charging battery MUST connect the balancer. This will cause the imbalanced voltage in each cell. See this [page](https://www.wattflyer.com/forums/showthread.php?t=31107) for details. 
  - [Voltage](https://www.quora.com/What-is-the-difference-between-the-nominal-voltage-of-3-7V-and-the-voltage-of-a-cell-of-4-2V-in-lithium-cells): 3.7V is the nominal voltage (It is the voltage for long storage).  4.2V is the full voltage. However, in QGroundControl, we can set minimum voltage to a little lower (3.5 V). That is because under load, the measured voltage will be slightly lower than we expected. Optionally, we can set the maximum voltage to a little lower (4.05 V).
  - C Rating: Simply speaking, it determines the discharge rate:
    ```
    (mAh / 1000) x C Rate = Continuous Discharge 
    Amperag (1600 / 1000) x 10 = 16A
    ```
  - Energy Density: Energy density is measured in Watt-hours per kilogram (Wh/kg)
- Compass: 
  - VIO/MoCap: If we want to use the compass as heading estimation with VIO/MoCap, after turning on the camera (e.g. RealSense T265), we need to rotate the drone until the displayed yaw is ```w=1, x=y=z=0```. See reference from the [official documentation](https://docs.px4.io/master/en/ros/external_position_estimation.html) and [github issue](https://github.com/Auterion/VIO/issues/16#issuecomment-856809595).
  - How to correct [calibrate](https://docs.px4.io/master/en/config/compass.html) compass: You will need to calibrate your compass on first use, and you may need to recalibrate it if the vehicles is ever exposed to a very strong magnetic field, or if it is used in an area with abnormal magnetic characteristics.Also, please calibrate away from any metal (Metal is not always obvious! Avoid calibrating on top of an office table (often contain metal bars) or next to a vehicle. Calibration can even be affected if you're standing on a slab of concrete with uneven distribution of re-bar)



- Telemetry: 
  - Baudrate: USB connection can provide a higher [baudrate](https://learn.sparkfun.com/tutorials/serial-communication/rules-of-serial#:~:text=One%20of%20the%20more%20common,fast%20data%20can%20be%20transferred.) which determines the data transmission rate. The default baudrate of MAVLINK is 921600, but DJI manifold uart0 can only support up to 115200. Note the data frequency of ```mavros/local_position/pose``` should be ~30hz for a reasonable communication configuration.
- ESC [wiring](https://docs.px4.io/master/en/peripherals/pwm_escs_and_servo.html) & [protocal & firmware](https://oscarliang.com/esc-firmware-protocols/) & [calibration](https://docs.px4.io/master/en/advanced_config/esc_calibration.html):
  - Wiring： battery wire & Servo wire (PWM (color) and GND (black))
  - Communication Protocal: In short, Dshot is the best and latest protocal. From early to latest, we have PWM (1-2 ms latency), Oneshot (0.125-0.25 ms latency), Dshot (less than 0.1 ms latency). 
  - ESC firmware: Common firmware: BLHeli, BLHeli_S, BLHeli_32, SimonK, KISS. BLHeli_S and BLHeli_32 are todays' most common used one 
  - Purpose for calibration: ESC calibration is actually to find the Minimum&maximum PWM (Pulse-width modulation) value for the flight controller based purely on the battery. It does not require ESC! It is actually a calibration for controller based on battery. After calibration, the parameter related MAX/MIN_PWM is changed.
- T265:
  - Facing downward by a certain angle (e.g. 30 - 60 degree) can help increase feature and prevent from view block.
- Calibration:
- [CUAV Nora](https://docs.px4.io/v1.12/en/flight_controller/cuav_nora.html):
  - Power A and Power C: Power A is common adc interface, Power C is uavcan battery interface. We should use power C instead of Power A because we use its CAN PMU SE so it support UAVCAN. Also, as mention in their [wiring instruction](https://doc.cuav.net/flight-controller/x7/en/quick-start/quick-start-nora.html), all the parameters have been preconfigured (there is no need to do calibration and change parameter. The minmum voltage is 3.5V and maximum volrage is 4.2 V.


# Unsolved Problems:
- T265 boot problem: replug first time.
- HARDWARE_CLOCK. 
- DJI manifold freezes after running octomap and replug in T265. (TO test)
- Latency in WIFI transmission. Sometimes automatically disconnected. WIFI lost. 
- Propeller Guard??

# Solved Problems:
- Battery display problem: always 100% (see Nora notes)
- Minimum Thottle too high. (PWM_MAIN_MIN/MAX)
- Warning: sdk version does not match. (Reinstall)
- USB cable warning: 2.0 and 3.0. (Battery power usb hub)


# TODO List:
1. Solve the above problems.
2. Test current design
3. Build the second drone

# Date: 12/07
1. Extend camera mount.
2. Test octomap and wifi. (Check nora QGC)
3. Manuel test.
4. Transform tool.
(5). WIFI
(6). T265
(7) HARDWARE_CLOCK
