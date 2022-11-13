
# Modeling Traffic Sign By Using Petri Nets

**Using petri nets to model the following system :**

![App Screenshot](https://cdn.discordapp.com/attachments/908279454621651015/1041354394752532621/drawio.png)


## **Traffic Sign Rules That We Must aware of** :

- The traffic lights must work with the order mentioned in the picture above.

- The two traffic lights at **lane 1** can be **green** and the **rest are red**.

- The two traffic lights at **lane 2** can be **green** and the **rest are red**.

- The traffic light at **lane 3** can be **green** and the **rest are red**.

- The traffic light at **lane 4** can be **green** and the **rest are red**.

- The traffic light at **lane 5.x** allows cars to **return when it is not conflict with another traffic light**.


## Tools

The Tool That We Are Use For Petri Nets Modeling :

https://apo.adrian-jagusch.de/

## Example Of Modeling The Traffic Sign

![App Screenshot](https://cdn.discordapp.com/attachments/908279454621651015/1041350233034084352/Capture1.PNG)


## .apt

import it in apo.adrian-jagusch.de website

```bash
.name "TrafficSign"
.type PN

.places
t1.green
t1.red
t2.red
t2.green
t3.red
t3.green
t4.red
t4.green
t5.1.green
t5.1.red
t5.2.green
t5.2.red
t5.3.red
t5.3.green
sync2
sync3
sync4
sync1

.transitions
r2g
g2r
r2g
g2r
g2r
r2g
g2r
r2g

.flows
r2g: {1*t1.red, 1*t5.1.red, 1*sync1} -> {1*t1.green, 1*t5.1.green}
g2r: {1*t1.green, 1*t5.1.green} -> {1*t1.red, 1*t5.1.red, 1*sync2}
r2g: {1*t2.red, 1*sync2} -> {1*t2.green}
g2r: {1*t2.green} -> {1*t2.red, 1*sync3}
g2r: {1*t3.green, 1*t5.2.green} -> {1*t3.red, 1*t5.2.red, 1*sync4}
r2g: {1*t3.red, 1*t5.2.red, 1*sync3} -> {1*t3.green, 1*t5.2.green}
g2r: {1*t4.green, 1*t5.3.green} -> {1*t4.red, 1*t5.3.red, 1*sync1}
r2g: {1*t4.red, 1*t5.3.red, 1*sync4} -> {1*t4.green, 1*t5.3.green}

.initial_marking {1*t1.red, 1*t2.red, 1*t3.red, 1*t4.red, 1*t5.1.red, 1*t5.2.red, 1*t5.3.red, 1*sync1}

```
    





