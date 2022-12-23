# One-Dimensional Kalman Filter with Constant Dynamics Model (Kalman_1D)
This is an implementation of the one-dimensional Kalman filter with process noise and constant dynamics as described by Alex Becker in his [Kalman Filter website](https://www.kalmanfilter.net/kalman1d_pn.html).

## How to Use
See the example code inside the zip file for an Arduino Uno implementation that measures the temperature using an LM35 thermistor.

### Include Library in Workspace
1. Download zip file
2. For Arduino: “Sketch” > “Include Library” > “Add .ZIP Library…”; For C++: Import library via IDE
3. Include header: `#include <kalman_1d.h>` at the top of the C++ or .ino file

### Functions:
`Kalman_1D(double initEstimate, double initEstimateError, double measurementError, double procNoiseVar);` Initializes filter with initial estimate, estimate error, measurement error, and process noise variance

`void iterationZero();` Performs iteration 0 of the Kalman filter; not necessary to call this, as it is already called during initialization

`void iterate(double measuredData);` Performs an iteration of the Kalman filter (see cpp file for details)

`double getCurrentEstimate();` Returns current state estimate

`double getCurrentEstimateUncertainty();` Returns current state estimate uncertainty

`double getExtrapolatedEstimateUncertainty();` Returns extrapolated state estimate uncertainty

`double getKalmanGain();` Returns current kalman gain constant

### Implement
1. Instantiate Kalman_1D object with initial estimate, initial estimate error, measurement error, and process noise variance: `Kalman_1D kalman(10, 50, 0.5, 0.005);`
2. For each iteration: measure data, then pass it in as a parameter into iterate() function: `kalman.iterate(data);`
3. Use getter functions to get current estimate, current estimate error, and other variables if desired
