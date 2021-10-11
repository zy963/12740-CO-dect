<script>
  var head = document.getElementsByTagName("header").item(0);
  var p = head.getElementsByTagName("p").item(0);
  p.innerText = "Yijie Zhu, Yuming Zhang, Zheyi Li";
</script>

<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      processEscapes: true
    }
  });
</script>
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

<h2 style="text-align:center;"> Vechicular CO Dection </h2>
vedio link:
---
### Introduction

CO is undetectable to the human senses, leading to many deaths every year. Non-traffic, unintentional CO poisoning from vehicle exhaust averaged an estimated 2,000 injuries from 2003–2006. Outbreaks of CO poisoning often occur during winter and extreme weather events (e.g., hurricanes, snowstorms, blizzards) because of motor vehicles left running in a closed environment[1]. Such a breathtaking number draws our attention. Incomplete combustion of fuel produces a huge amount of carbon monoxide. It’s extremely dangerous for passengers and the driver, especially with a defective exhaust system and unsealed car body.  
  
This project focuses on the CO detection and initial response system for vehicles. CO detection system is designed to collect information of CO concentration, the status of engine, and the occupancy of people in car. If CO detection system finds CO concentration in the car is determined to be unsafe, the initial response system will be triggered to alarm the driver and passengers and circulate the air in the car to ensure the safety of people. We use CO sensor, temperature sensor and motion sensor to verify a true danger. The initial response system includes multiple alarms and starting up the self-circulation of the air conditioner to initially decrease risk.

#### Motivation

When CO density exceeds a certain threshold, our body replaces the oxygen in your red blood cells with carbon monoxide, which can lead to serious tissue damage, or even death[2]. The CO  produced by internal combustion gasoline engines is up to 30,000 parts per million (ppm). So it’s dangerous for a vehicle with a defective exhaust system where CO leaks from and enters the vehicle through holes in the body or open windows[3]. Therefore, we decided to develop a CO detection and initial response system to initially reduce or lift danger and fight for rescue time. 

#### Goals

We installed a CO sensor and a motion sensor in the car cabinet and a temperature sensor in the exhaust pipe.  
  
If the CO density is high enough to be determined dangerous, the initial response system will be triggered. If the motion sensor detects the driver in the car, the initial response system will turn on the in-vehicle alarm and the air conditioning system. If there’s only passengers or no people in the car, the initial response system will send an emergency message to the driver besides the in-vehicle alarm and the air conditioning system. But considering that CO poisoning is a low possibility event, we add an extra temperature sensor for engine status check to verify that the high CO density is caused by the engine instead of a system failure. That is to say, the situation will be defined as dangerous when the CO concentration is high with the engine running. The corresponding action of the initial response system will be determined based on human occupancy. The flow chart is attached below. 
  
<div align="center">Figure 1 DEcision-Making Map</div>
<img src="https://raw.githubusercontent.com/zy963/12740-CO-dect/main/flow%20chart.png" alt="Figure 1 DEcision-Making Map">
    
However, out of safety concerns, we will measure humidity instead of CO. Note that for the rest of the report, the target gas will still be addressed as CO even though it is humidity that is actually being measured.  
  
---
### Progress Report

#### Progress Report

##### 09/15/2021
Our group set up the goal of the project, which is to detect the CO concentration in the closed environment and send an alarm to the user who is in this closed environment. The principle of our project is to protect human life by letting them know whether the CO concentration is in danger level. We assumed the vehicle is a closed environment for our testing purpose.  
  
##### 09/22/2021
Based on the principle of the project, our second meeting focusing on discussing the logic of CO detection and alarming system. As shown in Figure 1, our decision-making map has been created.From Figure 1, we made serval conditions that may occur during the real-life situation. But the major part is still the CO concentration sensor. Other decision circles like *Message* will be expressed by using light. The engine on/off status will be detected by the temperature sensor. 
Meanwhile, we determine the sensor we are potential going to use are:
- HC-SR501 PIR Motion Sensor
- DHT 11 Temperature and Humidity Sensor
- LED Light(s)
- MQ-7 CO Carbon Monoxide Detector Sensor  
  
