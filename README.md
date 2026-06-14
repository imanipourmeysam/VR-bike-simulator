<h1> VR bike simulator </h1> 

I developed this VR bike simulator during my PhD doctoral research at university of Paris-Saclay in laboratory of ESTACA.
The bike simulator was used in two research projects.

1) assessment of the validity of VR bike simulator for eHMIs evaluation.
2) evaluating road layout design and its impact oncyclists' mental work load. 

You can find more information on the validation method of the bike simulator via my published paper and thesis report:

https://www.sciencedirect.com/science/article/pii/S2950105925000488

https://theses.fr/2026UPAST053
 
<h2>

<b> A video demo of the bike simulator and immersion in the VR environment. </b>

https://github.com/user-attachments/assets/1778a7d2-4b64-4f21-8617-2074ad2387d3
</h2>

<h2> <b> bike simulator architecture </b> </h2>

<p> the developed bike simulator uses bicycle kinematic model for motion simulation and 1D resistance model based on wind and rolling resistances for deceleration functionality. 
</p>

<p> Figure 1. shows the global architecture of the bike simulator.</p>
<figure>
  <img width="1065" height="317" alt="image" src="https://github.com/user-attachments/assets/d7a2d859-0b52-4a40-893f-28eba25f01f3" />
  <figcaption>
    
   Figure 1.  Bike simulator architecture.
  </figcaption>
</figure>


<p> the kinematic model compute the VR bicycle location in the VR environemnt based on cyclists' speed and steering angle inputs.</p>
<figure>
  <img width="260" height="240" alt="Bicycle simulator architecture"
       src="https://github.com/user-attachments/assets/23374d32-c4ca-4e7d-85fd-4dc1d9335be1" />
  <figcaption>
    
   Figure 2.  Kinematic model of the bike simulator.
  </figcaption>
</figure>



The mathematical formulation of the bicycle kinematic model is defined as follows. Let:

- 𝛿 denote the steering angle of the front wheel.
- ICR denote the instantaneous center of rotation.
- 𝑣 denote the longitudinal velocity (bicycling speed).
- 𝑑 denote the wheelbase length.
- φ denotes the yaw angle.

The kinematic equations of the bicycle model are defined as:

𝑥̇ = 𝑣. cos⁡(𝜑)

𝑦̇ = 𝑣. sin⁡(𝜑)

𝜑̇ =  $\frac{v}{d} \cdot \tan(\delta)$

Given the sampling time 𝛥𝑡 in the VR software, these kinematic
equations can be discretized as follow:

𝑥(𝑡 + 1) ⁡ = 𝑥(𝑡) + 𝑥̇ ⋅ 𝛥𝑡

𝑦(𝑡 + 1) = 𝑦(𝑡) + 𝑦̇ ⋅ 𝛥𝑡

𝜑(𝑡 + 1) = 𝜑(𝑡) + 𝜑̇ ⋅ 𝛥𝑡

The 1 dimensional resistance model computes the total resistance amount to be written to the home trainer based on braking intensity and natural deceleration including braking and rolling resistances.

For braking intensity, two resistive sensors were installed between the brake pads (see figure 2).

<figure>
 <img width="260" height="240"
      src="https://github.com/user-attachments/assets/ae60d71a-e43f-4b3e-ac48-ef09611698e7" />
  <figcaption>
    
   Figure 3.  resistive sensor to compute braking intensity.
   
  </figcaption>  
</figure>

The total resistance was computed via the following formula:

𝑅𝑡𝑜𝑡𝑎𝑙 = 𝛼⁡. 𝑅𝑝𝑎𝑠𝑠𝑖𝑣𝑒 + 𝛽. 𝑅𝑎𝑐𝑡𝑖𝑣𝑒

where the 𝑅𝑝𝑎𝑠𝑠𝑖𝑣𝑒 is the sum of wind and rolling resistance, and 𝑅𝑎𝑐𝑡𝑖𝑣𝑒 is the intensity of braking computed via the resistive sensors.

𝛼⁡ and 𝛽 are experimental factors to adjust braking and deceleration amount based on user feedbacks.



