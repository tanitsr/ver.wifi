# **Check Point [Last : 251062]**
## Setup <br>
- set all pin (load cell + lcd + relay + keypad) <br>
- set W / R EEPROM <br>
- setup wifimanager <br>
- set relay <br>
- calibration load call {4 load} <br>
- set firebase auth <br>
## Function <br>
- listen load cell get weight (while loop)<br>
- if weight > 10 kg start system <br>
- get welcome page<br>
- get select mode page + function select mode<br>
- get payload Student ID form firebase<br>
- set payload Student ID {weight , height , bmi} of firebase <b>"meaning real-time"</b> <br>
- push json history payload {weight , height , bmi} with Etag timestamp (yyyy-mm-dd'T'hh:mm:ss) <b>"meaning history"</b><br>
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
- set realtime , push history payload {weight , height , bmi} to firebase
- in 30 sec back to select mode
### Offline
- show weight {2 time to success}
> - no weight in 30 sec back to select mode
- height with input by keypad 
 > - input can reset everytime
 > - if input > height (lock hundred point) : can't input and process 
 > - if input != int : can't input and process
- show results BMI with image 
- in 30 sec back to select mode

###### Last Commit : 251062 
