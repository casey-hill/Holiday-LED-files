# Holiday LED


Here's my guide to building the Holiday LED lights. This guide is designed to help those who haven't been using Home Assistant in the past or for those who are trying to understand where things are broken. I'm also going to provide some key tips to avoid some extra work.

I have enough experience with Arduino and Smartthings; I figured this wouldn't be too hard but found most guides are out of date and it was a challenge to troubleshoot.

Why recreate what other's have done? I found many guides out there but struggled to understand how to programtically identify what my problems where. I hope this guide will help those wehre I struggled.

## Summary:

 I followed [DrZzs guide](https://www.youtube.com/watch?v=6Y6jUM1OaYM&t=1s) which motivied me to create this guide but also used [Ben's videos too](https://www.youtube.com/watch?v=9KI36GTgwuQ). Ben's are great to get up and running and DrZze's guide helped me understand more about the LEDs.

## Hardware (Home Assistant) ~$60

* https://www.amazon.com/gp/product/B01CD5VC92/ref=oh_aui_detailpage_o05_s00?ie=UTF8&psc=1
* https://www.amazon.com/gp/product/B011RBJUOC/ref=oh_aui_detailpage_o05_s01?ie=UTF8&psc=1
* https://www.amazon.com/gp/product/B00MARDJZ4/ref=oh_aui_detailpage_o05_s02?ie=UTF8&psc=1
* https://www.amazon.com/gp/product/B06XX29S9Q/ref=oh_aui_detailpage_o05_s02?ie=UTF8&psc=1

## Software ~$free

* [Arduino 1.8.7](https://www.arduino.cc/en/Main/Software)
* [Download the Hass.io image for your device]( https://github.com/home-assistant/hassos/releases/download/1.13/hassos_rpi3-1.13.img.gz)
* [Download Etcher to write the image to an SD card]( https://www.balena.io/etcher/)

## Lights

* [LED 2811](https://www.amazon.com/gp/product/B01AU6UG5C/ref=oh_aui_detailpage_o04_s03?ie=UTF8&psc=1)
* [Soderless Board]( https://www.amazon.com/gp/product/B0727X6N9D/ref=oh_aui_detailpage_o04_s00?ie=UTF8&psc=1)
* [D1 board](https://www.amazon.com/gp/product/B01N3P763C/ref=oh_aui_detailpage_o04_s00?ie=UTF8&psc=1)
* [2nd 8266 board](https://www.amazon.com/gp/product/B010O1G1ES/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1)
* [Sealed box](https://www.amazon.com/gp/product/B005T990I0/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1)
* [Wire](https://www.amazon.com/gp/product/B0119IE4C6/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1)
* [PowerSupply](https://www.amazon.com/gp/product/B06XK3X3PW/ref=od_aui_detailpages00?ie=UTF8&psc=1)
* [J-Channel](https://www.homedepot.com/p/Metal-Sales-2-in-x-10-5-ft-J-Channel-Drip-Edge-Flashing-in-White-4227430/204256712)

## Optional

These are things I used or found helpful during my installation. I wanted to make my board more modualar and also overcome some challenges.
* [PBC board](https://www.amazon.com/gp/product/B01N3161JP/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1)
* [Male/Female pins](https://www.amazon.com/gp/product/B074HVBTZ4/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1)
* [Male/Female connectors](https://www.amazon.com/gp/product/B00NBSH4CA/ref=oh_aui_detailpage_o04_s01?ie=UTF8&psc=1)
* [Logic Shifter](https://www.amazon.com/gp/product/B0148BLZGE/ref=oh_aui_detailpage_o04_s02?ie=UTF8&psc=1)

## Tools
* Sodering iron + sodder
* Drill
* 1/2 drill bit
* philips screw driver
* saw horse
* two childern
* ladder
* 3D printer
* wire strippers
* screws

## Overall process

* Home assistant OS install
* Home assistant configuration
* Home assisant configure MQTT
* Home assistant add the lights
* Uploading the Arduino Code
* Installing the hardware


### Home assitant OS install

I had actually no problems following the setup guides mentioned online. DrZzes tells you to follow Ben's video which I linked above. However things have changed since Ben's video. If you follow his guide completely, you'll end up running into trouble.
Follow [Ben's video](https://www.youtube.com/watch?v=9KI36GTgwuQ) to install the home assistant OS on the card, place the card in the Pi and power it up. I'm going to assume you can figure out how to connect at this point, you should assign it a static ip address and connect via ip address as opposed to the the name of the Pi.

Now, it is imporant to undestand, Ben provides a lot of good tips in the entire video so please watch it all. I'll call out his tips on: checking the configuration file and restarting the server. I would ignore the MQTT installation and Samba installation sections as they are not necessary for this setup.

### Home assitant Configuration

Configuration of Home Assistant Walk through the setup questions. Once you are logged in, you will want to install the web based editor. Ben described how to do this above, so this is one step you will follow. That is it, you don't need to install or add anything additional. MQTT broker is already installed on this version of the Hass.io.

**TIP** - Edit your configuraiton.yaml file. Add one line to the end of the file (later you'll be asked for the username which is in the documentatation; homeassistant); you don't need to put in a ip address or port number as others have mentioned

MQTT
 
    password: makeoneyoucanremember
	

At this point, do a configuration file check and reboot the server.

Once the Home Assistant is up and running, check the log file to verify there are no issues.


### Home Assistant MQTT Configuration

As I mentioned above, all you need to do is add MQTT at the end of the configuration.yaml file and add the password. Don't specifiy the username as it is already preconfigured as homeassistant.

### Home Assistant adding the lights

Up to this point, you have installed Home Assistant and enabled the use of MQTT with a password of your choice. It's now time to configure Home Assistant to how the light switch, theme and animation speeds.

Doing this is super simple, just navigate to the end of the configuration.yaml file and past in the particial Configuration.yaml file that DrZzs provided.

Now check the configuration file and reboot the server.

Once the server is up and running, you should see the new buttons added.

### Updating the Arduino code

Generally speaking, there were minor changes here for this to work.  I would state you need to follow Ben's video to import the libraries.  I know during the time I was using the arduino code, I saw errors with one of the libraries but I just commented it out.  

The other pain I had was the chip DrZzs uses would not work on D4, only until I changed it to just 5 did I see things working.  


### Installing the hardware

This area was a little lacking in the videos and I had to make a few decisions.  

**PowerSupply**
First, you going to need a powercord to plug-in to the power supply.  If you don't know which one is "N" vs "L", you should!  Here is the easy way to tell, I looked at my cord to determine which one the larger end was and used ![this diagram](https://github.com/casey-hill/Holiday-LED-files/blob/master/images/power%20outlet.PNG) to trace the wire.




**FAQ** 

**Q.** Why are the first 10 or so lights turning on but the rest of the string is off?

**A.** If you didn't use a power supply, you'll need to purchase the above. If you have the power supply connected, then the code you have on the Arduino is not properly configured or you are using the wrong pin.  Also, the D1 chip doesn't push a full 5 volts which is why only a few work and then it fades out quickly.

**Q.**  My switches are not using up on Home Assistant

**A.**  Did you install the 3rd party MQTT add-in? I would suggest removing it and using the built-in broker.

**Q.** I noticed after I restarted my server that there are errors. 

**A.** Click on the error and review the error in the configuration.yaml file. Likely the problem will exist there since nothing else is changing.

**Q** Do I need to use the additional logic shifter?

**A**  You don't need to BUT if you are going to jump across spaces in the roof line, then you need one.  There doesn't appear to be limitation on lenght for a roof anyway.  I've jumped 15 feet and 10 feet with no problems.