##### 09/30/2021
After talked with Professor Berges about our project, especially the feasibility of CO concentration sensor data collection. We found that the environment in which we decided to collect the CO concentration data has potential extreme danger, and also, we don’t have a vehicle to create a closed environment for our test.  
As a concession, we decide to use humidity as a substitution for CO. In the rest of the circuit setup, we will not use the MQ-7 CO concentration sensor but use DHT 11 to collect humidity instead.  
  
##### 10/01/2021
First attempt to set up the circuit by using Raspberry Pi 4 and sensors. We first use a motion sensor, 1 LED light, DHT-11 sensor to create a simple circuit to check whether all sensors are working properly.  
From Figure 2 and 3, we will use the print function in Python code to print the collected temperature and humidity and print “Motion Detected!” if the motion sensor returns the “True” value. “True” value will only be returned once the motion sensor detects motion in the detection range. Based on the output, we think all the sensors work properly. 
<img src="https://raw.githubusercontent.com/zy963/12740-CO-dect/main/DHT11 testing code.png" alt="Figure 2 – DHT 11 Sensor Testing Code">
<div align="center">Figure 2 – DHT 11 Sensor Testing Code</div>  
<img src="https://raw.githubusercontent.com/zy963/12740-CO-dect/main/Output_PIR testing code.jpg" alt="Figure 3 – Sensor Data Output & Motion Sensor Testing Code">
<div align="center">Figure 3 – Sensor Data Output & Motion Sensor Testing Code</div>  
  
Then we added 2 LED lights to show the working status; green LED will on if the DHT 11 is collecting data in Figure 4, then turn off once the DHT 11 stop working in Figure 5. Red LED will on once the motion has been detected by a sensor in Figure 6, turned off when there is no motion detected in Figure 7.  

<div align="center">Figure 4 – Green LED On – DHT 11 is Collecting</div>
<img src="https://raw.githubusercontent.com/zy963/12740-CO-dect/main/Green LED On.jpg" alt="Figure 4 – Green LED On – DHT 11 is Collecting">  

<div align="center">Figure 5 – Green LED Off – DHT 11 not working</div>
<img src="https://raw.githubusercontent.com/zy963/12740-CO-dect/main/Green LED Off.jpg" alt="Figure 5 – Green LED Off – DHT 11 not working">  

<div align="center">Figure 6– Red LED On– Humidity is above safe level</div>
<img src="https://raw.githubusercontent.com/zy963/12740-CO-dect/main/Red LED On.jpg" alt="Figure 6– Red LED On– Humidity is above safe level">  

<div align="center">Figure 7 – Red LED Off – Humidity is below safe level</div>
<img src="https://raw.githubusercontent.com/zy963/12740-CO-dect/main/Red LED Off.jpg" alt="Figure 7 – Red LED Off – Humidity is below safe level">
  
##### 10/02/2021-10/08/2021
Optimizing the logical and decision-making process, we used red LED while the DHT11 was collecting data and green LED on while the motion sensor was working. While testing the motion sensor with no motion detection, a problem was found. The motion sensor keeps returning a True value even if there is no motion in the detection range.  
A potential problem that may cause the failure in motion sensor returned value:  
- Motion sensor return certain float numbers that will cause if function always true.
  - Use while loop to print the input value from motion sensor at the time period of 1s, the code and running result is in Figure 8.
  - After printing, we found that the motion sensor always returns 1 for either motion detected or motion not detected situation.
  - We think the problem is caused by the sensor itself, since it only returns 1 value.  

