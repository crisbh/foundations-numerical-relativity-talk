---
marp: true
paginate: false
math: katex
theme: default
html: true
style: |
  section {
    font-size: 2.2em !important;
    font-family: 'Arial', sans-serif;
    overflow: hidden;
  }
  img {
    display: block;
    margin: auto;
    width: 60%;
    max-width: 100%;
  }
  .video-container {
    position: relative;
    padding-bottom: 56.25%; /* 16:9 aspect ratio */
    height: 0;
    overflow: hidden;
    max-width: 100%;
    background: black;
  }
  .video-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
---
<!-- _class: lead -->

<img src="../images/logo_cefitev.png"
     style="
      position: absolute;
      top: 10px;
      right: 10px;
      opacity: 0.65;
      width: 250px;
      z-index: 2;
     ">

<img src="../images/logo_uv.png"
     style="
      position: absolute;
      top: 10px;
      left: 10px;
      opacity: 0.70;
      width: 250px;
      z-index: 2;
     ">

<br>

## **Métodos Computacionales y Machine Learning en Física Teórica** 

### Sesión 1: Fundamentos de Relatividad Numérica

Escuela de Física Teórica de Valparaíso 2025

<br>

    Cristian Barrera Hinojosa  
    Instituto de Física y Astronomía
    Universidad de Valparaíso

---

# **Objetivos**

- ¿Qué es la Relatividad Numérica?
- De Newton a Einstein
  - Ideas fundamentales de Relatividad General
- Más allá de las soluciones analíticas
  - Formulación de Cauchy: ADM (3+1)
  - De ADM a BSSN
  <!-- - Métodos numéricos básicos -->

---

# **Motivación**

La Relatividad General (RG) es la **teoría moderna de la gravitación**, pero no es facil lidiar con ella:

- Ecuaciones altamente **no lineales**
- **Pocas soluciones analíticas**
- Fenómenos **dinámicos**  complejos (e.g. colapso gravitacional)

La RN ofrece una vía para resolver numéricamente:

$$
\boxed{
G_{\mu\nu} = 8\pi G T_{\mu\nu}
}
$$

---

<!-- ## **Aplicaciones de la Relatividad Numérica** -->
<!---->
<!-- - **Ondas gravitacionales:** Permite predecir y analizar señales detectadas por observatorios como LIGO y Virgo. -->
<!-- - **Colisión de agujeros negros y estrellas de neutrones:** Permite modelar estos eventos y predecir sus efectos observacionales. -->
<!-- - **Colapso gravitacional y formación de agujeros negros:** Permite estudiar cómo se forman estos objetos. -->
<!-- - **Cosmología computacional:** Permite estudiar la evolución del universo y poner a prueba distintas teorías de la gravitación. -->
<!---->
<!-- --- -->
<img src="../images/Black_hole.webp"
     style="
       position: absolute;
       top: 0;
       left: 0;
       width: 100%;
       height: 100%;
       object-fit: cover;
       opacity: 0.95;
       z-index: 0;
     ">


---

<div class="video-container">
    <iframe 
        src="https://www.youtube-nocookie.com/embed/FGC_DM7ZgAk" 
        frameborder="0" 
        allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen>
    </iframe>
</div>

---

## **Las ondas gravitacionales**

- En 2015, LIGO-VIRGO detectó por **primera vez** una señal de ondas gravitacionales generadas por la fusión de dos agujeros negros.
- Este evento confirmó una predicción importante de la RG: la **existencia** de dichas ondas.
<!-- - Además, abrió una nueva era en la astronomía observacional. -->
- Actualmente se planean nuevos proyectos para medir ondas gravitacionales en el futuro, incluso en el espacio (LISA).

---

<div style="text-align: center;">
  <img src="../images/Nobel_Prize_GW_2017.jpg" width="200px">
</div>

---

# **RN en el contexto moderno**

- Detectores LIGO/Virgo/KAGRA requieren modelos teóricos precisos. 
- Señales de ondas gravitacionales poseen fases:  
  *Inspiral → Merger → Ringdown*.
- RN es el **único** método para obtener la fase de merger correctamente.


---

<div style="text-align: center;">
  <img src="../images/LIGO_measurement_of_gravitational_waves.svg" style="width:780px;">
</div>

---

<br>
<br>
<br>

