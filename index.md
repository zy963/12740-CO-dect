<script>
  var head = document.getElementsByTagName("header").item(0);
  var p = head.getElementsByTagName("p").item(0);
  p.innerText = "Yijie Zhu, Yuming Zhang, Zheyi Li";
</script>


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
  
<img src="https://raw.githubusercontent.com/zy963/12740-CO-dect/main/flow%20chart.png" alt="Flow Chart">
  
However, out of safety concerns, we will measure humidity instead of CO. Note that for the rest of the report, the target gas will still be addressed as CO even though it is humidity that is actually being measured.  
  
---

### For Progress Report

#### Current Progress

##### Things that have been done by 10/2/2021
- Circuit Setup (80% complete)  
  
<img src="https://raw.githubusercontent.com/zy963/12740-CO-dect/main/circuit_1004.jpg" alt="Circuit">
<div align="center">Circuit by Oct.04</div> 
  
  
- Temperature and humidity sensor  
1. Temperature focusing on determining the engine on/off status.  
1. Humidity focusing on determining the CO concentration level: Out of safety concerns, we will measure humidity instead of CO.
  
- 2 Lights  
1. 1 will keep lighting if the circuit is working properly: Lighting while temperature and humidity sensor is working.  
1. 2 will keep lighting once the CO concentrationhumidity (humidity) is above certain threshold.  
  
- Data will be stored in a .npy file, which can be imported on other device by using Python 3.
1. In our circuit, we will use light to reflect the CO concentration timely.  
  
- Report Section  
1. Introduction, Motivation and Goal first draft has been finished.  
1. Waiting for experiments and results to make adjustment on these sections.   
  
#### Problems Encountered

- PIR Motion sensor malfunctioning  
1. Always returns "True" values, even there is no motion in detection area.  

Borrwed one more sensor to check if it is hardware problem or coding problem.  
  
#### Future Plan

- Things have to be done by 10/10/2021  
1. Making sure motion sensor will online with correct values return
1. Finish Methodology first draft based on our circuit setup and project goal
1. Collecting data to generate continuous plot of temperature to show different situations(i.e. Engine on/off, CO concentration in safe/warning level)
1. First draft of presentation slides based on report
- Things have tobe done by 10/12
1. Demo (5 minutes)
  
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
  
[2]MAYO Clinic. (2019, October 16). Carbon monoxide poisoning. Mayo Clinic. Retrieved October 4, 2021, from https://www.mayoclinic.org/diseases-conditions/carbon-monoxide/symptoms-causes/syc-20370642.   
  
[3]Iowa State University. (2020). Carbon monoxide poisoning: Vehicles (AEN-208). Department of Agricultural and Biosystems Engineering. Retrieved October 4, 2021, from https://www.abe.iastate.edu/extension-and-outreach/carbon-monoxide-poisoning-vehicles-aen-208/.   
