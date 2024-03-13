# Objective-1
## Solving the magnetic diffusion equation along $z$-coordinates

Magnetic Induction equation is essential in the realm of magnetohydrodynamics and it relates the variation of magnetic field with that of the velocity of electrically conductive ensemble of charged particles. This ensemble resembles a charged conductive fluid such as plasma, and hence plays a major role in plasma physics, especially in the two-fluid model of dynamo theory.

### Obtaining magnetic induction equation

The induction equation can be derived from Maxwell's equations describing the Faraday's law and Ampere's law, given by:

\begin{gather}
    \vec{\nabla} \times \vec{E} = - \dfrac{\partial \vec{B}}{\partial t} \tag{1}\\
    \vec{\nabla} \times \vec{B} = \mu_0 \vec{J} \tag{2}
\end{gather}

Where $\vec{E}$, $\vec{B}$ and $\vec{J}$ are the electric field, magnetic field and electric current density respectively. Now, electric field can be related to current density and magentic field using the Ohm's law for conductive fluid given by:

\begin{equation}
    \vec{E} + ( \vec{V} \times \vec{B} ) = \vec{J}/\sigma \tag{3}
\end{equation}

Where $\vec{V}$ is the velocity field of the fluid with electrical conductivity $\sigma$. Now finding the curl of both the L.H.S. and R.H.S. of $(3)$, we get:

\begin{equation}
    (\vec{\nabla} \times \vec{E}) + \vec{\nabla} \times ( \vec{V} \times \vec{B} ) = [\vec{\nabla} \times (1/\sigma)\vec{J}] \tag{4}
\end{equation}

Now, substituting from $(1)$ and $(2)$ into $(4)$ and rearranging, we get:

\begin{equation}
    \dfrac{\partial \vec{B}}{\partial t} = \vec{\nabla} \times \left[( \vec{V} \times \vec{B} ) - \eta (\vec{\nabla} \times \vec{B})\right] \tag{5}
\end{equation}

Where $\eta = 1/\mu_0 \sigma$ is the magnetic diffusivity. We can consider the magnetic field $\vec{B}$ and velocity vector $\vec{V}$ as:

\begin{align}
    \vec{B} = \overline{\vec{B}} + \vec{b} ~~~~~&~~~~~ \vec{V} = \overline{\vec{V}} + \vec{v} \tag{6}
\end{align}

Where $\overline{\vec{B}}$ and $\overline{\vec{V}}$ are the mean components, and $\vec{b}$ and $\vec{v}$ are the random components of magnetic and velocity vectors respectively. Hence, we can obtain the mean field induction equation given by:

\begin{equation}
    \dfrac{\partial \overline{\vec{B}}}{\partial t} = \vec{\nabla} \times \left[ ( \overline{\vec{V}} \times \overline{\vec{B}} ) + \vec{\mathcal{E}} - \eta (\vec{\nabla} \times \overline{\vec{B}})\right] \tag{7}
\end{equation}

Where $\vec{\mathcal{E}} = \overline{\vec{v} \times \vec{b}}$. Applying **First Order Smoothening Approximation (FOSA)**, we can approximate the $\vec{\mathcal{E}}$ as:

\begin{equation}
    \vec{\mathcal{E}} \approx \alpha \overline{\vec{B}} - \eta_t (\vec{\nabla} \times \overline{\vec{B}}) \tag{8}
\end{equation}

Where we have:

\begin{align}
    \alpha = -\dfrac{1}{3} \tau~ \overline{\vec{v} \cdot \vec{\nabla} \times \vec{v}} ~~~~&~~~~ \eta_t =\dfrac{1}{3}\tau~ \overline{v^2} \tag{9}
\end{align}

Using $(9)$, the mean field induction equation in $(7)$ can be modified after applying FOSA as:

\begin{equation}
    \dfrac{\partial \overline{\vec{B}}}{\partial t} = \vec{\nabla} \times \left[ ( \overline{\vec{V}} \times \overline{\vec{B}} ) + \alpha\overline{\vec{B}} - (\eta + \eta_t) (\vec{\nabla} \times \overline{\vec{B}})\right] \tag{10}
