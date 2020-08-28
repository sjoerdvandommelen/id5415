---
layout: course-page
title: "Lab XP 3"
permalink: /module3/labxp
description: "Prototyping Connected Products - Lab Experiment 3"
labxp-of: id5415-3
introduction: In this Lab Experiment,
technique:
metrics:
report:
---


---

* Do not remove this line (it will not be displayed)
{:toc}

---

```python3
import os
import board

from dotenv import load_dotenv

from dcd.entities.thing import Thing
from time import sleep

# import DHT sensor library
from Adafruit_DHT import DHT11
# import light sensor from GPIO0 
from gpiozero import LightSensor # for ldr connection


# The thing ID and access token
load_dotenv()
THING_ID = os.environ['THING_ID']

# Instantiate a thing with its credential
my_thing = Thing(thing_id=THING_ID, private_key_path="/etc/ssl/certs/" + THING_ID + ".private.pem")

# suing gpio pin 4 
dht_sensor = DHT11(board.d4, use_pulseio=False)
LDR_pin = 18
LDR_sensor = LightSensor(LDR_pin)

# Find or create a property to store light 
my_property_ldr = my_thing.find_or_create_property("LDR sensor", "LIGHT")


# Find or create a property to store temperature
my_property_temp = my_thing.find_or_create_property("DHT Temperature", "TEMPERATURE")


# Find or create a property to store humidity 
my_property_humidity = my_thing.find_or_create_property("DHT Humidity", "RELATIVE_HUMIDITY")




def update_light():

	# calibration to LUX  needs to be done

	try:
	    lux = LDR_sensor.value # between 0 (dark) and 1 (light)
  	    lux = lux*100 # dummy calibration
	    my_property_cpu.update_values((lux,))	
	except RuntimeError as error:
	    print(error.args[0])
	    continue

	except Exception as error:
	    raise error




def update_temp():
	try:
	    temp = dht_sensor.temperature
	    my_property_temp.update_values((temp),)	
	except RuntimeError as error:
	    # DHT Errors can happen fairly often
	    print(error.args[0])
	    continue

	except Exception as error:
	    dht_sensor.exit()
	    raise error
	


def update_humidity():
	try:
	    humidity = dht_sensor.humidity
	    my_property_humidity.update_values((humidity),)
	except RuntimeError as error:
	    # DHT Errors can happen fairly often
	    print(error.args[0])
	    continue

	except Exception as error:
	    dht_sensor.exit()
	    raise error



while True:
	update_light()
	update_temp()
	update_humidity()

	# sleep every 60 seconds
	time.sleep(60)
```
