# Introduction #

The formular used by eeepc-fancontrol is very simple. Used variables are
  * $minSpeed (> 0 and < 100 and < $maxSpeed) for the minimum speed the fan should run,
  * $maxSpeed (> 0 and < 100 and > $minSpeed) for the maximum speed,
  * $normalTemp (> 0 and < $highTemp) for the temperature the fan should start spinning at $minSpeed,
  * $highTemp (> 0 and > $normalTemp) for the temperature the fan should spin at $maxSpeed

# Details #

Additional information:
The fan speed value is 0 to 100. Those are percentages (wow!). The fan itself is PWM controlled.

**ATTENTION**: You need to set $minSpeed to at least 14. Everything under 14% is not enough to power the motor inside the fan. It will stop spinning. Version 0.12 implements routines to check if the fan still spins.

The daemon adjusts fan speed by translating the temperature + the variables linear to a fan speed. The speedPercentage per Celsius+$normalTemp is calculated this way:
```
$speedPercentage = $minSpeed+(($maxSpeed-$minSpeed)/($highTemp-$normalTemp)*($currentTemperature-$normalTemp))
```
This formular is quite simple but effective. This way fan really spins only if needed.

Applicable settings for the vars are (tested, usualy not harming)
```
$minSpeed = 14
$maxSpeed = 100
$normalTemp = 50
$highTemp = 60
```