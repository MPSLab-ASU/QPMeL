

$$\newcommand{\ket}[1]{\left|{#1}\right\rangle}$$
$$\newcommand{\bra}[1]{\left\langle{#1}\right|}$$
$$\bra{\Psi}\Omega\ket{\Psi}$$

$$\newcommand{\braket}[2]{\left\langle{#1}\middle|{#2}\right\rangle}$$
$$\braket{\Psi}{\Psi}$$
$$\braket{\frac{\Psi}{2}}{\Psi}$$

## Math Demo
$$ \alpha = \beta $$

## Paper Contributions
**QPMeL** addresses introduces the following ideas: 
1. A novel classical network that encodes classical data into 2 real-valued vectors that are used as Polar coordinates of a qubit. This allows us to utilize the entire 3D space of a qubit, as we are not limited to a single plane.
2. A hybrid Hilbert space distance metric we dub *Fidelity Triplet Loss* that measures distance in Hilbert Space while creating the optimization target classically. The distances are measured in-circuit while their difference is computed classically.
3. *Quantum Residual Corrections* to speed up model learning and generate more stable gradients by acting as a noise barrier. The parameters absorb noisier gradients to allow the classical model to learn more efficiently.


## Quantum State Equation

The final state produced by our Encoding circuit would be:
\begin{equation}
   \ket{\psi} = \bigotimes_{i=0}^n \exp(i\frac{\phi_i}{2}) \cos{\frac{\theta_i}{2}} \ket{0} \; + \; \exp(i \frac{- \phi_i}{2}) \sin{\frac{\theta_i}{2}} \ket{1} 
\end{equation}
where,

$$
\begin{align*}
    \phi_i &= \alpha_k - \alpha_i - \gamma_i \\
    k &= (n+i)\mod (n+1) 
    \theta_i &= \theta_{m_i} + \theta_{\Delta_i} \quad | \quad \gamma_i = \gamma_{m_i} + \gamma_{\Delta_i} \\
    \theta_{m_i}, \gamma_{m_i} &= f(image,w) \\
\end{align*}
$$

Where we have 6 parameters per qubit, 2 from the classical model ($\theta_m,\gamma_m$), 2 learned parameters for the $ZZ$-Gate ($\alpha_i,\alpha_k$) and 2 residuals ($\theta_{\Delta},\gamma_{\Delta}$).