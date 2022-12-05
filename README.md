### MPC based ACC using Matlab
A Model Predictive Control (MPC) approach is implemented on a basic Adaptive Cruise Control (ACC) system. A vehicle is moving with a constant velocity and an ego vehicle approaches the leading vehicle and should maintain the same velocity. Using an MPC controller, the required stability with the specified input constraints and the target velocity for a constant preceding vehicle velocity is achieved. Through simulations in MATLAB, it is shown that the proposed MPC strategy can maintain a vehicle in designated constraints.

### Adaptive Cruise Control in literature
ACC is an enhancement of the conventional cruise control which is currently standardized in most modern commercialized vehicles. The purpose of a classical cruise control is to maintain longitudinal vehicle velocity by tracking the velocity as requested by the driver. In ACC, there is an additional tracking of the velocity of the vehicle ahead and adapting to it, by accelerating or braking the vehicle independently of the driver. Typically, an external sensor such as a radar is used to detect the vehicle ahead and measure relative velocity between the vehicles [1].


### Vehicle Model
The host vehicle and target vehicle are modelled as in Figure 1 with a relative distance. Since the purpose of ACC is to maintain a desired distance between host and lead vehicle, a problem of the below considerations is taken,
	The distance error δ_d, defined as difference between the inter-vehicle distance d and desired distance d_r, where δ_d=d-d_r. This error should converge to zero.
	The velocity error δ_v, defined as the difference between the preceding lead vehicle velocity v_p and ego velocity v_h. This error also should converge to zero.
	Acceleration of the ego vehicle v ̇_h, which should also converge to zero.
A vehicle dynamics model is also considered to design MPC and analyze the controller performance.


![fig2](https://user-images.githubusercontent.com/81799459/205552393-9e3043ee-1926-46e9-87af-eb54493249e8.jpg)
