# **Check Point**
<b>Setup</b>
- set all pin (load cell + lcd + delay + keypad)
- set W / R EEPROM
- setup wifimanager
- set delay 
- calibration load call
<b>Function</b>
- listen load cell get weight (while loop)
- if weight > 1 kg start system 
- get welcome page
- get select mode page + function select mode
__Online__
- read SSID , Password from EEPROM
- if no wifi start wifimanager {
 get config wifi page {show SSID , Password for config}
 start AP to config
 get wifi connect when config finish
}
- if have wifimanager going !! \
- get wifi connect when config finish\
- ID input by keypad + get ID data from firebase \{if input > ID : can\'92t , if input != int : can\'92t\}\
- get show detail page user\
- get show weight \{3 time to success\} + push weight to firebase (no weight in 30 sec power off lcd and reset system)\
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