<p align="center" style="position: relative; z-index: 1;">
  <span style="font-size: 3.0em; font-weight: bold;">De Newton a Einstein</span>
</p>


---

# **La gravedad según Newton**

La teoría de Newton describe la gravedad mediante un potencial:

$$\boxed{
\nabla^2 \Phi = 4\pi G \rho
}
$$

Pero existen algunos problemas:

- Acción instantánea (no causal)
- Falla en altas velocidades ($v \sim c$)
- No predice ondas gravitacionales
- No predice agujeros negros

---

# **La gravedad según Einstein**

Einstein propone que:

> *La gravedad no es una fuerza*.
> *Es la manifestación de la deformación del espaciotiempo*.

Es una teoría **geométrica**, donde objeto fundamental es:

$$
g_{\mu\nu} \quad \leftarrow \text{la métrica del espaciotiempo}
$$

---

<!-- ## **La gravedad y el espaciotiempo**  -->

<!-- <br> -->

<!-- <div style="text-align: center;"> -->
  <!-- <img src="../images/Sun-Earth-Moon-Space-Time.jpg" style="width:600px;"> -->
<!-- </div> -->
<!-- Background image -->
<img src="../images/Sun-Earth-Moon-Space-Time.jpg"
     style="
       position: absolute;
       top: 0; left: 0;
       width: 100%; height: 100%;
       object-fit: cover;
       opacity: 0.85;
       z-index: 0;
     ">

<!-- White overlay -->
<div style="
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(255,255,255,0.05);  /* semi-transparent white */
  z-index: 1;
"></div>

<!-- Equation -->
<div style="
  position: absolute;
  top: 70%;
  width: 100%;
  text-align: center;
  z-index: 3;
  color: black;        /* ensure good contrast */
">

$$
\colorbox{white}{
  $\displaystyle
  G_{\mu\nu} = R_{\mu\nu} - \frac{1}{2} R\,g_{\mu\nu} = 8\pi G\,T_{\mu\nu}
  $
}
$$

<!-- </div> -->
<!-- <img src="../images/Sun-Earth-Moon-Space-Time.jpg" -->
<!--      style=" -->
<!--        position: absolute; -->
<!--        top: 0; -->
<!--        left: 0; -->
<!--        width: 100%; -->
<!--        height: 100%; -->
<!--        object-fit: cover; -->
<!--        opacity: 0.95; -->
<!--        z-index: 0; -->
<!--      "> -->
<!---->
<!-- <div style=" -->
<!--   position: absolute; -->
<!--   top: 0; left: 0; -->
<!--   width: 100%; height: 110%; -->
<!--   background: rgba(0,0,0,0.35); -->
<!--   z-index: 1; -->
<!-- "></div> -->
<!---->
<!-- <div style=" -->
<!--   position: absolute; -->
<!--   top: 40%; -->
<!--   width: 100%; -->
<!--   text-align: center; -->
<!--   z-index: 3; -->
<!-- "> -->
<!---->
<!-- $$ -->
<!-- \boxed{ -->
<!-- G_{\mu\nu} = R_{\mu\nu} - \frac{1}{2} R\,g_{\mu\nu} = 8\pi G\,T_{\mu\nu} -->
<!-- } -->
<!-- $$ -->



---

## **¿Por qué usar tensores?**
- **Pricipio de Relatividad de Einstein**: las leyes de la Física deben ser las mismas en todos los sistemas de coordenadas.
     - Las coordenadas son simplemente etiquetas para eventos. No tienen sentido físico.
     - Los tensores permiten escribir ecuaciones en forma **covariante** (independiente de las coordenadas).

- La métrica $g_{\mu\nu}$ es el **tensor fundamental** en RG.
  - Las ecuaciones de Einstein son **ecuaciones para la métrica**.
---

# **Espaciotiempo y métrica**

Distancias y tiempos se miden mediante:

$$
ds^2 = g_{\mu\nu}\, dx^\mu dx^\nu
$$

Además, permite:
- Manipular índices (subir/bajar)
- Definir las derivadas covariantes
- Definir la curvatura del espaciotiempo


---

## **El Espaciotiempo de Minkowski**

- Un caso particular es el espaciotiempo **plano**, que describe la Relatividad Especial, y se denomina la **métrica de Minkowski**:

$$ g_{\mu\nu} = \eta_{\mu\nu} = \begin{bmatrix} -1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{bmatrix} $$

