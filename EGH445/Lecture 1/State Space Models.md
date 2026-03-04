← Back to [[Introduction to Modern Control]]
## Input-State-Output Framework
|**Structural Component**|**Variable**|**Description / Function**|
|---|---|---|
|**System Input**|$u(t)$|External signal entering the system.|
|**State Space**|$x(t)$|Represents the internal states and system dynamics (equations).|
|**System Output**|$y(t)$|Measured signal exiting the system.|
|**Controls**||Mechanisms used to manipulate state variables.|
|**Observers**||Systems designed to measure the output.|
|**Feedback Application**||Utilizes output feedback and state estimation.



### Core Equations

**State Equation:**
$$\dot{x}(t) = f(x(t), u(t))$$

**Output Equation:**
$$y(t) = g(x(t), u(t))$$

For Linear Time-Invariant (LTI) systems:
$$\dot{x} = Ax + Bu$$
$$y = Cx + Du$$

| Matrix | Dimensions | Description |
|--------|------------|-------------|
| A | n×n | State transition matrix |
| B | n×m | Input/state coupling |
| C | p×n | State/output coupling |
| D | p×m | Direct input-to-output |

### State Vector Definition

The state vector encapsulates the minimal set of variables needed to completely describe system behavior:

```matlab
% For a mass-spring-damper system
% Minimal complete description requires two variables:
% - Displacement
% - Velocity

x = [y; dydt];  % State vector: [position; velocity]

```

