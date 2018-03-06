# Arduino_DS3102
Proof of concept Arduino and Realtime DS3102

# Ubuntu Configuration

Previous to upload your sketch to Arduino, you must:

* Check device arduino connected. In Ubuntu 16.04 could be:
    ```
    ls -l /dev/ttyACM*
    ```
* Now we just need to add our user to the group:
    ```
    sudo usermod -a -G dialout <username>
    ```    
  You will need to log out and log in again for this change to take effect    
* Under Ubuntu 14.04 and upper you will hace a problem with the ModemManager so when you'll try to upload your sketch you'll obtain this error:
  ```
    avrdude: ser_open(): can't open device "/dev/ttyACM0": Device or resource busy 
    avrdude: ser_send(): write error: Bad file descriptor Problem uploading to board. 
    See http://www.arduino.cc/en/Guide/Troubleshooting#upload for suggestions.
  ```
 
  Add own rule telling ModemManger to ignore all USB devices from Arduino.org:
    ```
    sudo /etc/udev/rules.d/77-arduino.rules
    
    ATTRS{idVendor}=="2a03", ENV{ID_MM_DEVICE_IGNORE}="1"
    ```

# DS3102 Arduino connection

![img_4683](https://user-images.githubusercontent.com/1216181/37030523-896f38c4-213b-11e8-901c-f6c2dfbe760b.JPG)