- En coordenadas cartesianas $x^\mu = (t, x, y, z)$, tenemos:

$$ ds^2 = -dt^2 + dx^2 + dy^2 + dz^2 $$

---

## **Geometría curva**

Si caminamos de forma paralela, ¿qué observamos?

<br>

<div style="text-align:center;">
  <img src="../images/curved_surfaces.jpg" style="width:800px;">
</div>

<!-- --- -->
<!---->
<!-- ## **Geometría curva** -->
<!---->
<!-- Consideremos ahora una esfera. Notar que hablamos de una *superficie*, i.e. un espacio 2D. Usamos coordenadas $(\theta, \phi)$: -->
<!---->
<!-- - $\theta$: ángulo polar (de $0$ a $\pi$) -->
<!-- - $\phi$: ángulo azimutal (de $0$ a $2\pi$) -->
<!---->
<!-- La métrica en la superficie de la esfera de radio $R$ es: -->
<!---->
<!-- $$ -->
<!-- ds^2 = R^2 \left( d\theta^2 + \sin^2 \theta \, d\phi^2 \right) -->
<!-- $$ -->
<!---->

<!-- --- -->
<!---->
<!-- ## **Geometría curva** -->
<!---->
<!-- <!-- Un ejemplo de geometría curva es la superficie de una esfera: --> -->
<!---->
<!-- Si medimos $S$, verificaríamos que el perímetro es $2\pi S$? -->
<!---->
<!-- <div style="text-align: center;"> -->
<!--   <img src="../images/sphere_curvature.png" width="200px"> -->
<!-- </div> -->

<!-- --- -->
<!---->
<!-- ## **Geometría curva** -->
<!---->
<!-- - Si recorremos imaginariamente la superficie, podemos darnos cuenta que el espacio es curvo: -->
<!--   - En el camino mostrado en la figura, podemos verificar que no se respeta la relación $C=2\pi S$. -->
<!--   - Alternativamente, podemos trazar una trayectoria "triangular", y verificar que la suma de los ángulos internos de dicho triángulo es mayor que $180°$. -->
<!---->
<!-- Notar que, *localmente*, la superficie de la esfera **parece plana** en vez de curva (como en el caso de la Tierra).  -->
<!---->

---

# **Geodésicas**

- Las geodésicas son las trayectorias "más rectas" en un espaciotiempo curvo. 
- Estas son las trayectorias que siguen las partículas libres:

$$
\frac{d^2 x^\mu}{d\tau^2}
+ \Gamma^\mu_{\;\alpha\beta}
\frac{dx^\alpha}{d\tau}
\frac{dx^\beta}{d\tau}
= 0
$$

<!-- Este es el análogo a $F^i = m a^i$ en mecánica Newtoniana. -->


donde


$$
\Gamma^\rho{}_{\mu\nu}
= \frac{1}{2} g^{\rho\sigma}
\left(
\partial_\mu g_{\nu\sigma}
+ \partial_\nu g_{\mu\sigma}
- \partial_\sigma g_{\mu\nu}
\right)\quad \text{(símbolos de Christoffel)}
$$

<!-- - Partículas con masa → geodésicas temporales   -->
<!-- - Luz → geodésicas **nulas** ($ds^2=0$) -->

---

# **Curvatura**


- El tensor de Riemann contiene información sobre la **curvatura** del espaciotiempo:

$$
R^\alpha_{\;\beta\gamma\delta} = 
\partial_\gamma \Gamma^\alpha_{\;\delta\beta} - 
\partial_\delta \Gamma^\alpha_{\;\gamma\beta} + 
\Gamma^\alpha_{\;\gamma\mu}\Gamma^\mu_{\;\delta\beta} -
\Gamma^\alpha_{\;\delta\mu}\Gamma^\mu_{\;\gamma\beta}
$$


- Este tensor nos permite identificar un espaciotiempo curvo **independientemente de que coordenadas utilizamos**.

---

# **Curvatura**

Contracciones importantes:

- Tensor de Ricci  
  $$ R_{\mu\nu} = R^\rho_{\;\mu\rho\nu} $$
- Escalar Ricci  
  $$ R = g^{\mu\nu}R_{\mu\nu} $$

---

## **Las ecuaciones de campo de Einstein** 

Las **Ecuaciones de Einstein** (EdE) conectan la geometría del espaciotiempo al contenido de materia y energía:

