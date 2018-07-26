# Orange Pi

## website

[http://www.orangepi.org/](http://www.orangepi.org/)

## links

[https://developer.ubuntu.com/core/get-started/orange-pi-zero](https://developer.ubuntu.com/core/get-started/orange-pi-zero)

## env

* 板子: Orange Pi Zero
* 连接: USB CH340 TTL
* 系统: ubuntu\_server\_xenial\_OrangePiZero 16.04LTS

## setup

1. SD Card Formatter formate SD
2. Win32DiskImager flash unbutu image to SD
3. USB-TTL 连接到 orange pi的debug port 1. GND &lt;-&gt; GND 2. RX &lt;-&gt; TX 3. TX &lt;-&gt; RX
4. use putty in window pc
   1. Connection type: Serial
   2. Serial line: COMxx \(find it in you PC device manager port\)
   3. Speed 115200
5. use screen in linux

   ```text
   sudo screen /dev/ttyUSB0 115200
   ```

6. login user as root/orangepi and password as orangepi

