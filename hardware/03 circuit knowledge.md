# Circuit Knowledge

Author: Leslie Lee ([LeeChunHei](https://github.com/LeeChunHei))

This tutorial will teach you some basic circuit.

## Pull UP

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/human_pull_up.jpg)

Pull up circuit is a circuit that a pull-up resistor connect the logic signal to high potential. It keeps the logic level of signal to high when the state is not set.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/pull_up.png)

## Pull Down

Pull down circuit is similar to pull up circuit, but there is a pull-down resistor connect the logic signal to ground instead. It keeps the logic level of signal to low when the state is not set.

![](https://github.com/hkust-smartcar/tutorials/raw/master/hardware/img/pull_down.png)

## Debounce

Debounce circuit consists of resistors and capacitor. There is a pull up resistor, it ensures the logic level is high when the state is not set and charge the capacitor. So when the signal is bouncing, the capacitor will 