<div align="center">Figure 8 – Print Returning Value from Motion Sensor</div>
<img src="https://raw.githubusercontent.com/zy963/12740-CO-dect/main/Print Returning Value from Motion Sensor.jpg" alt="Figure 8 – Print Returning Value from Motion Sensor">
  
- Sensitivity is too high so that the motion will be detected any time. (×)
  - Use a 3*mm* straight screwdriver to return sensitivity counterclockwise to reduce the sensitivity as much low as we can.
  - Adjusting sensitivity in both counterclockwise and clockwise during the sensor is working, try to find a "motion no detected" situation where the sensor will return a *False* result.  

- Time delay is too high that the motion sensor has no time to return other value. (×)
  - Use a 3*mm* straight screwdriver to return sensitivity counterclockwise to reduce the sensitivity as much low as we can.
  - Adjusting sensitivity in both counterclockwise and clockwise during the sensor is working, try to find a "motion no detected" situation where the sensor will return a *False* result.  

- Coding issue.
  - Solved. There is no syntax or pin arrangement issue in the code.
  - If there is a problem, the sensor will not return values.
  - According to the result printing step shown above, we know that the sensor will only return the same value, which is not caused by the code.  

- Motion sensor malfunction due to itself.
  - We borrowed the other motion sensor from another course group.
  - By conducting the same process shown above, the motion sensor from the other group will also have the same problem that only returns 1 value all the time.  

Based on all attempts shown above, we decide to not use motion sensor anymore. We will use photosensitive light sensor to detect human occupancy.







---
The rest is a draft. 

---

### Methodology

#### Phenomena of Interest
temperature; gas density; PIR

- Temperature of the exhaust pipe<br />
Temperature is the measurement of hotness or coldness. In this project we are using the Celsius (°C) temperature scale. The temperature measurement is intended to check the status of the vehicle engine. However, the sensor can only detect up 125°C, which is why we are mearsuring the exhaust pipe instead.
<u> how to caliberate </u>

- Density of CO<sub>2</sub>

- Human occupancy<br />
For human occupancy we are using a PIR senor.<br /> 
PIR sensors are more complicated than the other two sensors used in this project. There are multiple variables that affect the sensors input and output. The PIR sensor itself has two slots in it, each slot is made of a special material that is sensitive to IR. The lens used here is not really doing much and so we see that the two slots can 'see' out past some distance (basically the sensitivity of the sensor). When the sensor is idle, both slots detect the same amount of IR, the ambient amount radiated from the room or walls or outdoors. When a warm body like a human or animal passes by, it first intercepts one half of the PIR sensor, which causes a positive differential change between the two halves. When the warm body leaves the sensing area, the reverse happens, whereby the sensor generates a negative differential change. These change pulses are what is detected.

Describe the physical phenomena of interest, e.g. physical principles, static and dynamic behavior, and signal characteristics

#### Sensors Used

- Describe the sensors you used, e.g. physical principles, static and dynamic behavior, and signal characteristics

#### Signal Conditioning and Processing

- Describe the signal conditioning and processing procedures

---

### Experiments and Results

- Describe the experiments you did and present the results; Use tables and plots if possible

---

### Discussion

- Discuss the insights from the project

---

### Reference
[1]Centers for Disease Control and Prevention. PICTURE OF AMERICA REPORT. Available from URL:https://www.cdc.gov/pictureofamerica/pdfs/picture_of_america_poisoning.pdf.  
  
[2]MAYO Clinic. (2019, October 16). Carbon monoxide poisoning. Mayo Clinic. Retrieved October 4, 2021, Available from https://www.mayoclinic.org/diseases-conditions/carbon-monoxide/symptoms-causes/syc-20370642.   
  
[3]Iowa State University. (2020). Carbon monoxide poisoning: Vehicles (AEN-208). Department of Agricultural and Biosystems Engineering. Retrieved October 4, 2021, Available from https://www.abe.iastate.edu/extension-and-outreach/carbon-monoxide-poisoning-vehicles-aen-208/.   
