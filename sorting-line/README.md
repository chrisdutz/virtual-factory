# High-Bay Storage

# Modifications

Initially I used the color detector the model comes with.
However, I quickly realized that this doesn't work nicely under varying light conditions.

If I set the values at night, the sorting only worked reliably at night. If I set the values at day, it depended on if it's a sunny or cloudy day.

So I replaced the color-sensor with an OpenMV cam, which I programmed to do an object detection. 
My programming was done in a way, that it used one of the PWM outputs of the camera to mimic the voltage of the original color detection. 

In order to make sure the lighting is always identical I added two LED light bars inside the casing, that I built for the camera and 3d printed the parts needed to mount the camera in it.

Unfortunately using a PWM-analog output doesn't work well if your IOs are too fast. 
I therefore added a 0-24V PWM-to-Analog converter, to convert the pulses into a true analog signal. 
With this I was able to replace the color sensor with the OpenMV version without having to change the PLC program. 

I did however have a few problems with detecting the White token. 
If you think of how it works, it's sort of obvious:
White is the presence of all colors, so if you do your color detection on a certain wave-range being present over a given threshold, it will sort of trigger all of them. 

I know I probably could have come up with a different way of doing things, but I simply ended up with buying some green paint, ordering a spare set of 3 white tokens and painting them green ... problem solved ;-)

# Hardware

For this model I used one of my Siemens S7-1200 devices I had. 
It's the simplest model of the 4. 

Didn't even need any of the 2 fast counters it had, as the model uses a simple switch and a gear for the conveyor movement.

## I/O Connections

Here's how I connected all inputs and outputs to the PLC

### Inputs

- I1: The pulse coming from said switch with a gear for the conveyor movement (As it only moves in one direction, this is enough)
- I2: Light barrier on the intake
- I3: Light barrier after the detection
- A4: Analog signal from the detector
- I5: Light barrier in the green bay
- I6: Light barrier in the red bay
- I7: Light barrier in the blue bay

### Outputs

- Q1: Motor conveyor belt
- Q2: Compressor
- Q3: Valve eject green bay
- Q4: Valve eject red bay
- Q5: Valve eject blue bay

# Configuration of the PLC

## I/O Configuration

# Writing the PLC Programm

