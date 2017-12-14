# Component recognition

Author: Leslie Lee ([LeeChunHei](https://github.com/LeeChunHei))

Credit: HKUST Robotics Team Electronic Tutorial

This tutorial will teach you how to recognize all basic components

## Component package technology

There are mainly two type of packaging

### Through-hole technology

There will be some through-hole conductive legs surrounded the component. You can solder this kind of component by matching the legs to the hole and place solder on it.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/through_hole.jpg)

### Surface-mount technology (SMD)

There will be no through-hole legs surrounded the component and holes on the board. The conductive part of the component will just need to mount on the surface of the pad on the board. You just need to place the component on the footprint on the board and place solder to secure it.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/smd.jpg)

And the component size of two terminal package is called in the following way.

| Size | dimensions, length * width |
| :--: | -------------------------- |
| 0201 | 0.6mm * 0.3mm              |
| 0402 | 1.0mm * 0.5mm              |
| 0603 | 1.6mm * 0.8mm              |
| 0805 | 2.0mm * 1.25mm             |
| 1008 | 2.5mm * 1.25mm             |
| 1206 | 3.2mm * 2.5mm              |
| 1812 | 3.2mm * 2.5mm              |

## Resistor

A resistor is a two terminals electronic component which is designed for producing a
specific voltage drop across the terminals. It is manufactured with a specific value of ohm(Ω). The most common resistors are carbon-composition and wire-wound type. The primary characteristics of resistors are resistance value, power rating, tolerance, temperature coefficient and noisy figure.

### Marking

For axial resistors 2W or less, use a pattern of colored bands or stripes to indicate
resistance. Large power rating resistors and surface-mount resistors are marked
numerically if the size is big enough to allow marking.

### Color codes for Four-band axial axial resistors

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/through_hole_res.jpg)

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/color_code.png)

Remark: 1st band is wider than others with axial leads. If resistors have color stripes and axial leads, body color is not used for color-coded value. If a resistor has five stripes, the fourth stripe is the multiplier and the fifth is the tolerance.

### Numeric codes for three digits Surface mount device (SMD) resistors

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/smd_res.jpg)

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/smd_resis_num_code.jpg)

## Capacitor

A capacitor is formed by two conductors surrounding an insulator. When a voltage potential difference is between the conductors of a capacitor, an electric field is present in the dielectric. This field stores energy and produces a force between plates. A capacitor is manufactured with specific value of farads(F). In practical, one farad is very large. The most commonly used multiples and submultiples of capacitors are microfarad(μF), nanofarad(nF) and picofarad(pF).

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/type_cap.jpg)

Ceramic capacitors have stripes or dots with three or five colors. When there are five colors, the first and last indicate the temperature coefficient and tolerance respectively. The middle three colors give the value in picofarads(pF).

### Color code for ceramic capacitors

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/through_hole_cap.jpg)

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/cap_color_code.jpg)

### Surface mount device (SMD) capacitor

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/smd_cap.jpg)

Most of SMD capacitors are too tiny to have a marking on it. The capacitance & other information can be found on the reels or packing. If the space is enough for making on it, sometimes a non-standard coding is used, datasheet should be check for more detailed information.

### Electrolytic Capacitor

Unlike ceramic capacitors, electrolytic capacitors have specified polarities. Electrolytic capacitors have very high capacitances and ESR and are usually used for rectifying power nets; Beware of the polarity where usually the negative terminal will be marked.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/cap_sign.jpg)

**Never reverse the polarity or apply a voltage higher than that specified on the package or there will be risk of explosion.**

### Tantalum Capacitor

Tantalum capacitor is less commonly used due to its expensiveness and a lack of necessity. However, there may be some occasions where tantalum capacitors are deployed and extreme care must be taken. Tantalum capacitors have high capacitance-to-volume ratio and a ESR in between ceramic and electrolytic capacitors. However, it is extremely prone to explosion under abnormal usage or near-borderline working conditions.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/tantalum_cap.jpg)

Note that the markings on a tantalum capacitor is opposite to an electrolytic capacitor, where the strip indicates a positive terminal.

**Applying any voltage below the negative terminal on the positive terminal, or any voltage higher than 80% of the rated voltage (±20% tolerance), will cause an explosion.**

## Inductor

Inductor is a passive two-terminal electrical component that stores electrical energy when electric current flows through it. It is similar to the opposite of a capacitor. It will filter high frequency noise.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/through_hole_inductor.jpg)

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/smd_inductor.jpg)

## Diode

Diode is a semiconductor based device categorized as an active device. It only allows one direction current through the device, named forward biased condition. In common, a forward bias (Vd) requires about 0.7 volts to break over to the conduction mode; in reverse bias, nearly no current through the device except while maximum reverse voltage applies on the diode (Vbr).

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/diode.jpg)

## Light Emitting Diode(LED)

A LED is a light source device and widely used in interface between human & electronic product to indicate or display some information. LEDs are available in visible, ultraviolet and infra-red wavelengths with very high brightness. The outlook of Infra-red(IR) LED and visible light LED are the same. Use a digital camera capture a photo to identify a switch on IR LED.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/led.jpg)

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/led_package.jpg)

Remark: The terminal pointed by the small triangle at the bottom of the led is the negative terminal

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/led_footprint.PNG)

Remark: The pad with line marking on the white oil footprint is the negative terminal, put the negative terminal of the led on it. 

## Transistor

A transistor is a semiconductor based device categorized as an active device. It is an electronic switch controlled by voltage or current applied on terminals. There are two types of transistor commonly use – Bipolar junction
transistors(BJT) & Field effect transistors (FET). The following are “ON” condition of BJT. 

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/transistor.jpg)

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/transistor1.jpg)

## Regulator

A voltage regulator is an electronic circuit that provides a stable dc voltage by stepping up or down the voltage from the supply voltage.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/through_hole_regulator.jpg)

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/smd_regulator.jpg)

Remark: Read the datasheet to control the output voltage of adjustable voltage regulator.

## Connector

Besides the above basic components, you also need to deal with different type of connector.

For each type of connector, there will be female and male version.

### Female version

Female version of connector always uses on supply side, which means, female connector will use at the side that giving out electricity, like the battery side. Female version of connector is used in supply side is because there are insulated material protected the metal pin of the connector, this can prevent the connector short circuit can causes serious consequence.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/female_connector.JPG)

### Male version

So male version of connector is used on the receiver side, as receiver side don't afraid of short circuit when there is no power supply. And feature of male connector is no insulated material between pins.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/male_connector.jpg)

**DON'T mix up male and female connector when you are doing wiring**

And following is the connector you will meet the most in the lab

### T Plug

T plug is a connector with two thick copper terminal, we will use it at power connection.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/t_plug.jpg)

### Multi-pin Header

Multi-pin header is a connector with multiple pins, we will use it at signal connection.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/multi_pin_header_male.jpg)

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/multi_pin_header_female.jpg)

### XT60

XT60 is a connector also with two thick copper terminal like T plug, but it's more secure than T plug.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/xt60.jpg)