$$
\boxed{
G_{\mu\nu} = R_{\mu\nu} - \frac{1}{2} R\,g_{\mu\nu} = 8\pi G\,T_{\mu\nu}
}
$$

- **Geometría**: El tensor de Einstein $G_{\mu\nu}$ (curvatura).
- **Materia/Energía**: Tensor de energía-momento $T_{\mu\nu}$ (distribución de masa y energía).

---

## **Las ecuaciones de campo de Einstein** 

En palabras del Físico John Archibald Wheeler:

> *La materia le dice al espacio cómo curvarse, y el espacio curvado le dice a la materia cómo moverse.*

---

## **RG y teoría de Newton**

| Cantidad | Gravedad Newtoniana | Relatividad General |
|---|---|---|
| Campo fundamental | Potencial $\Phi$ | Métrica $g_{\mu\nu}$ |
| Ecuación de movimiento | $F^i=m a^i$ | $a^\mu=0$ (geodésica)|
| Tensor de marea | $R_{ij}=\partial_i \partial_j \Phi$ | Riemann $R^\rho_{\sigma\mu\nu}$ |
| Ecuación de campo | $\nabla^2 \Phi = 4\pi G \rho$ | $G_{\mu\nu} = 8\pi G T_{\mu\nu}$ |


---

## **El tensor de energía-momento** 

El tensor de energía-momento $T_{\mu\nu}$ describe la densidad y flujo de energía y momento en el espaciotiempo.

Ejemplo, para un fluido perfecto:

$$
T^{\mu\nu} = \rho\,u^\mu u^\nu + P\left(g^{\mu\nu} + u^\mu u^\nu\right)
$$

- $\rho$: densidad de energía
- $P$: presión
- $u^\mu$: cuadri-velocidad del fluido

<!-- --- -->
<!---->
<!-- # **Conservación de energía–momento** -->
<!---->
<!-- La identidad de Bianchi implica: -->
<!---->
<!-- $$ -->
<!-- \nabla_\mu G^{\mu\nu} = 0 \quad \Rightarrow \quad -->
<!-- \nabla_\mu T^{\mu\nu} = 0 -->
<!-- $$ -->
<!---->
<!-- Conservación **local** de energía y momento. -->

---

## **La solución de Schwarzschild** 

La métrica de Schwarzschild es una solución a las ecuaciones de Einstein para una partícula puntual (o distribución esférica):
- Vacío (masa-energía solo en el origen)
  - $T_{\mu\nu}=0$ para $r>0$
- Simetría esférica
  - Invariante bajo rotaciones.
- Métrica estacionaria
  - Invariante bajo traslaciones temporales.

---

## **La solución de Schwarzschild** 

El elemento de línea (métrica) de Schwarzschild es:
$$
ds^2 = -\left(1-\frac{2GM}{r}\right)dt^2 + \left(1-\frac{2GM}{r}\right)^{-1}dr^2 + r^2d\Omega^2
$$

donde:
- $d\Omega^2=d\theta^2+\sin^2\theta\,d\phi^2$ (parte angular).
- $M$: parámetro de masa.

---

<!-- ## **La solución de Schwarzschild**  -->
<!---->
<!-- - Notar que se recupera la métrica de Minkowski al alejarse mucho de la partícula  ($r\gg 2GM$): -->
<!--   $$ -->
<!--   ds^2 \approx -dt^2+dr^2+r^2 d\Omega^2 -->
<!--   $$ -->
<!---->
<!-- - Por otra parte: qué pasará cuando la métrica se indetermina? -->
<!---->
<!-- --- -->

<!-- ## **El horizonte de eventos**  -->
<!---->
<!-- - **Radio de Schwarzschild**: -->
<!-- $$ -->
<!-- r_s = \frac{2GM}{c^2} -->
<!-- $$ -->
<!-- - **Horizonte de eventos** en $r=r_s$: la luz no puede escapar. -->
<!-- - La métrica diverge en $r=r_s$. Sin embargo, esta es una **singularidad de coordenadas**, i.e. desaparece si elegimos otro sistema de coordenadas conveniente. -->
<!--   - La divergencia en $r=0$ **sí es física**: la curvatura diverge. -->


## **El horizonte de eventos** 

- **Radio de Schwarzschild**:
$$
r_s = \frac{2GM}{c^2}
$$

