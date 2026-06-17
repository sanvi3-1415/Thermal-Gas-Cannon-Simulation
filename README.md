# Thermal Gas Cannon Experiment

**Visualizing the Maxwell Velocity Distribution via Projectile Kinematics**

This project visually demonstrates how the chaotic, invisible thermal velocities of an ideal gas adhere to a Normal Distribution. By allowing gas to escape a thermal bath in a vacuum and subjecting it to gravity, we physically map velocity directly to spatial distance.

## ⚙️ Interactive Simulation

You can run the live interactive simulation by opening `index.html` in any modern web browser. The simulation allows you to dynamically adjust Temperature ($T$), Gas Particle Mass ($m$), Gravity ($g$), and Total Particle Count ($N$).

## 📚 Theoretical Framework & Derivation

### 1. Visualization & Graph Scaling
The vertical bars in the simulation represent physical counts (frequencies) of particles, not direct probabilities. To accurately compare the theoretical Normal distribution to the physical histogram, we must scale the probability density function, $f(x)$.

For a continuous probability density function, the probability of a particle landing in a small interval of width $\delta$ (the bar size) is approximately the area under the curve in that interval: **Probability $\approx f(x) \times \delta$**.

In statistics, **Relative Frequency** is defined as the number of successful observations (particles in a specific bar, $n$) divided by the total number of trials (total particles dropped, $N$). By the Law of Large Numbers, relative frequency approaches probability as $N$ increases:

$$\text{Relative Frequency} = \frac{n}{N} \approx \text{Probability}$$
$$\frac{n}{N} \approx f(x) \times \delta$$
$$n \approx N \times f(x) \times \delta$$

Therefore, the dotted curve plots the expected count: $N \times f(x) \times \text{bar size}$. This allows the mathematical envelope to grow dynamically alongside the accumulating particles.

### 2. The Velocity Distribution
Imagine a gas without any overall flow. The molecules are moving randomly. To find the distribution of velocities, we set up three axes $x$, $y$, and $z$. The velocity is expressed as $(V_1, V_2, V_3)$. Since there is no overall flow and no favored direction, $V_1, V_2$, and $V_3$ must be independent and identically distributed (IID).

Assuming each $V_i$ has a density $f$, the joint density is $f(v_1)f(v_2)f(v_3)$. This cannot depend on the direction, meaning it depends only on the magnitude squared $(v_1^2 + v_2^2 + v_3^2)$. Thus, for some function $g$:

$$f(v_1)f(v_2)f(v_3) = g(v_1^2 + v_2^2 + v_3^2)$$

Assuming $f$ is differentiable, we differentiate both sides partially with respect to $v_i$:

$$\frac{f'(v_1)f(v_2)f(v_3)}{v_1} = \frac{f(v_1)f'(v_2)f(v_3)}{v_2}$$
$$\frac{f'(v_1)}{v_1 f(v_1)} = \frac{f'(v_2)}{v_2 f(v_2)}$$

Since $v_1$ and $v_2$ are arbitrary, this ratio must equal a constant, $k$. Solving the differential equation $\frac{f'(x)}{x f(x)} = k$ yields:

$$\log f(x) = \frac{kx^2}{2} + C \implies f(x) \propto e^{kx^2/2}$$

To formally identify this distribution, we compare it to the probability density function of a Normal Distribution, $N(\mu, \sigma^2)$:

$$f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$$

By comparing the exponents, it is clear that $\mu = 0$. Furthermore, the coefficient of $x^2$ gives us $\frac{k}{2} = -\frac{1}{2\sigma^2}$, which means $\sigma^2 = -1/k$. Since $f$ is a density, its total integral must be $1$, requiring $k < 0$. Therefore, the velocity exactly follows a **$N(0, -1/k)$** distribution.

### 3. Newtonian Mechanics and Pressure
To find the constant $k$, we evaluate the pressure exerted by the gas using pure Newtonian mechanics. Consider a cubical element of side length $L$ and volume $V = L^3$. A particle of mass $m$ moving with velocity $v_x$ collides elastically with the wall and bounces back.

The change in momentum is $\Delta p = mv_x - (-mv_x) = 2mv_x$. The particle must travel distance $2L$ (back and forth) before hitting the same wall again, so the time between collisions is $\Delta t = \frac{2L}{v_x}$. By Newton's Second Law, the average force exerted by this single particle is:

$$F = \frac{\Delta p}{\Delta t} = \frac{2mv_x}{2L / v_x} = \frac{mv_x^2}{L}$$

The total pressure $P$ is the total force of all $N_{total}$ particles divided by the wall's area ($A = L^2$). We use the mean square velocity $\overline{v_x^2}$ to represent the average over all particles:

$$P = \frac{N_{total} \cdot m \cdot \overline{v_x^2} / L}{L^2} = \frac{N_{total} m \overline{v_x^2}}{V}$$

Equating this with the macroscopic Ideal Gas Law ($PV = N_{total} k_B T$):

$$\frac{N_{total} m \overline{v_x^2}}{V} = \frac{N_{total} k_B T}{V} \implies m \overline{v_x^2} = k_B T \implies \overline{v_x^2} = \frac{k_B T}{m}$$

From our $N(0, -1/k)$ distribution, the variance is strictly equal to the mean square velocity $\overline{v_x^2}$. Therefore, $-\frac{1}{k} = \frac{k_B T}{m}$, which solves to **$k = -\frac{m}{k_B T}$**.

### 4. Projectile Kinematics
Once a particle exits the thermal chamber at height $H$, thermodynamics ends and deterministic kinematics takes over. We calculate the time of flight using Newton's second equation of motion:

$$s = ut + \frac{1}{2}at^2$$

In the vertical direction, the initial velocity is zero ($u_y = 0$), the acceleration is downward gravity ($a = g$), and the displacement is the height of the fall ($s = H$). Substituting these values:

$$H = 0 \cdot t + \frac{1}{2}gt^2 \implies t = \sqrt{\frac{2H}{g}}$$

In the horizontal direction, gravity exerts no force, meaning the horizontal acceleration is zero ($a_x = 0$). Thus, the horizontal velocity $v_x$ remains perfectly constant throughout the flight. The final landing range $X$ is the horizontal velocity multiplied by the time of flight:

$$X = v_x \cdot t = v_x \sqrt{\frac{2H}{g}}$$
