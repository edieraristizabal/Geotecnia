(cap-esfuerzos)=
# Estado de esfuerzos

:::{important}
**Objetivos de aprendizaje**

- Definir esfuerzo normal y cortante, y el tensor de esfuerzos en un punto.
- Calcular los esfuerzos sobre un plano cualquiera y los esfuerzos principales en dos dimensiones.
- Construir el círculo de Mohr y usar el método del polo.
- Representar estados de esfuerzos y trayectorias en diagramas p-q.
:::

## El terreno como medio esforzado

El terreno, bajo la acción de su propio peso y de las cargas que le transmiten las estructuras, está sometido en cada punto a un estado de esfuerzos. Conocerlo es el primer paso para resolver los dos grandes tipos de problemas de la geotecnia. En los **problemas de deformación** los esfuerzos se mantienen muy por debajo de la resistencia del material y lo que interesa es cuánto se deforma el terreno: asentamientos de cimentaciones o desplazamientos de excavaciones. En los **problemas de estabilidad** interesa si los esfuerzos alcanzan la resistencia en alguna superficie y el terreno falla: capacidad portante, estabilidad de taludes y empujes sobre muros.

Para el geólogo el concepto no es nuevo. El estado de esfuerzos de la corteza se estudia en geología estructural para explicar el fallamiento y el plegamiento, y las mismas herramientas (el tensor de esfuerzos y el círculo de Mohr) sirven para entender por qué una falla normal buza 60° o por qué se abre una grieta de tracción en la corona de un talud. La diferencia es de convención: en geotecnia y en geología los esfuerzos de **compresión se consideran positivos**, al contrario de la mecánica de materiales.

## Definiciones

Una fuerza $F$ que actúa sobre un plano de área $A$ se puede descomponer en una componente normal $F_n$ y una tangencial $F_t$. Se definen el esfuerzo normal y el esfuerzo cortante como:

$$
\sigma=\frac{F_n}{A}\qquad\tau=\frac{F_t}{A}
$$

En un suelo, que es un medio particulado, estos esfuerzos son promedios sobre un área que contiene muchos granos; las fuerzas reales se transmiten por los contactos entre partículas. Esta idealización como medio continuo es razonable cuando el área considerada es grande respecto al tamaño de los granos.

### Tensor de esfuerzos

El estado de esfuerzos en un punto queda definido considerando un cubo elemental orientado según un sistema de ejes $x$, $y$, $z$. Sobre cada cara actúan un esfuerzo normal y dos cortantes, que se agrupan en el tensor de esfuerzos:

$$
\boldsymbol{\sigma}=\begin{bmatrix}\sigma_x & \tau_{xy} & \tau_{xz}\\ \tau_{yx} & \sigma_y & \tau_{yz}\\ \tau_{zx} & \tau_{zy} & \sigma_z\end{bmatrix}
$$

Por equilibrio de momentos el tensor es simétrico ($\tau_{xy}=\tau_{yx}$, etc.), de modo que bastan seis componentes independientes. Para cualquier estado de esfuerzos existen tres planos perpendiculares entre sí, los **planos principales**, sobre los cuales el esfuerzo cortante es nulo. Los esfuerzos normales sobre ellos son los esfuerzos principales, $\sigma_1\ge\sigma_2\ge\sigma_3$.

```{figure} images/4/s05_0470.webp
:width: 55%
:name: fig-cubo

Componentes del esfuerzo sobre un cubo elemental.
```

## Análisis bidimensional

Muchos problemas geotécnicos se pueden reducir a dos dimensiones. En muros, terraplenes, cortes de carreteras y cimentaciones corridas, una dimensión es mucho mayor que las otras y la deformación en esa dirección es despreciable: es la condición de **deformación plana**. El estado de esfuerzos queda definido entonces por $\sigma_x$, $\sigma_z$ y $\tau_{xz}$.

Sobre un plano cuya normal forma un ángulo $\theta$ con el eje $x$, el equilibrio de un elemento triangular da:

$$
\sigma_\theta=\frac{\sigma_x+\sigma_z}{2}+\frac{\sigma_x-\sigma_z}{2}\cos2\theta+\tau_{xz}\sin2\theta
$$

$$
\tau_\theta=\frac{\sigma_x-\sigma_z}{2}\sin2\theta-\tau_{xz}\cos2\theta
$$

Los esfuerzos principales y el cortante máximo son:

$$
\sigma_{1,3}=\frac{\sigma_x+\sigma_z}{2}\pm\sqrt{\left(\frac{\sigma_x-\sigma_z}{2}\right)^2+\tau_{xz}^2}\qquad
\tau_{max}=\frac{\sigma_1-\sigma_3}{2}
$$

y la orientación de los planos principales cumple $\tan2\theta_p=2\tau_{xz}/(\sigma_x-\sigma_z)$.

## El círculo de Mohr

Mohr (1882) observó que las ecuaciones anteriores son las ecuaciones paramétricas de una circunferencia en el plano $\sigma$-$\tau$, con centro en $\left((\sigma_x+\sigma_z)/2,\,0\right)$ y radio igual a $\tau_{max}$. Cada punto del círculo representa los esfuerzos sobre un plano que pasa por el punto analizado. Para construirlo:

1. Se grafican los puntos $(\sigma_x,\tau_{xz})$ y $(\sigma_z,-\tau_{xz})$, que representan los esfuerzos sobre los planos perpendiculares a los ejes $x$ y $z$.
2. Se unen los dos puntos con una línea, que corta el eje $\sigma$ en el centro del círculo.
3. Se traza la circunferencia con ese centro que pasa por ambos puntos.

