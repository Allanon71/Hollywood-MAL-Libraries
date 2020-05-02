# EASING LIBRARY                                                   
> Author  : Fabio Falcucci (Allanon)  
> Contact : info@a-mc.biz  
> License : Freeware  
> Version : 1.4  
> Release : 02.05.2020  
> Dependancies : None  

**SUPPORT ME ON PATREON**  : https://www.patreon.com/Allanon71  
**SUPPORT ME WITH PAYPAL** : mailto:hijoe@tin.it

---
 
## DESCRIPTION
   Easing library is an include file for Hollywood suited to create very
   smooth transitions between values so you can use it to animate almost
   anything like: graphical objects, colors, values, and any value you 
   need to be smoothly changed into another value.
   Please note that this library is based on the library "tween.lua" 
   v1.0.1 (2012-02) by Enrique Garcia Cota.
   I've started the port of the original code to Hollywood in 2013 and
   I've added some new features during time.
   You can get the original code here -> https://github.com/kikito/tween.lua

## INDEX

* [AVAILABLE TRANSITIONS](#available-transitions)
* [FUNCTIONS](#functions)
	* [tween.start()](#tweenstart)
	* [tween.reset()](#tweenreset)
	* [tween.resetAll()](#tweenresetall)
	* [tween.update()](#tweenupdate)
	* [tween.stop()](#tweenstop)
	* [tween.stopAll()](#tweenstopall)
	* [tween.count()](#tweencount)
	* [tween.TEST()](#tweentest)

## AVAILABLE TRANSITIONS
  + linear
  + inQuad
  + outQuad
  + inOutQuad
  + outInQuad
  + inCubic
  + outCubic
  + inOutCubic
  + outInCubic
  + inQuart
  + outQuart
  + inOutQuart
  + outInQuart
  + inQuint
  + outQuint
  + inOutQuint
  + outInQuint
  + inSine
  + outSine
  + inOutSine
  + outInSine
  + inExpo
  + outExpo
  + inOutExpo
  + outInExpo
  + inCirc
  + outCirc
  + inOutCirc
  + outInCirc
  + inElastic
  + outElastic
  + inOutElastic
  + outInElastic
  + inBack
  + outBack
  + inOutBack
  + outInBack
  + inBounce
  + outBounce
  + inOutBounce
  + outInBounce

## FUNCTIONS
   Here is a list of all available functions:

  + tween.start(time, subject, target, easing, callback, ...)
  + tween.reset(id)
  + tween.resetAll()
  + tween.update(dt)
  + tween.stop(id, callback)
  + tween.stopAll(callback)
  + tween.count()
  + tween.TEST()
  
### tween.start()
```plaintext
tweenId = tween.start(time, subject, target, easing, callback, ...)

Start a new tween and returns its id.

INPUT
  time     : Transition time in milliseconds
  subject  : Table where the transition target(s) are defined
  target   : A table with one or more targets and their final values
  easing   : String with the easing formula name
  callback : Function to call when the transition ends
  ...      : Additional variables to pass to the callback function at
             the end of the transition
OUTPUT
  tweenId  : Id of the initialized tween

NOTES
  Possible string values for the parameter <easing> are:
  - linear      - inquad       - outquad      - inoutquad     - outinquad
  - incubic     - outcubic     - inoutcubic   - outincubic    - inquart
  - outquart    - inoutquart   - outinquart   - inquint       - outquint
  - inoutquint  - outinquint   - insine       - outsine       - inoutsine
  - outinsine   - inexpo       - outexpo      - inoutexpo     - outinexpo
  - incirc      - outcirc      - inoutcirc    - outincirc     - inelastic
  - outelastic  - inoutelastic - outinelastic - inback        - outback
  - inoutback   - outinback    - inbounce     - outbounce     - inoutbounce
  - outinbounce.
```

### tween.reset()
```plaintext
tween.reset(tweenId)
 
Reset, and stop, the specified running tween.
 
INPUT
 id : The id of the tween we want to reset
```

### tween.resetAll()
```plaintext
tween.resetAll()
 
Reset, and stop, all running tweens.
```

### tween.update()
```plaintext
tween.update(dt)
 
Update all running tweens evaluating the given 'dt' delta time.
 
INPUT
  dt : Delta time in milliseconds, it is the time passed between the last
       update and this exact moment.
```

### tween.stop()
```plaintext
tween.stop(id, callback)
 
Stops the given running tween.
 
INPUT
  id       : Id of the tween we want to stop
  callback : Set this argument to TRUE if you want to execute the associated
             callback function like if the tween was naturally ended.
```

### tween.stopAll()
```plaintext
tween.stopAll(callback)
 
Stops all running tweens

INPUT
  callback : Set this argument to TRUE if you want to execute the associated
             callback function like if the tween was naturally ended.
```

### tween.count()
```plaintext
count = tween.count()
 
Returns how many tweens are running.
 
OUTPUT
  count : Number of running tweens
```

### tween.TEST()
This program shows how to use tweens and will test all tween functions.
It also uses recursive callback functions to build tween chains.
Have a look at it to see how to use this library.