- Fuera del horizonte ($r>r_s$): los observadores pueden permanecer estáticos.
- En el horizonte ($r=r_s$): las trayectorias de la luz no puede escapar.
- Dentro del horizonte ($r<r_s$): cualquier trayectoria lleva a la singularidad ($r=0$).

---

<br>
<br>

<p align="center" style="position: relative; z-index: 1;">
  <span style="font-size: 3.0em; font-weight: bold;">Más allá de las soluciones analíticas</span>
</p>


---

## **Más allá de las soluciones analíticas**

- Muchas soluciones conocidas (Schwarzschild, Kerr, FLRW, etc.) son **estáticas** o **altamente simétricas**.
- Muchos fenómenos astrofísicos son **dinámicos** y **no simétricos**.
- Necesitamos resolver las ecuaciones de Einstein **numéricamente**.

Este es el objetivo de la **Relatividad Numérica (RN)**.

---

# **Las ecuaciones de la RN**

- En RN, no resolvemos las ecuaciones de Einstein en su forma covariante original.

- Las ecuaciones covariantes **no están formuladas como problema de Cauchy**.

Para una simulación, queremos:

$$
\text{Condiciones iniciales en } t=0
\quad \longrightarrow \quad
\text{Evolución en el tiempo}
$$

Necesitamos separar **espacio + tiempo**.

---

# **Descomposición 3+1 (ADM)**

<br>

<div style="text-align:center;">
  <img src="../images/adm_bulk.png" style="width:500px;">
</div>

---

# **Descomposición 3+1 (ADM)**

<br>

<div style="text-align:center;">
  <img src="../images/adm_decomposition.png" style="width:800px;">
</div>

---

# **Descomposición 3+1 (ADM)**

- Foliamos el espaciotiempo en una secuencia de hipersuperficies espaciales $\Sigma_t$, normales a un vector temporal $n^\mu$.

- El elemento de línea 4D puede escribirse como:

$$
ds^2 = -\alpha^2 dt^2 
+ \gamma_{ij}(dx^i + \beta^i dt)(dx^j + \beta^j dt)
$$

- Esta descomposición es totalmente **general y exacta**.
- Acá ya solo aparecen índices espaciales ($i,j=1,2,3$).


---

# **Interpretación de las variables**

Componentes de la metrica 3+1:
- $\gamma_{ij}$: métrica espacial  
- $\alpha$: *lapse* → avanza del tiempo propio localmente
- $\beta^i$: *shift* → movimiento de coordenadas espaciales

Además, existe una segunda cantidad fundamental:
- $K_{ij}$: curvatura extrínseca (de cada slice)

---

# **Curvatura extrínseca**

$$
K_{ij}
= -\frac{1}{2\alpha}
\left(
\partial_t \gamma_{ij}
- D_i\beta_j - D_j\beta_i
\right)
$$

- Representa cómo se "inclina" la hipersuperficie en el espaciotiempo.
- Puede pensarse como una "velocidad" de cambio de la métrica espacial (en analogía con mecánica clásica).

---

# **Curvatura extrínseca**

<br>
<div style="text-align:center;">
  <img src="../images/extrinsic_curvature.png" style="width:700px;">
</div>


---
# **Ecuaciones de Einstein (en ADM)**

Con el formalismo ADM, podemos escribir las
ec. de Einstein como un sistema con dos tipos de ecuaciones:

$$
G_{\mu\nu} = 8\pi G T_{\mu\nu}
\;\xRightarrow[\text{ADM 3+1}]{}\;
\begin{cases}
\text{Ecuaciones de evolución} & (\partial_t \gamma_{ij},\, \partial_t K_{ij}) \\
\text{Ecuaciones de restricción} & (\mathcal{H}=0,\, \mathcal{M}^i=0)
\end{cases}
$$

  - **Ecuaciones de evolución** (cómo cambia la geometría espacial en el tiempo). 
  - **Ecuaciones de restricción** (condiciones que deben satisfacer los datos iniciales).

---

# **Ecuaciones de evolución (en ADM)**