Los cortes del círculo con el eje $\sigma$ son los esfuerzos principales; el punto más alto da el cortante máximo, que actúa sobre planos a 45° de los principales. Un ángulo $\theta$ entre dos planos en el terreno corresponde a un ángulo $2\theta$ entre los puntos que los representan en el círculo.

```{figure} images/4/s12_0475.webp
:width: 65%
:name: fig-mohr

Construcción del círculo de Mohr.
```

### El método del polo

Sobre todo círculo de Mohr existe un punto único llamado **polo** u origen de planos, con la siguiente propiedad: una línea trazada desde el polo paralela a un plano cualquiera del terreno corta el círculo en el punto cuyas coordenadas son los esfuerzos sobre ese plano. El polo permite trabajar directamente con la geometría del problema, sin ángulos dobles. Para encontrarlo se parte de un punto con esfuerzos conocidos, por ejemplo el que representa el plano horizontal, y se traza una paralela a ese plano: donde corta el círculo está el polo. Las líneas que unen el polo con $\sigma_1$ y $\sigma_3$ dan las orientaciones de los planos principales.

```{figure} images/4/s16_0479.webp
:width: 60%
:name: fig-polo

Método del polo u origen de planos.
```

:::{admonition} Ejemplo resuelto: esfuerzos principales y esfuerzos sobre un plano
:class: note
En un punto del terreno $\sigma_x=100$ kPa, $\sigma_z=40$ kPa y $\tau_{xz}=20$ kPa. Calcule los esfuerzos principales, su orientación y los esfuerzos sobre un plano a $\theta=30°$.

**Centro y radio:** $c=(100+40)/2=70$ kPa; $R=\sqrt{30^2+20^2}=36{,}1$ kPa.

**Esfuerzos principales:** $\sigma_1=70+36{,}1=106{,}1$ kPa y $\sigma_3=70-36{,}1=33{,}9$ kPa. El cortante máximo es 36,1 kPa.

**Orientación:** $\tan2\theta_p=2(20)/(100-40)=0{,}667$, de donde $2\theta_p=33{,}7°$ y $\theta_p=16{,}8°$.

**Plano a 30°:**
$\sigma_\theta=70+30\cos60°+20\sin60°=70+15+17{,}3=102{,}3$ kPa;
$\tau_\theta=30\sin60°-20\cos60°=26{,}0-10=16{,}0$ kPa.
:::

## Estado de esfuerzos geostático

En un terreno de superficie horizontal sin cargas externas, los planos horizontal y vertical son principales por simetría. El esfuerzo vertical se debe al peso del material suprayacente, $\sigma_v=\sum\gamma_i h_i$, y el horizontal se relaciona con él mediante el **coeficiente de presión de tierras en reposo**, $K_0=\sigma'_h/\sigma'_v$, definido en términos de esfuerzos efectivos (capítulo {ref}`cap-efectivos`). En un suelo normalmente consolidado $K_0<1$ y suele estimarse con la fórmula de Jaky, $K_0\approx1-\sin\phi'$. En suelos sobreconsolidados, en zonas sometidas a erosión intensa o en regiones tectónicamente activas, $K_0$ puede ser mayor que 1, con el esfuerzo horizontal como principal mayor. Esta situación es común en los macizos rocosos y tiene consecuencias importantes en túneles y excavaciones profundas.

## Diagramas p-q y trayectorias de esfuerzos

Cuando se quieren representar muchos estados de esfuerzos, por ejemplo los sucesivos estados de una muestra durante un ensayo triaxial, dibujar todos los círculos de Mohr resulta confuso. Una alternativa es representar cada círculo por un solo punto, el de su cortante máximo, con coordenadas:

$$
p=\frac{\sigma_1+\sigma_3}{2}\qquad q=\frac{\sigma_1-\sigma_3}{2}
$$

La línea que une los puntos sucesivos se denomina **trayectoria de esfuerzos**. En el diagrama p-q la envolvente de falla de Mohr-Coulomb se transforma en la línea $K_f$, de ecuación $q=a+p\tan\alpha$, cuyos parámetros se relacionan con los de resistencia mediante $\sin\phi=\tan\alpha$ y $c=a/\cos\phi$. Las trayectorias muestran de un vistazo cómo se acerca cada elemento del terreno a la falla durante la construcción o la excavación, y son especialmente útiles para comparar condiciones drenadas y no drenadas (capítulo {ref}`cap-corte`).

```{figure} images/4/s43_0501.webp
:width: 70%
:name: fig-trayectorias

Trayectorias de esfuerzos en el diagrama p-q.
```

## Lecturas recomendadas

- {cite:t}`holtz_introduction_1981`, capítulo 10, sobre el círculo de Mohr y el método del polo.
- {cite:t}`lambe_soil_1969`, capítulo 8, sobre trayectorias de esfuerzos.

## Ejercicios

1. Para $\sigma_1=200$ kPa (vertical) y $\sigma_3=80$ kPa (horizontal), encuentre con el método del polo los esfuerzos sobre un plano que buza 35°.
2. Dibuje la trayectoria de esfuerzos en el diagrama p-q de un elemento bajo el centro de un terraplén al aumentar la altura, y la de un elemento detrás de un muro que se desplaza hacia afuera.
3. ¿Qué indica sobre la historia geológica de un macizo un valor medido de $K_0=1{,}8$ a 50 m de profundidad?
