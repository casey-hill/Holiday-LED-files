# Holiday-LED-files

Here's my guide to building the Holiday LED lights.  This guide is designed to help those who haven't been using Home Assistant in the past or for those who are trying to understand where things are broken.  I'm also going to provide some key tips to avoid some extra work.

I have enough experience with Arduino and Smartthings; I figured this wouldn't be too hard but found most guides are out of date and it was a challenge to troubleshoot.  

Why recreate what other's have done? 
I found many guides out there but struggled to understand how to programtically identify what my problems where.  I hope this guide will help those wehre I struggled.

Summary:
I followed DrZzs guide (https://www.youtube.com/watch?v=6Y6jUM1OaYM&t=1s) which motivied me to create this guide but also used Ben's videos too (https://www.youtube.com/watch?v=9KI36GTgwuQ).  Ben's are great to get up and running and DrZze's guide helped me understand more about the LEDs.   

Hardware (Home Assistant) ~$60
- https://www.amazon.com/gp/product/B01CD5VC92/ref=oh_aui_detailpage_o05_s00?ie=UTF8&psc=1
- https://www.amazon.com/gp/product/B011RBJUOC/ref=oh_aui_detailpage_o05_s01?ie=UTF8&psc=1
- https://www.amazon.com/gp/product/B00MARDJZ4/ref=oh_aui_detailpage_o05_s02?ie=UTF8&psc=1
- https://www.amazon.com/gp/product/B06XX29S9Q/ref=oh_aui_detailpage_o05_s02?ie=UTF8&psc=1

Software is free
- Arduino 1.8.7 https://www.arduino.cc/en/Main/Software
- Download the Hass.io image for your device https://github.com/home-assistant/hassos/releases/download/1.13/hassos_rpi3-1.13.img.gz
- Download Etcher to write the image to an SD card https://www.balena.io/etcher/

Lights
- LED 2811 https://www.amazon.com/gp/product/B01AU6UG5C/ref=oh_aui_detailpage_o04_s03?ie=UTF8&psc=1
- Soderless Board https://www.amazon.com/gp/product/B0727X6N9D/ref=oh_aui_detailpage_o04_s00?ie=UTF8&psc=1
- D1 board https://www.amazon.com/gp/product/B01N3P763C/ref=oh_aui_detailpage_o04_s00?ie=UTF8&psc=1
- 2nd 8266 board https://www.amazon.com/gp/product/B010O1G1ES/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1
- Sealed box https://www.amazon.com/gp/product/B005T990I0/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1
- wire https://www.amazon.com/gp/product/B0119IE4C6/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1
- PowerSupply https://www.amazon.com/gp/product/B06XK3X3PW/ref=od_aui_detailpages00?ie=UTF8&psc=1
- J-Channel https://www.homedepot.com/p/Metal-Sales-2-in-x-10-5-ft-J-Channel-Drip-Edge-Flashing-in-White-4227430/204256712

Tools
- Sodering iron + sodder
- Drill
- 1/2 drill bit
- philips screw driver
- saw horse
- two childern
- ladder
- 3D printer
- wire strippers
- screws

1st Home Assistant setup

I had actually no problems following the setup guides mentioned online.  DrZzes tells you to follow Ben's video which I linked above.  However things have changed since Ben's video.  If you follow his guide completely, you'll end up running into trouble.

Follow his video https://www.youtube.com/watch?v=9KI36GTgwuQ to install the home assistant.  STOP after the installation, do NOT do the additonal steps in his video as they are not necessary for you (MQRTT, SAMBA share)







