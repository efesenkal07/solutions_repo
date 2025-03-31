# Problem 1

# Investigating the Range as a Function of the Angle of Projection

## Motivation

Projectile motion is a fascinating area of physics that involves analyzing the trajectory of an object launched into the air. Although the problem of projectile motion seems simple at first glance, it is a rich and complex topic when analyzed in depth. The goal of this task is to investigate how the range of a projectile depends on its angle of projection. The equations governing projectile motion exhibit both linear and quadratic relationships, making them accessible yet deeply insightful.

By exploring this topic, we gain insight into the behavior of a variety of real-world phenomena, ranging from the arc of a soccer ball to the trajectory of a rocket. The problem is influenced by several factors, including the initial velocity of the projectile, gravitational acceleration, and launch height, all of which lead to a diverse set of solutions.

## Task Breakdown

### 1. Theoretical Foundation

#### Deriving the Governing Equations of Motion

Projectile motion can be broken down into two components: horizontal and vertical motion. These components are influenced by different forces, and the equations governing them are derived from Newton's laws of motion.

The motion in the horizontal direction (x-axis) is given by:

$$
x(t) = v_0 \cdot \cos(\theta) \cdot t
$$

Where:
- \( x(t) \) is the horizontal position at time \( t \),
- \( v_0 \) is the initial velocity of the projectile,
- \( \theta \) is the angle of projection,
- \( t \) is the time elapsed.

The vertical motion (y-axis) is governed by the equation:

$$
y(t) = v_0 \cdot \sin(\theta) \cdot t - \frac{1}{2} g \cdot t^2
$$

Where:
- \( y(t) \) is the vertical position at time \( t \),
- \( g \) is the acceleration due to gravity (\( g = 9.81 \, m/s^2 \) on Earth).

#### Time of Flight

To find the time when the projectile hits the ground, we set \( y(t) = 0 \). Using the vertical motion equation:

$$
0 = v_0 \cdot \sin(\theta) \cdot t - \frac{1}{2} g \cdot t^2
$$

This simplifies to:

$$
t = \frac{2 v_0 \cdot \sin(\theta)}{g}
$$

Thus, the time of flight \( T \) is given by:

$$
T = \frac{2 v_0 \cdot \sin(\theta)}{g}
$$

#### Range

The range of the projectile, \( R \), is the horizontal distance traveled when it hits the ground. Using the horizontal motion equation and the time of flight, we find the range as:

$$
R = v_0 \cdot \cos(\theta) \cdot T
$$

Substituting \( T \) from the previous equation:

$$
R = \frac{v_0^2 \cdot \sin(2\theta)}{g}
$$

This is the standard equation for the range of a projectile launched from the ground. The range depends on the initial velocity \( v_0 \), the gravitational acceleration \( g \), and the angle of projection \( \theta \).

### 2. Analysis of the Range

#### Dependence on the Angle of Projection

The range equation 

$$ 
R = \frac{v_0^2 \cdot \sin(2\theta)}{g} 
$$

 reveals that the range is a function of 
 
 $$ 
 sin(2\theta) 
 $$
 
 . Therefore, the range is maximized when 
 
 $$ 
 \sin(2\theta) = 1 
 $$
 
 , which occurs when 
 
 $$
  \theta = 45^\circ 
  $$
  
  . This means that, for a given initial velocity, the optimal angle for achieving the maximum range is 45 degrees.

#### Influence of Initial Velocity and Gravitational Acceleration

- **Initial velocity (\( v_0 \))**: The range increases with the square of the initial velocity. Doubling the initial velocity will quadruple the range.
- **Gravitational acceleration (\( g \))**: The range is inversely proportional to gravitational acceleration. In locations with lower gravity, such as the Moon, the range would be significantly larger compared to Earth.

### 3. Practical Applications

The basic projectile motion model can be applied to various real-world situations, such as:
- **Sports**: Understanding the trajectory of balls in games like soccer, basketball, or golf.
- **Engineering**: Designing missiles, rockets, or water fountains.
- **Astrophysics**: Analyzing the motion of meteoroids or spacecraft.

#### Launch on Uneven Terrain

For projectiles launched on uneven terrain, the initial height of launch \( h_0 \) must be considered. The equation for the vertical motion becomes:

$$
y(t) = h_0 + v_0 \cdot \sin(\theta) \cdot t - \frac{1}{2} g \cdot t^2
$$

In this case, the projectile will have a different time of flight and range depending on the launch height.

#### Air Resistance

Air resistance can significantly alter the trajectory of a projectile, especially at high speeds. In the presence of air resistance, the equations of motion become more complex, requiring numerical methods to solve. The drag force \( F_d \) is proportional to the square of the velocity:

$$
F_d = \frac{1}{2} C_d \rho A v^2
$$

Where:
- \( C_d \) is the drag coefficient,
- \( \rho \) is the air density,
- \( A \) is the cross-sectional area of the projectile,
- \( v \) is the velocity of the projectile.

### 4. Implementation

To simulate projectile motion and visualize the range as a function of the angle of projection, we can write a Python script to compute and plot the range for various angles of projection.

```python
import numpy as np
import matplotlib.pyplot as plt

# Define constants
g = 9.81  # gravitational acceleration (m/s^2)
v_0 = 20  # initial velocity (m/s)

# Function to calculate range
def calculate_range(v_0, theta_deg):
    theta = np.radians(theta_deg)  # Convert angle to radians
    R = (v_0**2 * np.sin(2*theta)) / g  # Range equation
    return R

# Generate an array of angles
angles = np.linspace(0, 90, 500)
ranges = [calculate_range(v_0, angle) for angle in angles]

# Plot the range as a function of the angle of projection
plt.figure(figsize=(10, 6))
plt.plot(angles, ranges, label=f'v0 = {v_0} m/s')
plt.title('Projectile Range as a Function of the Angle of Projection')
plt.xlabel('Angle of Projection (degrees)')
plt.ylabel('Range (meters)')
plt.grid(True)
plt.legend()
plt.show()
