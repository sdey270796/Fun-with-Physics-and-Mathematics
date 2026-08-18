# Visualizing the Trajectory of a Point on a Rolling Ring

> A small physics-meets-Python animation project created purely for fun
> and leisure, turning a familiar mechanics problem into animated
> trajectories.

## 🎯 Project Overview

This project is a playful computational visualization of the path traced
by a point on the circumference of a translating and rotating ring.

The notebook explores the motion through animated plots generated
entirely with Python.

Instead of solving the mechanics problem only algebraically, the project
makes the motion visible:

``` text
Rolling / Translating Ring
          ↓
Track a point on its circumference
          ↓
Calculate x(t) and y(t)
          ↓
Animate the ring
          ↓
Draw the trajectory
          ↓
Save the result as a GIF
```

The project contains three closely related animation experiments:

1.  A **sliding-ring trajectory**
2.  A **rotating-wheel trajectory**
3.  A **rotating-ring trajectory with a title**

It is intentionally a lightweight, recreational project rather than a
formal research or simulation study.

------------------------------------------------------------------------

# 🧠 The Physics Behind It

The notebook considers a ring of radius:

``` text
R = 1
```

moving horizontally with translational velocity:

``` text
v = 2
```

The angular velocity is determined using the no-slip condition:

``` text
ω = v / R
```

For the chosen parameters:

``` text
ω = 2 rad/s
```

A point on the circumference is then tracked as the ring moves.

The notebook calculates its coordinates as functions of time and uses
those coordinates to draw the trajectory.

------------------------------------------------------------------------

# 📐 Parameter Setup

The simulations use:

``` python
R = 1.0
v_translate = 2.0
```

and a time interval of five seconds:

``` python
t = np.linspace(0, 5, 250)
```

The angular velocity is calculated as:

``` python
omega = v_translate / R
```

Thus, the simulation satisfies the assumed no-slip relation between
translational and rotational motion.

------------------------------------------------------------------------

# 📈 Trajectory Equations

The notebook uses trigonometric parametric equations to determine the
position of the tracked point.

For the first animation:

``` python
x_trajectory = v_translate * t + R * np.sin(omega * t)
y_trajectory = R - R * np.cos(omega * t)
```

For the second and third animations:

``` python
x_trajectory = v_translate * t - R * np.sin(omega * t)
y_trajectory = R - R * np.cos(omega * t)
```

The sign difference in the horizontal trigonometric term produces a
different orientation of the resulting trajectory.

The notebook therefore provides a simple opportunity to see how changing
the mathematical description changes the resulting animation.

------------------------------------------------------------------------

# 🎞️ Three Animation Experiments

## 1. Sliding Ring

The first notebook cell generates:

``` text
sliding_ring_trajectory.gif
```

It visualizes a translating ring and the path of a point attached to its
circumference.

The title displayed in the notebook is:

``` text
Trajectory of a Point on a Sliding Ring
```

The tracked point is shown separately from the ring, while its
previously traversed path is retained.

------------------------------------------------------------------------

## 2. Rotating Wheel

The second cell generates:

``` text
rotating_wheel_trajectory.gif
```

This version uses:

``` python
x_trajectory = v_translate * t - R * np.sin(omega * t)
```

and:

``` python
y_trajectory = R - R * np.cos(omega * t)
```

The animation shows the wheel moving while the trajectory of the
selected point is progressively drawn.

------------------------------------------------------------------------

## 3. Rotating Ring with Title

The third cell produces:

``` text
rotating_ring_with_title.gif
```

This is essentially a presentation-oriented version of the second
animation, with the title:

``` text
Trajectory of a Point on a Rotating Ring
```

added to the figure.

------------------------------------------------------------------------

# 🎨 Animation Design

Each animation contains four principal visual elements:

``` text
Ring
  ↓
Tracked point
  ↓
Previously traced path
  ↓
Horizontal surface
```

The ring is represented by a circular curve.

The tracked point is displayed as a red marker.

The trajectory is progressively drawn behind the moving point.

A horizontal line represents the surface on which the ring moves.

The axes are intentionally hidden to keep the visualization clean and
focused on the motion.

------------------------------------------------------------------------

# 🔄 Animation Logic

The animation is generated using Matplotlib's:

``` python
FuncAnimation
```

For every frame, the notebook:

1.  Calculates the current angular position.
2.  Determines the ring's center.
3.  Generates the ring circumference.
4.  Updates the tracked point.
5.  Extends the trajectory path.
6.  Renders the new frame.

Conceptually:

``` text
Frame n
  │
  ├── Ring position
  │
  ├── Ring rotation
  │
  ├── Point position
  │
  └── Trajectory so far
         ↓
      Render frame
         ↓
      Frame n + 1
```

------------------------------------------------------------------------

# 🎥 GIF Generation

The animation contains:

``` text
250 frames
```

and uses:

``` python
interval=20
```

for the animation.

The final GIF is written using:

``` python
PillowWriter(fps=30)
```

For example:

``` python
writer = PillowWriter(fps=30)

ani.save(
    "sliding_ring_trajectory.gif",
    writer=writer
)
```

The same approach is used for the other two animations.

------------------------------------------------------------------------

# 🧩 Core Components

The notebook is intentionally simple and uses only a few Python
components.

