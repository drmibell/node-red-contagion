Contagion
========

### About

Node-RED flows to implement [compartmental models](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology) for contagious disease. The compartments used are:
 - **S** = susceptible
 - **E** = exposed
 - **I** = infectious
 - **R**= recovered
 - **D** = deceased

The models implemented are **SIR, SIRD, SEIR,** and **SEIRD**
### Transition rates
**SIR**
 - _rate_(**S** -> **I**) = _beta * I * S_
 - _rate_(**I** -> **R**) = _gamma * I_

**SIRD**
 - _rate_(**S** -> **I**) = _beta * I * S - gamma * I_
 - _rate_(**I -> D**) = 
 - _rate_(**I -> R**) =

**SEIR**

**SEIRD**

where 
 - _R0_ = basic reproduction number
 - _D_ = contagious period (days)
 - _gamma = 1 / D_
 - _beta = R0 * gamma_
 - let H     = msg.payload.H     // treatment time (days)
 - let alpha = msg.payload.alpha // fatality rate
 - let rho = 1 / H

Notes:
- The generally used value for R0 seems to 2.5