## MPC based ACC using Matlab
A Model Predictive Control (MPC) approach is implemented on a basic Adaptive Cruise Control (ACC) system. A vehicle is moving with a constant velocity and an ego vehicle approaches the leading vehicle and should maintain the same velocity. Using an MPC controller, the required stability with the specified input constraints and the target velocity for a constant preceding vehicle velocity is achieved. Through simulations in MATLAB, it is shown that the proposed MPC strategy can maintain a vehicle in designated constraints.

### Adaptive Cruise Control in literature
ACC is an enhancement of the conventional cruise control which is currently standardized in most modern commercialized vehicles. The purpose of a classical cruise control is to maintain longitudinal vehicle velocity by tracking the velocity as requested by the driver. In ACC, there is an additional tracking of the velocity of the vehicle ahead and adapting to it, by accelerating or braking the vehicle independently of the driver. Typically, an external sensor such as a radar is used to detect the vehicle ahead and measure relative velocity between the vehicles [1].


### Vehicle Model
The host vehicle and target vehicle are modelled as in Figure 1 with a relative distance. Since the purpose of ACC is to maintain a desired distance between host and lead vehicle, a problem of the below considerations is taken,
	The distance error δ_d, defined as difference between the inter-vehicle distance d and desired distance d_r, where δ_d=d-d_r. This error should converge to zero.
	The velocity error δ_v, defined as the difference between the preceding lead vehicle velocity v_p and ego velocity v_h. This error also should converge to zero.
	Acceleration of the ego vehicle v ̇_h, which should also converge to zero.
A vehicle dynamics model is also considered to design MPC and analyze the controller performance.

![fig1](https://user-images.githubusercontent.com/81799459/205553887-67acac7d-33b6-47de-b9c1-5f5876d2490d.jpg)


Figure 1. Example of ACC working principle. The ego vehicle, driving with velocity v_h and acceleration a_h, is equipped with ACC, which measures the preceding lead vehicle, with velocity v_p. A radar measures the distance d_r and the relative velocity v_r=v_p-v_h between the vehicles. [1]


### MODEL PREDICTIVE CONTROL DESIGN
In this section, a model predictive control method is designed to maintain a constant distance between the lead and ego vehicle. We use the method of regulation of system using state-based MPC. To solve the MPC problem at every iteration, we define a general cost function as given in [2]. 
Here, δ_d, δ_v and v ̇_h must be controlled to converge to the origin for a given control input command. The states considered must be constrained to meet the required distance and velocity between the vehicles.


### NUMERICAL SIMULATION
Initial ego acceleration v ̇_0 is set to 15 m2/s. To simulate the MPC controller, the Quadratic Programming (QP) in MATLAB is used as the cost function is quadratic and the constraints are linear. The QP solver available are active-set and interior-point methods and the MATLAB built-in solver interior-point-convex is used.


### MPC Output
As seen in the figure (2), the MPC controller can minimize δ_d. Negative δ_d does not imply that the vehicle crashes into the other, however, it implies that the difference between maintained distance (equal to specified limit of say 4m) and actual distance is zero. v_p maintains a constant velocity of 15 m/s. The δ_v and v ̇_h also converges to zero in a short period of time. A negative δ_v implies that the both the cars are moving towards each other with zero velocity error implying that they travel with the same velocity after some time.

![fig2](https://user-images.githubusercontent.com/81799459/205554802-cdbc623f-30ab-49f9-b6ef-85f606f5d67a.jpg)


Figure 2. MPC Result


### CONCLUSIONS
A Model Predictive Controller for a basic version of Adaptive Cruise Control is implemented. The controller can achieve the required stability and ensure that the distance between the car is minimized to a short time.

#### REFERENCES

[1] G.J.L. Naus, J. Ploeg, M.J.G. Molengraft, van de, W.P.M.H. Heemels, and M. Steinbuch. Design and implementation of parameterized adaptive cruise control: an explicit model predictive control approach. Control Engineering Practice, 18(8):882–892, 2010.

[2] J. Rawlings, D.Q. Mayne, and Moritz Diehl. Model Predictive Control: Theory, Computation, and Design. Nob Hill Publishing, 01 2017.

[3] https://de.mathworks.com/help/mpc/ref/adaptivecruisecontrolsystem.html





