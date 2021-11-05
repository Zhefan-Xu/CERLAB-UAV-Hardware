# building_px4_quadcopter


# Hardware:
- flight controller: 

- Telemetry Communication (companion computer with FC): [USB UART serial port](https://www.amazon.com/DSD-TECH-SH-U09C2-Debugging-Programming/dp/B07TXVRQ7V/ref=sr_1_3?crid=2ZVK4AYT03PDX&dchild=1&keywords=short+uart&qid=1635992461&qsid=144-8949687-4547914&sprefix=short+uart+%2Caps%2C73&sr=8-3&sres=B07J64TGS3%2CB07RBKCW3S%2CB07TXVRQ7V%2CB07R8BQYW1%2CB00LODGRV8%2CB00IJXZQ7C%2CB07D6LLX19%2CB07D9R5JFK%2CB01N47LXRA%2CB07R45QJVR%2CB00LZVEQEY%2CB08HLSS5T4%2CB075N82CDL%2CB08FBDTP5G%2CB07WX2DSVB%2CB014GZTCC6). (USB connection can provide a higher [baudrate](https://learn.sparkfun.com/tutorials/serial-communication/rules-of-serial#:~:text=One%20of%20the%20more%20common,fast%20data%20can%20be%20transferred.) which determines the data transmission rate. The default baudrate of MAVLINK is 921600, but DJI manifold uart0 can only support up to 115200. Note the data frequency of mavros/local_position/pose should be ~30hz for a reasonable communication configuration.)
