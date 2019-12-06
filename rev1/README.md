# **Check Point [Last : 161162]**
## Setup <br>
- set all pin (load cell + lcd + relay + keypad) <br>
- set W / R EEPROM <br>
- setup wifimanager <br>
- set relay <br>
- calibration load call {4 load} <br>
- set firebase auth <br>
- set get date from NTP Server when sent payload to firebase <br>
### Pin Define
- TFT 2.2" ili9925 LCD
> - RST 17
> - RS 16
> - CLK 18
> - SDI 23
> - CS 5
- keypad
> - 12 {row} //start left side only
> - 14
> - 27
> - 26
> - 25 {coloum}
> - 33
> - 32
> - 15
- hx711
> - DOUT 21
> - CLK 22
- delay 
> - 13
> - com to 5v output from esp32
## Function <br>
- listen load cell get weight (while loop)<br>
- if weight > 20 kg start system <br>
- get welcome page<br>
- get select mode page + function select mode<br>
- get payload Student ID form firebase<br>
- set payload Student ID {weight , height , bmi} of firebase <b>"meaning real-time"</b> <br>
- get date from NTP Server when push json history <b>ONLY!</b> <br>
- push json history payload {weight , height , bmi} with Etag timestamp (yyyy-mm-dd'T'hh:mm:ss) from NTP Server <b>"meaning history"</b><br>
### Select mode <br>
- before select mode show welcome page<br>
- show select mode page <br>
- "A" to online <br> 
- "B" to offline <br>
- in 30 sec if nothing turn off led 
### Online <br>
- read SSID , Password from EEPROM
- if no wifi start wifimanager 
 > - get config wifi page {show SSID , Password for config} <br>
 > - start AP to config <br>
 > - get wifi connect when config finish <br>
- if have wifimanager going !! 
- get wifi connect when config finish
- ID input by keypad + get ID data from firebase 
 > - input can reset everytime
 > - if input > ID : can't input and process <br>
 > - if input != int : can't input process 
- show detail page user
- show weight {2 time to success} 
 > - no weight in 30 sec back to select mode
- height with input by keypad + push to height firebase  
 > - input can reset everytime
 > - if input > height (lock hundred point) : can't input and process 
 > - if input != int : can't input and process
- show results BMI with image 
> - bmi <= 18.5 {under}
> - bmi > 18.5 && bmi <= 22.9 {healthy}
> - bmi >= 23 && bmi <= 29.9 {over}
> - bmi > 29.9 {obese}
- set real-time , push history payload {weight , height , bmi} to firebase
- in 30 sec back to select mode
### Offline
- show weight {2 time to success}
> - no weight in 30 sec back to select mode
- height with input by keypad 
 > - input can reset everytime
 > - if input > height (lock hundred point) : can't input and process 
 > - if input != int : can't input and process
- show results BMI with image 
> - bmi <= 18.5 {under}
> - bmi > 18.5 && bmi <= 22.9 {healthy}
> - bmi >= 23 && bmi <= 29.9 {over}
> - bmi > 29.9 {obese}
- in 30 sec back to select mode

###### Last Commit : 161162
