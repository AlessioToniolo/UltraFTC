## Mastering Control in FTC

Control, or *the ability to enhance the intelligence and function through software*, is what makes a robot great.

In FTC, most robots use *2-4* motors to power the movement of the robot. These motors have ports on them called encoders.

You can plug in a special motor wire in order to access the encoder through code. An encoder sees how many times the shaft, which is

what the wheel is mounted onto, spins. Specifically, it sees what position the encoder is at by couting how many times the shaft makes a full revolution.

![Encoder Configuration Diagram](https://www.pitsco.com/sharedimages/product/ExtraLarge/XL_first_control_hub_cable_conversion_pack_wiring_diagram.jpg)

---

### RUN_USING_ENCODER (RUE)

Using encoders to enhance the autonomous portion of FTC is extremely common due to the number of things you can do with them. This can be done by setting
the mode of the encoder from `RUN_WITHOUT_ENCODER` to `RUN_USING_ENCODER`.

This is located after 
```java
// Retrieves the motor
DcMotor motor = hardwareMap.dcMotor.get("NAME_OF_MOTOR");

//motor.setDirection(DcMotor.Direction.FORWARD);  |  This is optional to change the direction that the motor spins when motor.setPower(1 or -1)

// Resets the value of the encoder (recommended)
motor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);

// Activates RUE
motor.setMode(DcMotor.RunMode.RUN_USING_ENCODER);
```

#### The Concept of PID
You might ask, why would we want to use RUE?

The answer is [PID](https://en.wikipedia.org/wiki/PID_controller). PID is an [algorithim](https://en.wikipedia.org/wiki/Algorithm) that allows
a system, (e.g. motor and encoder) to reach a target based on continuous sensor reading. In FTC, this most commonly means: a motor can reach a target
position by measuring the shaft's position. For example, if we have a motor that controls an arm: it rotates it. Imagine we want to move the arm from 0 degrees
to 90 degrees. With some calculations, we can set the target position of the motor to be the converted value from 90 degrees to an encoder value, and we 
can get the position of the encoder along the way to track how close the motor is from reaching the target. This is called the error, 
`TargetPosition - CurrentPosition`

Here is an explanation of PID controllers for FTC teams:
[![Thumbnail](https://i.ytimg.com/vi/L5MA5BJeYkg/hq720.jpg?sqp=-oaymwEcCNAFEJQDSFXyq4qpAw4IARUAAIhCGAFwAcABBg==&rs=AOn4CLAaXjaPg-JDaRT79eBjQDX8NbdXcA)](https://www.youtube.com/watch?v=L5MA5BJeYkg)

***FOR CRISTO REY TEAMS:***
The base code provided by Marist already utilizes PID. Thinking back to the RUE section, the RUN_USING_ENCODER utilizes the built-in PID (so you don't have to
program the PID loop!) to reach a target encoder position. This is used for going forward/backward, strafing, and turning movements. It is also used for
setting the position of an arm. If you would like further guidance into implementing RUE, feel free to chat me on discord at 

PID can be taken to the next level in FTC, where you can
- Make the PID controller more accurate
- Create a custom PID controller with sensor readings and the math for PID
- Utilizing PID by using the [RoadRunner](https://learnroadrunner.com/) library! 
-   RoadRunner will be explained in depth in a later blog post!

Here is a sneak peak into the cool movements RoadRunner can do! (Download the .mp4 below)
[RoadRunner RR2 Gif](https://learnroadrunner.com/assets/trajectorybuilder-functions/spline-to.mp4)
