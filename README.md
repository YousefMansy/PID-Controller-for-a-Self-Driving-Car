[//]: # (Image References)

[image1]: ./pictures/left_turn_1.gif "left_turn_1"
[image2]: ./pictures/right_turn_1.gif "right_turn_1"
[image3]: ./pictures/P_high.gif "P_high"
[image4]: ./pictures/P_low.gif "P_low"
[image5]: ./pictures/I_high.gif "I_high"
[image6]: ./pictures/D_low.gif "D_low"
[image7]: ./pictures/D_high.gif "D_high"

# PID-Controller-for-a-Self-Driving-Car
The goal of this project is to implement a PID controller in C++ to maneuver a self-driving vehicle around a track!

![alt text][image1] ![alt text][image2]

In this project, the car uses two PID controllers for controlling both the steering angle and the throttle of the vehicle.

## Effects of each of the PID components

### The P component
The P component is responsible for increasing/decreasing the controlled value as long as the error value is higher than 0. The error value here is represented the distance of the car from the lane center, or the cross-track error (CTE).

This component was set to a small value so that the controlled values change at a small increments so as to arrive at the 0 error.

Here we can see the effect of using a high P value on the steering controller. The value used is 1.

![alt text][image3]

On the other hand, here we can see the effect of using a very low P value of 0.001.

![alt text][image4]

### The I Component
The I component is used to overcome the effects of bias, such as steering drift. When using the simulator, there was close to no bias in the values, so the I final value was set very close to 0.

Here we can see the effect of increasing the I component to 1.

![alt text][image5]

### The D Component
The D component, is responsible for dampening the effect of change made by the P component as much possible as the value of error approaches 0. In other words, it helps decrease the steering angle as the car as gets closer to the lane center. Without this component, the P component would cause overshoot, possibly causing oscillations around the lane center.

Here we can see the effect of using a D value that is too low. The value used is 0.5.

![alt text][image6]

And here we can see the effect of using a D value that is too high. The value used is 10.

![alt text][image7]

### The final tuned PID gains used were as follows
```
PID steering_pid(0.116, 0.0005, 3.81);
PID throttle_pid(0.188, 0.00002, 1.98);
```  
The values were tuned manually.
