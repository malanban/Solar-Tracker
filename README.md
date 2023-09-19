# Solar-Tracker
##Abstract
The objective of the project automatic solar tracker is to design and build a PID controller to rotate a solar panel which is capable of dynamically adjusting the solar panel to achieve its highest efficiency. The feedback error control mechanism is established using PID to adjust the PWM signal. The PWM signal controls the speed and the direction of rotation of the motor which is connected to the axis of the solar panel. Two LDRs are fixed symmetrically at both sides of the solar panel. These LDRs are producing the error which says how much the solar panel is deviated from its best efficiency position.

## Design Specifications
Complete design is based on analog electronics components. (Operational Amplifiers, capacitors, resistors)
Single axis design
1 second maximum latency to track the sunlight and adjust the panel. 
dynamically adjusting the panel’s angular position to achieve the highest efficiency. 

## Method
### i. Input

The solar tracker comprises 2 LDR sensors placed at either ends of the panel. The potential at the midpoint between the 2 LDRs is subject to change depending on the intensity of light falling on each of them. This value is compared with the set point ( the value obtained if both LDRs receive the same amount of light ), and the difference (error) between the 2 readings is calculated using a differential amplifier.
![image](https://github.com/malanban/Solar-Tracker/assets/131769448/a25e5d7b-fdd2-4262-880c-8adb430b1477)


### ii. PID control- proportional integral differential

The error obtained is fed into the PID control circuit. The PID control circuit acts as a feedback system that will adjust the panel’s orientation depending on the error calculated. It comprises of 3 operational amplifiers configured to perform proportional, integral and derivative operations.

Proportional: The proportional part gives a gain to the error signal. Here an inverting op amp configuration is used to get the required gain, including variable resistors to adjust the gain of the error to the required value.

![image](https://github.com/malanban/Solar-Tracker/assets/131769448/eb527fa2-ce37-4225-b22f-29183e6b3cc3)


Integral: The integral part reduces the steady state error by accumulating the error over time. An op amp integrator is used for this task with variable resistors. Here the 1Mohm resistor is used in parallel with the capacitor of the integrator to prevent the integration of input offset voltage of the op amp and producing an incorrect output.

![image](https://github.com/malanban/Solar-Tracker/assets/131769448/f1d9da7d-2172-42df-818f-9ce4aa47319f)


Derivative: The derivative component produces the output signal proportional to the rate of change of the error. It reduces the overshoot and smoothens the control signal. An op amp differentiator circuit is used here including variable resistors to adjust the values. There is a resistor series to the capacitor of the differentiator to decrease the effects of noise by decreasing the high frequency gain.

![image](https://github.com/malanban/Solar-Tracker/assets/131769448/4ef0b8b1-bb0f-4fb6-9d05-ee6942ba1228)




### iii. PWM generation

Square wave generation

The first part of this circuit is the schmitt trigger circuit, then comes the integrator circuit. The schmitt trigger circuit is basically a comparator circuit. When the non inverting input rises or falls about the inverting input, the output of the schmitt trigger will be the two saturated supply voltages.

Triangular wave generation

This output is applied to the integrator circuit and it integrates this voltage for a finite time. The output of the integrator circuit is fed back as input into the schmitt trigger.PWM wave generation
The comparator output will be a PWM signal whose pulse width will vary depending on the error.
﻿![image](https://github.com/malanban/Solar-Tracker/assets/131769448/57af43d3-e1c1-42fc-b712-c91d70c0f4ae)
 ![image](https://github.com/malanban/Solar-Tracker/assets/131769448/4345520b-8157-4df0-8c1c-654c776d9c60)



### iv. Motor controller

Built using L293D

### v. Component Selection

Motor Selection

Motor designs for solar power applications, therefore, must stand up to extremes in temperature (both absolute and over a broad range), humidity and highly corrosive salt sprays, wind loads and abrasive airborne particulate matter. Our choice- Brushed DC motors- simple, easy driving method and low cost. Control of dc motor is complex and life is short but we can replace brushes. As the solar panel can be affected by wind power high power motor is selected according to its weight and dimensions.
Selected motor – brushed dc motor
Voltage -12V
No load speed- 25 RPM
No load current- 60mA
Max torque- 16 kgcm
Stall current-0.9 A

Motor driver selection
According to our motor it drives a stall current of 0.9 A . so the maximum current of the motor driver should be greater than 0,9 A. Logic voltage as 5 V. our solar panel is in medium size (22 cm x 14 cm) , L93D is used.Op amp selection
LM741 (General Purpose)
LM339N (For Comparator)
LMC 560 (For Buffer)
﻿

## Circuit Diagram
![image](https://github.com/malanban/Solar-Tracker/assets/131769448/ff022e5e-db07-496a-b69a-353b5f7a3635)


## Enclosure
![image](https://github.com/malanban/Solar-Tracker/assets/131769448/cd5d307a-1ef1-4e69-bd5f-b15a9e101f65)
![image](https://github.com/malanban/Solar-Tracker/assets/131769448/2a3176d3-1bfd-42c1-9b46-652ac035561a)


## PCB
After testing the circuit in breadboards and obtaining the desired output waveforms, the PCB was designed using Altium software for the final implementation. The output Gerber files were generated and sent to China (JLCPCB) for printing.
![image](https://github.com/malanban/Solar-Tracker/assets/131769448/20735c48-33ce-48b2-bca3-9a5e6c82316e)
![image](https://github.com/malanban/Solar-Tracker/assets/131769448/3078e9b1-6c16-4e2f-a04f-f55423899057)
![image](https://github.com/malanban/Solar-Tracker/assets/131769448/e3234504-be31-4795-a272-0703fe7ff7c6)




Link for JLCPCB: https://jlcpcb.com/
## Our Product
![image](https://github.com/malanban/Solar-Tracker/assets/131769448/81cbe0ae-539f-44a1-8eea-e5c78f575325)


## Our Team
Amarasinghe A.M.V.M.

Gunawardena M.N.

Malanban K.

Rathnayake R.N.P