$$
\begin{aligned}
\partial_t \gamma_{ij}
&= -2\alpha K_{ij} + D_i \beta_j + D_j \beta_i, \\[4pt]
\partial_t K_{ij}
&= -D_i D_j \alpha
+ \alpha\!\left( R_{ij}
+ K K_{ij}
- 2 K_{i}{}^{k} K_{kj} \right)
+ \beta^k D_k K_{ij} \\[4pt]
&\quad + K_{ik} D_j \beta^k + K_{jk} D_i \beta^k
- 8\pi \alpha
  \left( S_{ij} - \tfrac{1}{2}\gamma_{ij}(S - \rho) \right).
\end{aligned}
$$

- $S_{ij}$: proyección espacial del tensor energía-momento.
- $\rho$: densidad de energía medida por un observador normal a la
hipersuperficie.

---

# **Ecuaciones de restricción**

### Hamiltoniana
$$
\mathcal H \equiv R + K^2 - K_{ij}K^{ij} - 16\pi \rho = 0
$$

### Momento
$$
\mathcal M^i \equiv D_j(K^{ij}-\gamma^{ij}K) - 8\pi j^i = 0
$$

- $j^i$: densidad de momento medida por un observador normal a la hipersuperficie.

<!-- --- -->
<!---->
<!-- # **¿Qué evoluciona realmente en RN?** -->
<!---->
<!-- - La métrica espacial $\gamma_{ij}$   -->
<!-- - La curvatura extrínseca $K_{ij}$ -->
<!-- - Lapse $\alpha$ y shift $\beta^i$ (gauge) -->
<!---->
<!-- El espaciotiempo completo (4D) se reconstruye a partir de estos campos. -->


<!-- # **Elección de gauge** -->
<!---->
<!-- Crucial para estabilidad numérica. -->
<!---->
<!-- Ejemplos modernos: -->
<!---->
<!-- - **1+log slicing**   -->
<!--   $$ \partial_t \alpha = -2\alpha K $$ -->
<!-- - **Gamma-driver shift**   -->
<!--   $$ \partial_t \beta^i = \tfrac34 B^i $$   -->
<!--   $$ \partial_t B^i = \partial_t \tilde\Gamma^i - \eta B^i $$ -->
<!---->
<!-- --- -->


---

# **Problemas del ADM original**

Sin embargo, el sistema de ecuaciones ADM presenta problemas:

- No es *fuertemente hiperbólico*.
- Violaciones de las ecuaciones de restricción crecen en el tiempo.
- Inestabilidades en evoluciones largas.

---

# **BSSN: Estabilizando ADM**

Existen extensiones que introducen modificaciones clave:

- Descomposición conforme de la métrica  
- División de $K_{ij}$ en traza + parte sin traza  
- Introducción de variables de conexión conformes

$\to$ ecuaciones de BSSN (Baumgarte-Shapiro-Shibata-Nakamura)

**Mucho más estable que ADM y usado en RN ampliamente.**


---

# **Discretización**

Métodos numéricos usuales:

- Diferencias finitas de alto orden (4+)
- Esquemas Runge–Kutta para evolución temporal.
- Método de líneas (MoL) para tratar PDEs.
- Refinamiento adaptativo de malla (AMR)


---

# **Visualización: dos agujeros negros**

<br>

<div style="text-align:center;">
  <img src="../images/exagrype_bhs.png" style="width:900px;">
</div>


---

# **Resumen**

- Einstein → ecuaciones tensoriales → PDEs no lineales
- ADM → reformulación como sistema de Cauchy  
- BSSN / CCZ4 → estabilidad y control de errores numéricos
- NR es indispensable para interpretar observaciones modernas  

---

<img src="../images/logo_cefitev.png"
     style="
      position: absolute;
      top: 10px;
      right: 10px;
      opacity: 0.75;
      width: 250px;
      z-index: 2;
     ">

<img src="../images/logo_uv.png"
     style="
      position: absolute;
      top: 10px;
      left: 10px;
      opacity: 0.80;
      width: 250px;
      z-index: 2;
     ">

<img src="../images/exagrype_bhs.png"
     style="
       position: absolute;
       top: 0;
       left: 0;
       width: 100%;
       height: 100%;
       object-fit: cover;
       opacity: 0.35;
       z-index: 0;
     ">

<br><br>

<p align="center" style="position: relative; z-index: 1;">
  <span style="font-size: 4.0em; font-weight: bold;">¡Gracias!</span>
</p>

<!-- <div style="text-align:center;"> -->
<!--   <img src="../images/exagrype_bhs.png" style="width:1000px;"> -->
<!-- </div> -->

