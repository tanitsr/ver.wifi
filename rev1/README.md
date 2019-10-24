# **Check Point [wait edit]**
## Setup <br>
- set all pin (load cell + lcd + delay + keypad) <br>
- set W / R EEPROM <br>
- setup wifimanager <br>
- set delay <br>
- calibration load call <br>
## Function <br>
- listen load cell get weight (while loop)<br>
- if weight > 1 kg start system <br>
- get welcome page<br>
- get select mode page + function select mode<br>
### Online <br>
- read SSID , Password from EEPROM
- if no wifi start wifimanager 
 > - get config wifi page {show SSID , Password for config} <br>
 > - start AP to config <br>
 > - get wifi connect when config finish <br>
- if have wifimanager going !! 
- get wifi connect when config finish
- ID input by keypad + get ID data from firebase 
 > - if input > ID : can't input and process <br>
 > - if input != int : can't input process
- get show detail page user
- get show weight {3 time to success} + push weight to firebase 
 > - no weight in 30 sec power off lcd and reset system
- height with input by keypad + push to height firebase  
 > - if input > height (lock hundred point) : can't input and process 
 > - if input != int : can't input and process
- show results BMI with image  + push BMI to firebase 
- in 30 sec reset system
### Offline
- get show weight \{3 time to success\} + push weight to firebase (no weight in 30 sec power off lcd and reset system)
- height with input by keypad + push to height firebase  
 > - if input > height (lock hundred point) : can't input and process 
 > - if input != int : can't input and process
- show results BMI with image  + push BMI to firebase 
- in 30 sec reset system

###### Last Commit : 71062 
