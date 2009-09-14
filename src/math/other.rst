Polar and Spherical Coordinates
-------------------------------


Polar coordinates (radial, azimuth) $(r,\phi)$ are defined by 

.. math::
    :nowrap:

    \begin{eqnarray*} x&=&r\cos\phi \\ y&=&r\sin\phi \\ \end{eqnarray*}

Spherical coordinates (radial, zenith, azimuth) $(\rho,\theta,\phi)$: 

.. math::
    :nowrap:

    \begin{eqnarray*} x&=&\rho\sin\theta\cos\phi \\ y&=&\rho\sin\theta\sin\phi \\ z&=&\rho\cos\theta \\ \end{eqnarray*}

Note: this meaning of $(\theta,\phi)$ is mostly used in the USA and in many books. In Europe people usualy use different symbols, like $(\phi,\theta)$, $(\vartheta,\varphi)$ and others.

.. index:: delta function

Delta Function
--------------


Delta function $\delta(x)$ is defined such that this relation holds: 

.. math::
    :label: deltadef

       \int f(x)\delta(x-t)\d x=f(t)

No such function exists, but one can find many sequences "converging" to a delta function: 

.. math::
    :label: deltalim

       \lim_{\alpha\to\infty}\delta_\alpha(x) = \delta(x)

more precisely: 

.. math::
    :label: deltaprec

       \lim_{\alpha\to\infty}\int f(x)\delta_\alpha(x)\d x = \int f(x)\lim_{\alpha\to\infty}\delta_\alpha(x)\d x = f(t)

one example of such a sequence is: 

.. math::

       \delta_\alpha(x) = {1\over\pi x}\sin(\alpha x)

It's clear that :eq:`deltaprec` holds for any well behaved function $f(x)$. Mathematicians like to say it's incorrect to use such a notation when in fact the integral :eq:`deltadef` doesn't "exist", but they are wrong, because it is not important if something "exist" or not, but rather if it is clear what we mean by our notation: :eq:`deltadef` is a shorthand for :eq:`deltaprec` and :eq:`deltalim` gets a mathematically rigorous meaning when you integrate both sides and use :eq:`deltadef` to arrive at :eq:`deltaprec`. Thus one uses the relations :eq:`deltadef`, :eq:`deltalim`, :eq:`deltaprec` to derive all properties of the delta function.

Let's give an example. Let ${\bf\hat r}$ be the unit vector in 3D and we can label it using spherical coordinates ${\bf\hat r}={\bf\hat r}(\theta,\phi)$. We can also express it in cartesian coordinates as ${\bf\hat r}(\theta,\phi)=(\cos\phi\sin\theta,\sin\phi\sin\theta,\cos\theta)$.



.. math::
    :label: deltar

       f({\bf\hat r'})=\int\delta({\bf\hat r}-{\bf\hat r'})f({\bf\hat r})\,\d {\bf\hat r}

Expressing $f({\bf\hat r})=f(\theta,\phi)$ as a function of $\theta$ and $\phi$ we have 

.. math::
    :label: deltaangles

       f(\theta',\phi')=\int\delta(\theta-\theta')\delta(\phi-\phi') f(\theta,\phi)\,\d\theta\d\phi

Expressing :eq:`deltar` in spherical coordinates we get 

