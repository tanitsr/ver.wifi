# **Check Point**
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
 > 1. get config wifi page {show SSID , Password for config} <br>
 > 2. start AP to config <br>
 > 3. get wifi connect when config finish <br>
- if have wifimanager going !! 
- get wifi connect when config finish
- ID input by keypad + get ID data from firebase 
 > if input > ID : can't 
 > if input != int : can't
- get show detail page user
- get show weight {3 time to success} + push weight to firebase 
 > no weight in 30 sec power off lcd and reset system
- height with input by keypad + push to height firebase  \{if input > height (lock 
\f1 hundred point
\f0 ) : can\'92t , if input != int : can\'92t\}\
- show results BMI with image  + push 
\f1 BMI 
\f0 to firebase \
- in 30 sec reset system\
__Offline__\
- get show weight \{3 time to success\} + push weight to firebase (no weight in 30 sec power off lcd and reset system)\
- height with input by keypad + push to height firebase  \{if input > height (lock 
\f1 hundred point
\f0 ) : can\'92t , if input != int : can\'92t\}\
- show results BMI with image  + push 
\f1 BMI 
\f0 to firebase \
- in 30 sec reset system\
 }