\end{equation}


Now considering $\eta_T = \eta + \eta_t$ and using the identity for finding curl of curl of a vector, given by:

\begin{equation}
    \vec{\nabla} \times (\vec{\nabla} \times \overline{\vec{B}}) = \vec{\nabla} (\vec{\nabla} \cdot \overline{\vec{B}}) - \vec{\nabla}^2 \overline{\vec{B}} \tag{11}
\end{equation}

Now, the first term of the R.H.S. of $(11)$ vanishes as $\vec{\nabla}\cdot\vec{B} = \vec{\nabla}\cdot\overline{\vec{B}} = 0$ according to Maxwell's equations, which gives the final form of induction equation as:

\begin{equation}
    \dfrac{\partial \overline{\vec{B}}}{\partial t} = \eta_T \vec{\nabla}^2 \overline{\vec{B}} + (\vec{\nabla} \times \alpha\overline{\vec{B}}) + \vec{\nabla} \times ( \overline{\vec{V}} \times \overline{\vec{B}} ) \tag{12}
\end{equation}

### Obtaining magnetic diffusion equation from magentic induction equation

Now, the **diffusion equation** can be obtained from the mean field induction equation by omitting the $\vec{\nabla} \times ( \overline{\vec{V}} \times \overline{\vec{B}} )$ and terms involving $\alpha$ from R.H.S. of $(12)$, leaving behind only terms involving $\eta_T$. Hence, the diffusion equation is given by:

\begin{equation}
    \dfrac{\partial \overline{\vec{B}}}{\partial t} = \eta_T \vec{\nabla}^2 \overline{\vec{B}} \tag{13}
\end{equation}

Expanding the vector laplacian into various components for the cylindrical coordinates $(r, \phi, z)$, we get:

\begin{gather}
    \dfrac{\partial \overline{B_i}}{\partial t} = \eta_T \dfrac{\partial}{\partial r}\left[ \dfrac{1}{r}\dfrac{\partial}{\partial r} (r\overline{B_i}) \right] + \eta_T \dfrac{\partial^2 \overline{B_i}}{\partial z^2} \tag{14}
\end{gather}

Since we are tasked with obtaining the solution of the diffusion equation with respect of $z$-coordinate only, we can neglect the derivatives with respect to $r$, which will give us the simpler form of equation as:

\begin{equation}
    \dfrac{\partial \overline{B_i}}{\partial t} = \eta_T \dfrac{\partial^2 \overline{B_i}}{\partial z^2} \tag{15}
\end{equation}

Which is eqeuivalent to solving heat equation in one dimension. Hence, appropriate numerical technique which can easily solve heat equation can be applied for solving magnetic diffusion equation too.

### Initial and boundary conditions

For mean field dynamo theory vacuum boundary conditions are commonly adapted, in which we neglect any electric currents outside the dynamo region. Also, the boundary conditions are applied to the magnetic diffusion equation in order to solve for the mean-field dynamo are based on the simplest approximation of a thin disc. The disc surface are described as $z = \pm h$, where it is assumed that there is electromagnetic vacuum outside the disc, i.e., $\vec{\nabla} \times \vec{B} = 0$ for $|z| > h$. Hence resulting boundary condition can be expressed as:

\begin{align}
    \overline{B}_r = 0 ,~~~~&~~~~ \overline{B}_\phi = 0 ~~~&&~~~ \text{at} ~z = \pm h
\end{align}

Where $h$ s the half-thickness of the disc, which in terms of expressing the solution in dimensionless form, can be set to $h = 1$. Now $\overline{B}_z$ can be obtained using $\vec{\nabla}\cdot \overline{\vec{B}} = 0$. In terms of choosing initial conditions, also called the seed magnetic field, different choices of magnetic field can be applied in order to explore to what extent these choices influence the magnetic field evolution. One can expect that the solution of the diffusion equation in the kinematic regime is not much depend on the seed magnetic field.  

