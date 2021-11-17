# building_px4_quadcopter


# Hardware:
- Frame:
  - [F330](https://www.amazon.com/Quadcopter-Frame-Aircraft-Accessory-Integrated/dp/B07D6K51DY/ref=sr_1_2?keywords=f330&qid=1636421247&qsid=140-8186632-2531121&s=toys-and-games&sr=1-2&sres=B08L3JT2Q4%2CB07D6K51DY%2CB075DD16LK%2CB0824RHXZN%2CB085W3VM2K%2CB00P23TYW0%2CB08LSVCSZ4%2CB09FB1XF77%2CB017H7E3VK%2CB06ZZQL33X%2CB08PHTLFFS%2CB00YR6ZGHA%2CB00SYGBQGE%2CB09KQNQ6Z7%2CB09DK3K3HM%2CB09GN7CBT9%2CB08538X9LN%2CB08B5TQ8JL%2CB089ZDLV3K%2CB08T5VCKY1)
  - [Q250](https://hobbyking.com/en_us/hobbykingtm-totem-q250-quadcopter-kit.html)
- Onboard/Companion Computer: 
  - [DJI Manifold 2C](https://www.dji.com/manifold-2)
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
  - TODO: [Voltage](https://www.quora.com/What-is-the-difference-between-the-nominal-voltage-of-3-7V-and-the-voltage-of-a-cell-of-4-2V-in-lithium-cells) 
  - TODO: C Rating:
  - TODO: Energy Density:
- Compass: 
  - VIO/MoCap: If we want to use the compass as heading estimation with VIO/MoCap, after turning on the camera (e.g. RealSense T265), we need to rotate the drone until the displayed yaw is ```w=1, x=y=z=0```. See reference from the [official documentation](https://docs.px4.io/master/en/ros/external_position_estimation.html) and [github issue](https://github.com/Auterion/VIO/issues/16#issuecomment-856809595).
  - TODO: How to correct [calibrate](https://docs.px4.io/master/en/config/compass.html) compass.
- Telemetry: 
  - Baudrate: USB connection can provide a higher [baudrate](https://learn.sparkfun.com/tutorials/serial-communication/rules-of-serial#:~:text=One%20of%20the%20more%20common,fast%20data%20can%20be%20transferred.) which determines the data transmission rate. The default baudrate of MAVLINK is 921600, but DJI manifold uart0 can only support up to 115200. Note the data frequency of ```mavros/local_position/pose``` should be ~30hz for a reasonable communication configuration.
- ESC [wiring](https://docs.px4.io/master/en/peripherals/pwm_escs_and_servo.html) & [protocal & firmware](https://oscarliang.com/esc-firmware-protocols/) & [calibration](https://docs.px4.io/master/en/advanced_config/esc_calibration.html):
  - TODO: Wiring
  - TODO: Communication Protocal
  - TODO: ESC firmware  
  - TODO: ESC calibration  
- T265:
  - Facing
- Calibration:
   

