# Thermal Gas Cannon Experiment

**Visualizing the Maxwell Velocity Distribution via Projectile Kinematics**

This project visually demonstrates how the chaotic, invisible thermal velocities of an ideal gas adhere to a Normal Distribution. By allowing gas to escape a thermal bath in a vacuum and subjecting it to gravity, we physically map velocity directly to spatial distance.

## ⚙️ Interactive Simulation

You can run the live interactive simulation by opening `index.html` in any modern web browser. 

The simulation allows you to dynamically adjust:
* **Temperature ($T$)**
* **Gas Particle Mass ($m$)**
* **Gravity ($g$)**
* **Total Particle Count ($N$)**

## 📚 Theoretical Framework & Derivation

### 1. The Origin of Pressure (Kinetic Theory)
Before applying statistics, we must derive the physical meaning of Temperature from pure Newtonian mechanics. Imagine a cubical container of side length $L$ and volume $V$. A single particle of mass $m$ moving with horizontal velocity $v_x$ bounces elastically off the wall.

The change in momentum during the collision is $\Delta p = 2mv_x$. The time between collisions with the same wall is $\Delta t = 2L / v_x$. By Newton's Second Law, the force exerted by one particle is:

$$F = \frac{\Delta p}{\Delta t} = \frac{2mv_x}{2L/v_x} = \frac{m v_x^2}{L}$$

Summing the forces of all $N$ particles and dividing by the area $A = L^2$ gives the macroscopic Pressure $P$. We use the "mean square velocity" $\overline{v_x^2}$ to represent the average of all particles:

$$P = \frac{F_{total}}{A} = \frac{N m \overline{v_x^2}}{L^3} = \frac{N m \overline{v_x^2}}{V}$$

### 2. Finding the Maxwell Constant '$k$'
The Ideal Gas Law is observationally known to be $PV = N k_B T$, where $k_B$ is the Boltzmann constant. By equating this with our mechanical derivation of pressure, we find:

$$\frac{N m \overline{v_x^2}}{V} = \frac{N k_B T}{V}$$

$$m \overline{v_x^2} = k_B T \implies \overline{v_x^2} = \frac{k_B T}{m}$$

From probability theory, if the gas velocity is perfectly random and symmetric, the distribution of $v_x$ must be a Normal Distribution centered at 0. The probability density function is known to take the form $f(x) \propto e^{kx^2/2}$. In probability, the variance of this distribution is strictly $-1/k$.

Since the mean velocity is 0, the Variance is exactly equal to the Mean Square Velocity ($\overline{v_x^2}$). Therefore:

$$\text{Variance} = \overline{v_x^2} = -\frac{1}{k}$$

$$\frac{k_B T}{m} = -\frac{1}{k} \implies k = -\frac{m}{k_B T}$$

Substituting $k$ back into the density function yields the exact Maxwell Distribution for 1D velocity!

### 3. The Physical Mapping (Simulation Logic)
In the simulation, particles are fired horizontally from height $H$. Once they leave the slit, they are purely Newtonian projectiles. The vertical time of flight is identical for every particle:

$$t = \sqrt{\frac{2H}{g}}$$

The horizontal landing distance $X$ is simply the thermal velocity multiplied by this constant time:

$$X = v_x \cdot \sqrt{\frac{2H}{g}}$$

A fundamental theorem of statistics states that multiplying a Normally distributed variable ($v_x$) by a constant ($\sqrt{2H/g}$) results in another Normal Distribution. The simulation physically constructs this: the height of the particle stacks on the floor forms a perfect spatial bell curve.

### 🔍 A Note on Visualization
* **The Dynamic Curve:** The dotted orange line does not plot the raw probability density function $f(x)$ (which always has a total area of 1). Since the physical bars represent the absolute count of particles, the mathematical curve is scaled to match. The curve plots the expected count per bin: **$\text{Expected Count} = N \times f(x) \times \text{bin width}$**.
* **The Central Bin:** The central gas cannon is designed to be exactly one histogram bin wide. Particles are emitted from the left and right edges. This guarantees that only the $x=0$ bin remains unoccupied, while the rest of the distribution forms symmetrically. The vertical bins represent mathematical frequency tallies, not solid obstacles, allowing particles to visually pass through them.
