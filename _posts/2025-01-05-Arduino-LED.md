---
layout: single
title: "[Arduino Tutorial] 1. LED"
categories: Arduino
tags: [arduino, tutorial] 
toc: true
# author_profile: false
# sidebar:
#     nav: "docs"
---
In this blog, we will take a look how to reprogram the UNO R3 board and control the 'L' LED on the board. Next, we will control the brightness of an external LED by using different values of resistor. Finally, we will control the color of an RGB LED by writing a new sketch.<br>

# Lesson 1: Arduino's built-in LED
The UNO R3 board which I have has a single LED that we can control from our sketches (by using Arduino IDE). This LED is built onto the UNO R3 board and is referred to as the 'L' LED as this is how it is labeled on the board.<br>
![byte-of-byeori]({{site.url}}\images\2025-01-05-Arduino-LED\built-in-LED.jpg)<br>
Before we write our sketch in order to control this 'L' LED, we need to connect our UNO R3 board to a USB port on our computer. Then we can find that our UNO R3 board's 'L' LED already blinks. We can reprogram the board with our own Blink sketch to change the rate at which it blinks. The original 'Blink' sketch is in the IDE's menu system under **File > Examples > 01.Basics**. The example sketches included with the Arduino IDE are 'read-only', so we need to save a copy of the sketch before rewriting it.<br>

Here is the code for the Blink sketch:<br>
``` arduino
// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(1000);                      // wait for a second
  digitalWrite(LED_BUILTIN, LOW);   // turn the LED off by making the voltage LOW
  delay(1000);                      // wait for a second
}
```

Every Arduino sketch must have a 'setup' function. In this case, there is a command in the setup function, which tells the Arduino board that we are going to use the built-in LED pin as an output.<br>

It is also mandatory for a sketch to have a 'loop' function. Inside our loop function, the commands first of all turn the LED pin on (HIGH), then delay for 1000 ms (1 second), then turn the LED pin off (LOW) and pause for another 1000ms. This process will continue until the Arduino board is disconnected to the USB port.<br>

In order to make the LED blinking faster or slower, we have to only change the number of 'delay(1000);'.<br>
For example, we can change the code like this in order to make the blinking faster:<br>
``` arduino
// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(500);                      // wait for a second
  digitalWrite(LED_BUILTIN, LOW);   // turn the LED off by making the voltage LOW
  delay(500);                      // wait for a second
}
```

# Lesson 2: Resistor
We can change the brightness of an LED by using different valuse of resistor.<br>
We need a breadboard, 3 different values of resistor, an Arduino board, an LED and M-M wires (Malte to Male jumper wires). <br>

## Breadboard
With a breadboard we can prototype circuits easily, without having to solder the connections.<br>
![byte-of-byeori]({{site.url}}\images\2025-01-05-Arduino-LED\breadboard.jpg)<br>
Inside the breadboards are strips of metal that provide electrical connection between holes in the columns. Pushing the legs of two different components into the same column joins them together electrically. A deep channel running down the middle indicates that there is a break in connections there. Also, there are two strips of holes running along edges of the board that are separated from the main grid. These strips are referred to as **rails** and they enable us to connect power to components or points in the board.<br>
While breadboards are great for prototyping, the connections are push-fit and temporary, so they are not reliable as soldered connections.

## LED
LEDs use very little electricity and they pretty much last forever. The most common sizes of LEDs are 3 mm, 5 mm and 10 mm, those refer to the diabeter of the LED. I used here a 5 mm red LED. You cannot directly connect an LED to a battery or voltage source because it will burn out without a resistor to limit the amount of current flowing through it.<br>

There are two leads of the LED; one is positive and another is negative. It is simple to recognize, the positive lead is longer.<br>

## Resistors
Resistors resist the flow of electricity. The higher the value of the resistor, the more it resists and the less electrical current will flow through it. We are going to use this to control how much electricity flows through the LED and therefore, how brightly it blinks.<br>

Resistors have different colored stripes on them, which tell you the value of the resistor. The resistor color code has four or five colored stripes.<br>
![byte-of-byeori]({{site.url}}\images\2025-01-05-Arduino-LED\resistor-color-code.JPG)<br>
If you find this too complicated, you can use a digital multimeter instead to measure directly the resistance of the resistor. Unlike LEDs, resistors do not have a positive and negative lead. So they can be connected either way around.



### Define Pins

``` arduino
# define BLUE 3
# define GREEN 5
# define RED 6
```

### Setup function

``` arduino
void setup()
{
pinMode(RED, OUTPUT);
pinMode(GREEN, OUTPUT);
pinMode(BLUE, OUTPUT);

digitalWrite(RED, HIGH);
digitalWrite(GREEN, LOW);
digitalWrite(BLUE, LOW);
}
```