### NumPy

Used for:

-   Time arrays
-   Trigonometric calculations
-   Numerical trajectory generation
-   Ring coordinates

### Matplotlib

Used for:

-   Creating the figure
-   Drawing the ring
-   Drawing the point
-   Drawing the trajectory
-   Creating the animation

### PillowWriter

Used to export the animation as a GIF.

------------------------------------------------------------------------

# 🛠️ Technology Stack

  Component               Technology
  ----------------------- ----------------------------
  Programming language    Python
  Numerical computation   NumPy
  Visualization           Matplotlib
  Animation               Matplotlib `FuncAnimation`
  GIF export              `PillowWriter`

------------------------------------------------------------------------

# 🚀 How to Run

## 1. Open the Notebook

Open:

``` text
Physics_problem.ipynb
```

in Jupyter Notebook, JupyterLab, Google Colab, or another compatible
Python environment.

## 2. Install Dependencies

If necessary:

``` bash
pip install numpy matplotlib pillow
```

## 3. Run the Cells

Run the three cells sequentially.

The notebook will generate:

``` text
sliding_ring_trajectory.gif
rotating_wheel_trajectory.gif
rotating_ring_with_title.gif
```

------------------------------------------------------------------------

# 📁 Suggested Repository Structure

``` text
.
├── README.md
├── Physics_problem.ipynb
├── sliding_ring_trajectory.gif
├── rotating_wheel_trajectory.gif
└── rotating_ring_with_title.gif
```

The GIF files are useful repository artifacts because they allow
visitors to see the result immediately without running the notebook.

------------------------------------------------------------------------

# 🔬 What the Project Demonstrates

Even though this is a very small project, it combines several useful
ideas.

### Physics

-   Translational motion
-   Rotational motion
-   Angular velocity
-   No-slip condition
-   Parametric trajectories

### Mathematics

-   Trigonometric functions
-   Parametric equations
-   Coordinate transformations

### Python

-   NumPy arrays
-   Mathematical computation
-   Matplotlib plotting
-   Animation
-   GIF generation

The main attraction, however, is the visualization.

------------------------------------------------------------------------

# 💡 Why Make a Project Like This?

Not every programming project needs to be a machine-learning model, a
research project, or a production application.

Sometimes a simple physics problem becomes much more enjoyable when it
is animated.

The idea here is essentially:

``` text
A familiar physics equation
          ↓
A few lines of Python
          ↓
A moving object
          ↓
A visible trajectory
          ↓
A GIF
```

It is a small example of using computation simply to **play with an idea
and see the mathematics come alive**.

------------------------------------------------------------------------

# ⚠️ Scope and Interpretation

This notebook is deliberately lightweight.

It is **not intended to be**:

-   A high-fidelity rigid-body dynamics simulator
-   A numerical mechanics research code
-   A physics engine
-   An experimental validation of rolling dynamics

The purpose is visualization and experimentation.

The equations are directly encoded into the animation, and the project
focuses on making the resulting trajectory intuitive and visually
interesting.

------------------------------------------------------------------------

# 🔮 Possible Extensions

If this little experiment were developed further, several fun extensions
would be possible.

## 1. Change the Radius

Allow the user to interactively change:

``` text
R
```

and watch how the trajectory changes.

## 2. Change Translational Velocity

Experiment with different values of:

``` text
v
```

and automatically update:

``` text
ω = v / R
```

## 3. Trace Different Points

Instead of always tracking one fixed point on the circumference, allow
the user to select:

``` text
Top point
Side point
Bottom point
Arbitrary angular position
```

## 4. Add a Velocity Vector

Display the instantaneous velocity of the tracked point.

## 5. Add an Acceleration Vector

Visualize the changing acceleration during the motion.

## 6. Compare Trajectories

Show multiple trajectories simultaneously for different:

``` text
R
v
ω
initial angular positions
```

## 7. Interactive Controls

A small `ipywidgets` interface could provide sliders for:

``` text
Radius
Velocity
Angular velocity
Simulation time
Animation speed
```

------------------------------------------------------------------------

# 🏁 Conclusion

This notebook is a compact example of **computational physics used
purely for visual exploration**.

It takes a simple rolling/rotating-ring problem and turns it into an
animated demonstration using:

``` text
Physics
   +
Parametric equations
   +
NumPy
   +
Matplotlib
   +
Animation
```

The result is not intended to solve a difficult research problem.

It is simply a fun way of asking:

> **"What does this trajectory actually look like if I let Python draw
> it?"**

And sometimes, that is reason enough to make a project.

------------------------------------------------------------------------

# 👤 Author

**Subhadeep Dey**

A small recreational computational-physics project created for
experimentation, visualization, and the sheer fun of turning physics
equations into motion.

------------------------------------------------------------------------

## ⭐ Project at a Glance

``` text
             PHYSICS EQUATIONS
                    │
                    ▼
            Translational Motion
                    +
             Rotational Motion
                    │
                    ▼
              x(t), y(t)
                    │
                    ▼
              NumPy Arrays
                    │
                    ▼
            Matplotlib Animation
                    │
                    ▼
                 GIF
                    │
                    ▼
           Watch the trajectory
           come alive 🎬
```

**A little physics, a little Python, and a lot of unnecessary fun.**
