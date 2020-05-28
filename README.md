Contagion Models
========

### About

Node-RED flows to implement [compartmental models](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology) for contagious disease. The compartments used are:
 - **S** = susceptible
 - **E** = exposed
 - **I** = infectious
 - **R**= recovered
 - **D** = deceased

The models implemented are **SIR, SIRD, SEIR,** and **SEIRD**. The rate equations (ordinary differential equations) representing transitions between the compartments are solved by the finite difference method, with a step size of 0.01 days. The populations of the compartments are represented by the time-dependent variables _s,e,i,r,d_, which are the fractions of the total population in each compartment. The system is initialized at _t_ = 0 with _i_ = 0.001 and _s_ = 0.999.

The models assume that the population is uniform and homogeneously mixed and that recovered individuals (compartment **R**) are immune to re-infection. The time period simulated is assumed to be brief enough that births and deaths (other than from the disease being modeled) can be neglected.

### Transition rates
**SIR**
 - _rate_(**S** -> **I**) = _beta * i * s_
 - _rate_(**I** -> **R**) = _gamma * i_

**SIRD**
 - _rate_(**S** -> **I**) = _beta * i * s_
 - _rate_(**I -> R**) = (1 - _alpha_) _* gamma * i_
 - _rate_(**I -> D**) = _alpha * rho * i_

**SEIR**
 - _rate_(**S** -> **E**) = _beta * i * s_
 - _rate_(**E** -> **I**) = _delta * e_
 - _rate_(**I -> R**) = _gamma * i_

**SEIRD**
 - _rate_(**S** -> **E**) = _beta * i * s_
 - _rate_(**E** -> **I**) = _delta * e_
 - _rate_(**I -> R**) = (1 - _alpha_) _* gamma * i_
 - _rate_(**I -> D**) = _alpha * rho * i_

where 
 - _R0_ = basic reproduction number
 - _I_ = incubation period (days)
 - _delta_ = 1/_I_
 - _D_ = contagious period (days)
 - _gamma_ = 1/_D_
 - _beta = R0 * gamma_
 - _H_ = treatment period (days)
 - _rho_ = 1/_H_
 - _alpha_ = fatality rate




Consensus values in the literature seem to be: _R0_ = 2.5, _D_ = 6 days, _I_ = 2 days, _H_ = 14 days, _alpha_ = 0.05 - 0.1

### Node-RED Flow Tabs
**Contagion Models**: allows the user to compare the results of two models, with the type and parameters selected independently.

**Interventions**: shows the result of imposing or modifying interventions (lockdown or social distancing), defined by changes in _R0_ at a specified times.