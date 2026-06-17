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

$$f(x) = \frac{1}{\sqrt{