.. math::

       f(\theta',\phi')=\int\delta({\bf\hat r}-{\bf\hat r'}) f(\theta,\phi)\sin\theta\,\d\theta\d\phi

and comparing to :eq:`deltaangles` we finally get 

.. math::

       \delta({\bf\hat r}-{\bf\hat r'})={1\over\sin\theta} \delta(\theta-\theta')\delta(\phi-\phi')

In exactly the same manner we get 

.. math::

       \delta({\bf r}-{\bf r'})=\delta({\bf\hat r}-{\bf\hat r'}) {\delta(\rho-\rho')\over\rho^2}

See also :eq:`functionalderdel` for an example of how to deal with more complex expressions involving the delta function like $\delta^2(x)$.

.. index:: variation, functional derivative

Variations and Functional Derivatives
-------------------------------------


Functional derivatives are a common source of confusion and especially the
notation. The reason is similar to the delta function --- the definition is
operational, i.e. it tells you what operations you need to do to get a
mathematically precise formula. The notation below is commonly used in physics
and in our opinion it is perfectly precise and exact, but some mathematicians
may not like it.

Let's have $\x=(x_1,x_2,\dots,x_N)$. The function $f(\x)$ assigns a number to each $\x$. We define a differential of $f$ as 

.. math::

       \d f\equiv \left.{\d\over\d\varepsilon}f(\x+\varepsilon\h) \right|_{\varepsilon=0} =\lim_{\varepsilon\to0} {f(\x+\varepsilon\h)-f(\x)\over\varepsilon}=\a\cdot\h

The last equality follows from the fact, that $\left.{\d\over\d\varepsilon}f(\x+\varepsilon\h) \right|_{\varepsilon=0}$ is a linear function of $\h$. We define ${\partial f\over\partial x_i}$ as 

.. math::

       \a\equiv\left({\partial f\over\partial x_1},{\partial f\over\partial x_2}, \dots,{\partial f\over\partial x_N}\right)

This also gives a formula for computing ${\partial f\over\partial x_i}$: we set $h_j=\delta_{ij}h_i$ and 

.. math::

       {\partial f\over\partial x_i}=a_i=\a\cdot\h=\left.{\d\over\d\varepsilon} f(\x+\varepsilon(0,0,\dots,1,\dots,0))\right|_{\varepsilon=0}=


.. math::

       =\lim_{\varepsilon\to0} {f(x_1,x_2,\dots,x_i+\varepsilon,\dots,x_N)-f(x_1,x_2,\dots,x_i,\dots,x_N) \over\varepsilon}

But this is just the way the partial derivative is usually defined. Every variable can be treated as a function (very simple one): 

.. math::

       x_i=g(x_1,\dots,x_N)=\delta_{ij}x_j

and so we define 

.. math::

       \d x_i\equiv\d g=\d(\delta_{ij}x_j)=h_i

and thus we write $h_i=\d x_i$ and $\h=\d\x$ and 

.. math::

       \d f={\d f\over\d x_i}\d x_i

So $\d\x$ has two meanings --- it's either $\h=\x-\x_0$ (a finite change in the independent variable $\x$) or a differential, depending on the context. Even mathematicians use this notation.

Functional $F[f]$ assigns a number to each function $f(x)$. The variation is defined as 

.. math::

       \delta F[f]\equiv\left.{\d\over\d\varepsilon}F[f+\varepsilon h] \right|_{\varepsilon=0}=\lim_{\epsilon\to0}{F[f+\epsilon h]-F[f]\over\epsilon}= \int a(x)h(x)\d x

We define ${\delta F\over\delta f(x)}$ as 

.. math::

       a(x)\equiv{\delta F\over\delta f(x)}

This also gives a formula for computing ${\delta F\over\delta f(x)}$: we set $h(y)=\delta(x-y)$ and 

.. math::

       {\delta F\over\delta f(x)}=a(x)=\int a(y)\delta(x-y)\d y= \left.{\d\over\d\varepsilon}F[f(y)+\varepsilon\delta(x-y)] \right|_{\varepsilon=0}=


.. math::

       =\lim_{\varepsilon\to0} {F[f(y)+\varepsilon\delta(x-y)]-F[f(y)]\over\varepsilon}

Every function can be treated as a functional (although a very simple one): 

.. math::

       f(x)=G[f]=\int f(y)\delta(x-y)\d y

and so we define 

.. math::

       \delta f\equiv\delta G[f]= \left.{\d\over\d\varepsilon}G[f(x)+\varepsilon h(x)] \right|_{\varepsilon=0}= \left.{\d\over\d\varepsilon}(f(x)+\varepsilon h(x)) \right|_{\varepsilon=0}= h(x)

thus we write $h=\delta f$ and 

.. math::

       \delta F[f]=\int {\delta F\over\delta f(x)}\delta f(x)\d x

so $\delta f$ have two meanings --- it's either $h(x)=\left.{\d\over\d\varepsilon}(f(x)+\varepsilon h(x)) \right|_{\varepsilon=0}$ (a finite change in the function $f$) or a variation of a functional, depending on the context. Mathematicians never write $\delta f$ in the meaning of $h(x)$, they always write the latter, but it's ridiculous, because it is completely analogous to $\d\x$.

The correspondence between the finite and infinite dimensional case can be summarized as: 

.. math::
    :nowrap:

    \begin{eqnarray*} f(x_i) \quad&\Longleftrightarrow&\quad F[f] \\ \d f=0 \quad&\Longleftrightarrow&\quad \delta F=0 \\ {\partial f\over\partial x_i}=0 \quad&\Longleftrightarrow&\quad {\delta F\over\delta f(x)}=0 \\ f \quad&\Longleftrightarrow&\quad F \\ x_i \quad&\Longleftrightarrow&\quad f(x) \\ x \quad&\Longleftrightarrow&\quad f \\ i \quad&\Longleftrightarrow&\quad x \\ \end{eqnarray*}


More generally, $\delta$-variation can by applied to any function $g$ which contains the function $f(x)$ being varied, you just need to replace $f$ by $f+\epsilon h$ and apply ${\d\over\d\epsilon}$ to the whole $g$, for example (here $g=\partial_\mu\phi$ and $f=\phi$): 

.. math::

       \delta\partial_\mu\phi=\left.{\d\over\d\varepsilon}\partial_\mu(\phi+\varepsilon h) \right|_{\varepsilon=0}= \partial_\mu\left.{\d\over\d\varepsilon}(\phi+\varepsilon h) \right|_{\varepsilon=0}=\partial_\mu\delta\phi


This notation allows us a very convinient computation, as shown in the following examples. First, when computing a variation of some integral, when can interchange $\delta$ and $\int$: 

.. math::

       F[f]=\int K(x) f(x) \d x


.. math::

       \delta F=\delta \int K(x) f(x) \d x = \left.{\d\over\d\varepsilon}\int K(x) (f+\varepsilon h)\d x\right|_{\varepsilon=0}= \left.\int{\d\over\d\varepsilon} (K(x) (f+\varepsilon h))\d x\right|_{\varepsilon=0}=


.. math::

       =\int\delta(K(x) f(x))\d x

In the expression $\delta(K(x) f(x))$ we must understand from the context if we are treating it as a functional of $f$ or $K$. In our case it's a functional of $f$, so we have $\delta(K f)=K\delta f$.

A few more examples: 

.. math::

       {\delta\over\delta f(t)}\int\d t'f(t')g(t')= \left.{\d\over\d\varepsilon}\int\d t'(f(t')+\varepsilon\delta(t-t'))g(t') \right|_{\varepsilon=0}=g(t)


.. math::

       {\delta f(t')\over\delta f(t)}= \left.{\d\over\d\varepsilon}(f(t')+\varepsilon\delta(t-t')) \right|_{\varepsilon=0}=\delta(t-t')


.. math::

       {\delta f(t_1)f(t_2)\over\delta f(t)}= \left.{\d\over\d\varepsilon}(f(t_1)+\varepsilon\delta(t-t_1)) (f(t_2)+\varepsilon\delta(t-t_2)) \right|_{\varepsilon=0}=\delta(t-t_1)f(t_2)+f(t_1)\delta(t-t_2)


.. math::

       {\delta\over\delta f(t)}\half\int\d t_1\d t_2K(t_1,t_2)f(t_1)f(t_2)= \half\int\d t_1\d t_2K(t_1,t_2){\delta f(t_1)f(t_2)\over\delta f(t)}=


.. math::

       =\half\left(\int\d t_1 K(t_1,t)f(t_1)+\int\d t_2 K(t,t_2)f(t_2)\right) =\int\d t_2 K(t,t_2)f(t_2)

The last equality follows from $K(t_1,t_2)=K(t_2,t_1)$ (any antisymmetrical part of a $K$ would not contribute to the symmetrical integration). 

.. math::

       {\delta\over\delta f(t)}\int f^3(x)\d x= \left.{\d\over\d\varepsilon}\int(f(x)+\varepsilon\delta(x-t))^3\d x \right|_{\varepsilon=0}=


.. math::

       =\left.\int3(f(x)+\varepsilon\delta(x-t))^2\delta(x-t)\d x \right|_{\varepsilon=0}=\int3f^2(x)\delta(x-t)\d x=3f^2(t)

Some mathematicians would say the above calculation is incorrect, because $\delta^2(x-t)$ is undefined. But that's not true, because in case of such problems the above notation automatically implies working with some sequence $\delta_\alpha(x) \to \delta(x)$ (for example $\delta_\alpha(x) = {1\over\pi x}\sin(\alpha x)$) and taking the limit $\alpha\to\infty$: 

.. math::

       {\delta\over\delta f(t)}\int f^3(x)\d x= \left.\lim_{\alpha\to\infty}{\d\over\d\varepsilon}\int(f(x)+\varepsilon\delta_\alpha(x-t))^3\d x \right|_{\varepsilon=0}=


.. math::

       =\left.\lim_{\alpha\to\infty}\int3(f(x)+\varepsilon\delta_\alpha(x-t))^2\delta_\alpha(x-t)\d x \right|_{\varepsilon=0}=\lim_{\alpha\to\infty}\int3f^2(x)\delta_\alpha(x-t)\d x=


.. math::
    :label: functionalderdel

       =\int3f^2(x)\lim_{\alpha\to\infty}\delta_\alpha(x-t)\d x= \int3f^2(x)\delta(x-t)\d x=3f^2(t)

As you can see, we got the same result, with the same rigor, but using an obfuscating notation. That's why such obvious manipulations with $\delta_\alpha$ are tacitly implied.

.. index:: spherical harmonics

Spherical Harmonics
-------------------


Are defined by 

.. math::

       Y_{lm}(\theta,\phi)=\sqrt{{2l+1\over4\pi}{(l-m)!\over(l+m)!}}\,P_l^m(\cos\theta)\,e^{im\phi}

where $P_l^m$ are associated Legendre polynomials defined by 

.. math::

       P_l^m(x)=(-1)^m (1-x^2)^{m/2}{\d^m\over\d x^m} P_l(x)

and $P_l$ are Legendre polynomials defined by the formula 

.. math::

       P_l(x)={1\over2^l l!}{\d^l\over\d x^l}[(x^2-1)^l]

they also obey the completeness relation 

.. math::
    :label: Lorto

       \sum_{l=0}^\infty {2l+1\over2}P_l(x')P_l(x)=\delta(x-x')

The spherical harmonics are ortonormal: 

.. math::
    :label: Yorto

       \int Y_{lm}\,Y^*_{l'm'}\,\d\Omega = \int_0^{2\pi}\int_0^{\pi} Y_{lm}(\theta,\phi)\,Y^*_{l'm'}(\theta,\phi)\sin\theta\,\d\theta\,\d\phi = \delta_{mm'}\delta_{ll'}

and complete (both in the $l$-subspace and the whole space): 

.. math::
    :label: lcomplete

       \sum_{m=-l}^l|Y_{lm}(\theta,\phi)|^2={2l+1\over4\pi}


.. math::
    :label: Ycomplete

       \sum_{l=0}^\infty\sum_{m=-l}^lY_{lm}(\theta,\phi)Y_{lm}^*(\theta',\phi') ={1\over\sin\theta}\delta(\theta-\theta')\delta(\phi-\phi')= \delta({\bf\hat r}-{\bf\hat r'})

The relation :eq:`lcomplete` is a special case of an addition theorem for spherical harmonics 

.. math::
    :label: lsum

       \sum_{m=-l}^lY_{lm}(\theta,\phi)Y_{lm}^*(\theta',\phi')= {4\pi\over 2l+1}P_l(\cos\gamma)

where $\gamma$ is the angle between the unit vectors given by ${\bf\hat r}=(\theta,\phi)$ and ${\bf\hat r'}=(\theta',\phi')$: 

.. math::

       \cos\gamma=\cos\theta\cos\theta'+\sin\theta\sin\theta'\cos(\phi-\phi') ={\bf\hat r}\cdot{\bf\hat r'}

.. index:: dirac notation

Dirac Notation
--------------


The Dirac notation allows a very compact and powerful way of writing equations that describe a function expansion into a basis, both discrete (e.g. a fourier series expansion) and continuous (e.g. a fourier transform) and related things. The notation is designed so that it is very easy to remember and it just guides you to write the correct equation.

Let's have a function $f(x)$. We define 

.. math::
    :nowrap:

    \begin{eqnarray*} \braket{x|f}&\equiv& f(x) \\ \braket{x'|f}&\equiv& f(x') \\ \braket{x'|x}&\equiv&\delta(x'-x) \\ \int\ket{x}\bra{x}\d x&\equiv&\one \\ \end{eqnarray*}

The following equation 

.. math::

       f(x')=\int\delta(x'-x)f(x)\d x

then becomes 

.. math::

       \braket{x'|f}=\int\braket{x'|x}\braket{x|f}\d x

and thus we can interpret $\ket{f}$ as a vector, $\ket{x}$ as a basis and $\braket{x|f}$ as the coefficients in the basis expansion: 

.. math::

       \ket{f}=\one\ket{f}=\int\ket{x}\bra{x}\d x\ket{f}= \int\ket{x}\braket{x|f}\d x

That's all there is to it. Take the above rules as the operational definition of the Dirac notation. It's like with the delta function - written alone it doesn't have any meaning, but there are clear and non-ambiguous rules to convert any expression with $\delta$ to an expression which even mathematicians understand (i.e. integrating, applying test functions and using other relations to get rid of all $\delta$ symbols in the expression -- but the result is usually much more complicated than the original formula). It's the same with the ket $\ket{f}$: written alone it doesn't have any meaning, but you can always use the above rules to get an expression that make sense to everyone (i.e. attaching any bra to the left and rewriting all brackets $\braket{a|b}$ with their equivalent expressions) -- but it will be more complex and harder to remember and -- that is important -- less general.

Now, let's look at the spherical harmonics: 

.. math::

       Y_{lm}({\bf\hat r})\equiv\braket{{\bf\hat r}|lm}

on the unit sphere, we have 

.. math::

       \int\ket{\bf\hat r}\bra{\bf\hat r}\d{\bf\hat r}= \int\ket{\bf\hat r}\bra{\bf\hat r}\d\Omega=\one


.. math::

       \delta({\bf\hat r}-{\bf\hat r'})=\braket{{\bf\hat r}|{\bf\hat r'}}

thus 

.. math::

       \int_0^{2\pi}\int_0^{\pi} Y_{lm}(\theta,\phi)\,Y^*_{l'm'}(\theta,\phi)\sin\theta\,\d\theta\,\d\phi = \int\braket{l'm'|{\bf\hat r}}\braket{{\bf\hat r}|lm}\d\Omega= \braket{l'm'|lm}

and from :eq:`Yorto` we get 

.. math::

       \braket{l'm'|lm}=\delta_{mm'}\delta_{ll'}

now 

.. math::

       \sum_{lm}Y_{lm}(\theta,\phi)Y_{lm}^*(\theta',\phi')= \sum_{lm}\braket{{\bf\hat r}|lm}\braket{lm|{\bf\hat r'}}

from :eq:`Ycomplete` we get 

.. math::

       \sum_{lm}\braket{{\bf\hat r}|lm}\braket{lm|{\bf\hat r'}}= \braket{{\bf\hat r}|{\bf\hat r'}}

so we have 

.. math::

       \sum_{lm}\ket{lm}\bra{lm}=\one

so $\ket{lm}$ forms an orthonormal basis. Any function defined on the sphere $f({\bf\hat r})$ can be written using this basis: 

.. math::

       f({\bf\hat r}) =\braket{{\bf\hat r}|f} =\sum_{lm}\braket{{\bf\hat r}|lm}\braket{lm|f} =\sum_{lm}Y_{lm}({\bf\hat r})f_{lm}

where 

.. math::

       f_{lm}=\braket{lm|f}=\int\braket{lm|{\bf\hat r}}\braket{{\bf\hat r}|f}\d\Omega =\int Y_{lm}^*({\bf\hat r}) f({\bf\hat r})\d\Omega

If we have a function $f({\bf r})$ in 3D, we can write it as a function of $\rho$ and ${\bf\hat r}$ and expand only with respect to the variable ${\bf\hat r}$: 

.. math::

       f({\bf r})=f(\rho{\bf\hat r})\equiv g(\rho,{\bf\hat r})= \sum_{lm}Y_{lm}({\bf\hat r})g_{lm}(\rho)

In Dirac notation we are doing the following: we decompose the space into the angular and radial part 

.. math::

       \ket{{\bf r}}=\ket{{\bf\hat r}}\otimes\ket{\rho} \equiv\ket{{\bf\hat r}}\ket{\rho}

and write 

.. math::

       f({\bf r})=\braket{{\bf r}|f}=\bra{{\bf\hat r}}\braket{\rho|f}= \sum_{lm}Y_{lm}({\bf\hat r})\bra{lm}\braket{\rho|f}

where 

.. math::

       \bra{lm}\braket{\rho|f}= \int\braket{lm|{\bf\hat r}}\bra{{\bf\hat r}}\braket{\rho|f}\d\Omega =\int Y_{lm}^*({\bf\hat r}) f({\bf r})\d\Omega

Let's calculate $\braket{\rho|\rho'}$

.. math::

       \braket{{\bf r}|{\bf r'}}=\bra{\bf\hat r}\braket{\rho|\rho'}\ket{{\bf\hat r'}} =\braket{{\bf\hat r}|{\bf\hat r'}}\braket{\rho|\rho'}

so 

.. math::

       \braket{\rho|\rho'} ={\braket{{\bf r}|{\bf r'}}\over\braket{{\bf\hat r}|{\bf\hat r'}}} ={\delta(\rho-\rho')\over\rho^2}

We must stress that $\ket{lm}$ only acts in the $\ket{{\bf\hat r}}$ space (not the $\ket\rho$ space) which means that 

.. math::

       \braket{{\bf r}|lm} =\bra{\bf\hat r}\braket{\rho|lm} =\braket{{\bf\hat r}|lm}\bra{\rho} =Y_{lm}({\bf\hat r})\bra{\rho}

and $V\ket{lm}$ leaves $V\ket\rho$ intact. Similarly, 

.. math::

       \sum_{lm} \ket{lm}\bra{lm}=\one

is a unity in the $\ket{\bf\hat r}$ space only (i.e. on the unit sphere).

Let's rewrite the equation :eq:`lsum`: 

.. math::

       \sum_m\braket{{\bf\hat r}|lm}\braket{lm|{\bf\hat r'}}= {4\pi\over 2l+1} \braket{{\bf\hat r}\cdot{\bf\hat r'}|P_l}

Using the completeness relation :eq:`Lorto`: 

.. math::

       \sum_l {2l+1\over2}\braket{x'|P_l}\braket{P_l|x}=\braket{x'|x}


.. math::

       \sum_l \ket{P_l}{2l+1\over2}\bra{P_l}=\one

we can now derive a very important formula true for every function $f({\bf\hat r}\cdot{\bf\hat r'})$:



.. math::

       f({\bf\hat r}\cdot{\bf\hat r'})=\braket{{\bf\hat r}\cdot{\bf\hat r'}|f}= \sum_l \braket{{\bf\hat r}\cdot{\bf\hat r'}|P_l}{2l+1\over2}\braket{P_l|f}= \sum_{lm}\braket{{\bf\hat r}|lm}\braket{lm|{\bf\hat r'}}{(2l+1)^2\over8\pi} \braket{P_l|f}=


.. math::

       =\sum_{lm}\braket{{\bf\hat r}|lm}f_l \braket{lm|{\bf\hat r'}}

where 

.. math::

       f_l={(2l+1)^2\over8\pi}\braket{P_l|f} ={(2l+1)^2\over8\pi}\int_{-1}^1 \braket{P_l|x}\braket{x|f}\d x ={(2l+1)^2\over8\pi}\int_{-1}^1 P_l(x)f(x)\d x

or written explicitly 

.. math::
    :label: fylm

       f({\bf\hat r}\cdot{\bf\hat r'})= \sum_{l=0}^\infty\sum_{m=-l}^l Y_{lm}({\bf\hat r}) f_l Y_{lm}^*({\bf\hat r'})
