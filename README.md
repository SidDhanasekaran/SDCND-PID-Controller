# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

This project implements PID controller for steering the car in the Unity engine simulator. The goal is to minimize cross track error.


## Parameter Selection

The three components (P,I,D) have different effects on the control of the steering angle

1 - The 'P' constant determines the correction in proportion to the error. Having a high 'P' allows you to drive in a curvy track. However, high 'P' tends to make oscillations worse, specially when there is "noise" in driving. 

2- The 'I' constant determines the control component based on the Integral of the error. 'I` helps when the car has deviated a lot - `I` control helps bring it back on track. However, it can amplify the oscillations because the error builds up.

3- The 'D' constant determines the correction based on the rate of change of the error. `D` helps reduce the oscillations caused by `P` and `I`. However if `D` is high, it will make the car impossible to turn.

To determine the P,D and I constants for the vehicle in the simulation, I used [![manual tuning]](https://en.wikipedia.org/wiki/PID_controller#Manual_tuning)


The parameters I found to produce the most stable results are:

| Kp  |  Ki   |  Kd  |
|-----|-------|------|
| 0.1 | 0.002 |  1.5 |

Kp is set to small value to increase stability. For same reason Ki is low. Kd is set to 1.5 to achieve fast enough correction of steering to reduce overshoot.Increasing Kd will lead to more aggressive reactions for overshoot. Increasing Ki and Kp will lead to instability (oscillations with increasing amplitude).

## Video of the car in the simulator

[![Self Driving Car Nanodegree PID control](http://img.youtube.com/vi/3TFM8YyKyRc/0.jpg)](https://www.youtube.com/watch?v=3TFM8YyKyRc)

---

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets) == 0.13, but the master branch will probably work just fine
  * Follow the instructions in the [uWebSockets README](https://github.com/uWebSockets/uWebSockets/blob/master/README.md) to get setup for your platform. You can download the zip of the appropriate version from the [releases page](https://github.com/uWebSockets/uWebSockets/releases). Here's a link to the [v0.13 zip](https://github.com/uWebSockets/uWebSockets/archive/v0.13.0.zip).
  * If you run OSX and have homebrew installed you can just run the ./install-mac.sh script to install this
* Simulator. You can download these from the [project intro page](https://github.com/udacity/CarND-PID-Control-Project/releases) in the classroom.

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`.

## Editor Settings

We've purposefully kept editor configuration files out of this repo in order to
keep it as simple and environment agnostic as possible. However, we recommend
using the following settings:

* indent using spaces
* set tab width to 2 spaces (keeps the matrices in source code aligned)

## Code Style

Please (do your best to) stick to [Google's C++ style guide](https://google.github.io/styleguide/cppguide.html).

## Project Instructions and Rubric

Note: regardless of the changes you make, your project must be buildable using
cmake and make!

More information is only accessible by people who are already enrolled in Term 2
of CarND. If you are enrolled, see [the project page](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/f1820894-8322-4bb3-81aa-b26b3c6dcbaf/lessons/e8235395-22dd-4b87-88e0-d108c5e5bbf4/concepts/6a4d8d42-6a04-4aa6-b284-1697c0fd6562)
for instructions and the project rubric.

## Hints!

* You don't have to follow this directory structure, but if you do, your work
  will span all of the .cpp files here. Keep an eye out for TODOs.

## Call for IDE Profiles Pull Requests

Help your fellow students!

We decided to create Makefiles with cmake to keep this project as platform
agnostic as possible. Similarly, we omitted IDE profiles in order to we ensure
that students don't feel pressured to use one IDE or another.

However! I'd love to help people get up and running with their IDEs of choice.
If you've created a profile for an IDE that you think other students would
appreciate, we'd love to have you add the requisite profile files and
instructions to ide_profiles/. For example if you wanted to add a VS Code
profile, you'd add:

* /ide_profiles/vscode/.vscode
* /ide_profiles/vscode/README.md

The README should explain what the profile does, how to take advantage of it,
and how to install it.

Frankly, I've never been involved in a project with multiple IDE profiles
before. I believe the best way to handle this would be to keep them out of the
repo root to avoid clutter. My expectation is that most profiles will include
instructions to copy files to a new location to get picked up by the IDE, but
that's just a guess.

One last note here: regardless of the IDE used, every submitted project must
still be compilable with cmake and make./
