## 1. Introducción al Capítulo: Objetivos y Relevancia Estratégica

La cinemática de fluidos es la disciplina que se ocupa de la descripción del movimiento sin entrar en el análisis de las fuerzas o momentos que lo producen. En el marco de la ingeniería mecánica, este estudio no es meramente descriptivo; representa la transición estratégica necesaria para traducir las leyes físicas universales —formuladas originalmente para sistemas de masa fija— al lenguaje de los volúmenes de control espaciales. Esta dicotomía entre sistema y volumen de control es el pilar sobre el cual se construye el análisis de flujo moderno, permitiendo al ingeniero abordar el continuo desde una perspectiva de campo.

Los objetivos fundamentales que el profesional debe dominar en este capítulo incluyen:

- **Derivada Material:** Comprender su rol como operador de transformación entre las descripciones lagrangiana y euleriana.
- **Visualización de Flujo:** Diferenciar patrones cinemáticos (líneas de corriente, traza, senda y tiempo) para interpretar datos experimentales y computacionales.
- **Cinemática de la Deformación:** Evaluar cómo los fluidos se trasladan, rotan y se deforman bajo tasas de strain específicas.
- **Vorticidad y Rotacionalidad:** Identificar regiones de flujo rotacional frente a irrotacional, un concepto crítico para simplificar las ecuaciones de movimiento.
- **Teorema de Transporte de Reynolds (RTT):** Dominar la herramienta de "contabilidad" integral para la conservación de masa, energía y cantidad de movimiento.

Esta comprensión analítica exige, ante todo, la elección de un marco de referencia adecuado para caracterizar el campo de flujo.

## 2. Descripciones del Movimiento: Marcos Lagrangianos vs. Eulerianos

El análisis cinemático exige la dicotomía entre la perspectiva basada en partículas individuales y la perspectiva basada en el campo de flujo. Mientras que el enfoque lagrangiano es el fundamento de la física clásica, el enfoque euleriano es la norma en la práctica de la ingeniería de fluidos.

### Análisis Comparativo de Marcos de Referencia

| Característica                   | Descripción Lagrangiana                                                    | Descripción Euleriana                                                             |
| -------------------------------- | -------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **Definición**                   | Sigue la trayectoria de parcelas individuales de fluido de identidad fija. | Define variables de campo (presión, velocidad) en funciones de posición y tiempo. |
| **Analogía Termodinámica**       | Sistema cerrado (masa de identidad fija).                                  | Volumen de control (región espacial).                                             |
| **Operador Matemático**          | Derivada total (d/dt).                                                     | Derivada material (D/Dt).                                                         |
| **Dificultad de Implementación** | Alta; seguimiento masivo de partículas deformables.                        | Menor; ideal para instrumentación fija y CFD.                                     |
| **Aplicaciones Prácticas**       | Rastreo de contaminantes, flujos rarificados, PIV.                         | Túneles de viento, diseño de turbomaquinaria, aerodinámica.                       |

### El Campo de Flujo Euleriano

Bajo el formalismo euleriano, las propiedades se definen como variables de campo. El vector velocidad $\vec{V}$ se expande en sus componentes cartesianas $(u, v, w)$ como: $\vec{V}(x, y, z, t) = u(x, y, z, t)\vec{i} + v(x, y, z, t)\vec{j} + w(x, y, z, t)\vec{k}$. Esta estructura permite definir campos escalares de presión $P(x, y, z, t)$ y campos vectoriales de aceleración $\vec{a}(x, y, z, t)$. La aplicación de leyes físicas de partículas a estos campos requiere el operador conocido como derivada material.

## 3. La Derivada Material y el Campo de Aceleración

La derivada material (D/Dt) actúa como el puente analítico que permite aplicar las leyes de Newton a un campo euleriano. Matemáticamente, representa la tasa de cambio de una propiedad siguiendo a una partícula fluida.

### Desglose de la Ecuación de Aceleración

La aceleración de una partícula se expresa como la derivada material de la velocidad: $\vec{a} = \frac{D\vec{V}}{Dt} = \frac{\partial\vec{V}}{\partial t} + (\vec{V} \cdot \nabla)\vec{V}$

1. **Aceleración Local ($\partial \vec{V}/\partial t$):** Refleja la falta de estacionariedad. En flujos estacionarios, este término se anula.
2. **Aceleración Advectiva ($\vec{V} \cdot \nabla)\vec{V}$):** Explica el cambio de velocidad debido al movimiento de la partícula hacia regiones con diferentes valores de campo. Este término es responsable de la aceleración en flujos estacionarios a través de conductos de sección variable.

**Caso de Estudio: Aceleración en una Boquilla (Ejemplo 4-2)** Considérese una boquilla de $L = 0.325 \text{ ft}$ con un diámetro de entrada $D_{in} = 0.420 \text{ in}$ y salida $D_{out} = 0.182 \text{ in}$. Con un caudal de $\dot{V} = 0.841 \text{ gpm} (0.00187 \text{ ft}^3/\text{s})$, las velocidades medias resultan en $u_{in} \approx 1.95 \text{ ft/s}$ y $u_{out} \approx 10.4 \text{ ft/s}$. La aceleración axial estimada es: $a_x \cong \frac{u_{out}^2 - u_{in}^2}{2L} = 160 \text{ ft/s}^2$ Esto representa casi cinco veces la aceleración de la gravedad (5g), evidenciando que la aceleración advectiva puede ser masiva incluso en ausencia de cambios temporales.

## 4. Patrones de Flujo y Técnicas de Visualización

La visualización de flujo transforma datos abstractos en comprensión física procesable, permitiendo al ingeniero "ver" fenómenos como la separación de capa límite o la formación de vórtices.

### Definiciones Técnicas de Patrones

- **Líneas de corriente (Streamlines):** Curvas instantáneamente tangentes al vector velocidad $\vec{V}$.
- **Sendas (Pathlines):** Trayectoria histórica real de una partícula individual (concepto lagrangiano).
- **Líneas de traza (Streaklines):** Locus de partículas que pasaron por un punto de inyección fijo (ej. humo).
- **Líneas de tiempo (Timelines):** Conjunto de partículas adyacentes marcadas en t=0; su deformación revela el perfil de velocidad.

### Análisis de Métodos Ópticos (Schlieren y Shadowgraph)

Basados en la refracción de la luz por cambios de densidad ($\rho$), son vitales en flujos supersónicos:

- **Shadowgraph:** Las regiones oscuras indican dónde se originan los rayos refractados; son menos distorsionadas y más útiles para interpretar la posición de ondas de choque (ej. choque de proa en una esfera).
- **Schlieren:** Utiliza un cuchillo de corte (knife edge) para bloquear luz refractada, logrando mayor sensibilidad a gradientes de densidad sutiles sin la distorsión óptica inherente al shadowgraph.

## 5. Propiedades Cinemáticas: Deformación y Tasas de Strain

El movimiento de un elemento fluido se descompone en traslación, rotación, deformación lineal y deformación por cortante. Debido a la naturaleza continua del fluido, estas se expresan como tasas temporales mediante el **Tensor de Tasa de Deformación** ($\varepsilon_{ij}$):

$$\varepsilon_{ij} = \begin{pmatrix} \frac{\partial u}{\partial x} & \frac{1}{2}\left(\frac{\partial u}{\partial y} + \frac{\partial v}{\partial x}\right) & \frac{1}{2}\left(\frac{\partial u}{\partial z} + \frac{\partial w}{\partial x}\right) \\ \frac{1}{2}\left(\frac{\partial v}{\partial x} + \frac{\partial u}{\partial y}\right) & \frac{\partial v}{\partial y} & \frac{1}{2}\left(\frac{\partial v}{\partial z} + \frac{\partial w}{\partial y}\right) \\ \frac{1}{2}\left(\frac{\partial w}{\partial x} + \frac{\partial u}{\partial z}\right) & \frac{1}{2}\left(\frac{\partial w}{\partial y} + \frac{\partial v}{\partial z}\right) & \frac{\partial w}{\partial z} \end{pmatrix}$$

- **Tasa de Deformación Lineal:** Los componentes de la diagonal principal ($\varepsilon_{xx}, \varepsilon_{yy}, \varepsilon_{zz}$).
- **Tasa de Dilatación Volumétrica:** Se define como la divergencia del campo de velocidades: $\frac{1}{\mathcal{V}}\frac{D\mathcal{V}}{Dt} = \nabla \cdot \vec{V}$. Para un **flujo incompresible**, esta suma debe ser idénticamente cero.
- **Tasa de Deformación por Cortante:** Los componentes fuera de la diagonal, cruciales para determinar los esfuerzos viscosos.

## 6. Vorticidad, Rotacionalidad e Irrotacionalidad

La vorticidad ($\vec{\zeta}$) se define como el rotacional del campo de velocidades: $\vec{\zeta} = \nabla \times \vec{V}$. Físicamente, representa el doble del vector de velocidad angular ($\vec{\zeta} = 2\vec{\omega}$).

### Evaluación Técnica de la Rotación

Es imperativo distinguir entre la curvatura de las líneas de corriente y la rotación de las partículas:

- **Vórtice de Cuerpo Sólido (Flujo Rotacional):** $\vec{\zeta} \neq 0$. Las partículas rotan sobre sí mismas (analogía del Carrusel).
- **Vórtice de Línea (Flujo Irrotacional):** $\vec{\zeta} = 0$ en todo el campo, excepto en el origen (r=0), donde existe una **singularidad matemática**. Las partículas mantienen su orientación original mientras orbitan (analogía de la Rueda de la Fortuna).

Esta distinción es la base para la teoría de flujo potencial, donde regiones extensas de flujo se consideran irrotacionales al estar libres de efectos viscosos.

## 7. El Teorema de Transporte de Reynolds (RTT)

El RTT es la herramienta de contabilidad integral que permite la transición de leyes para sistemas cerrados a volúmenes de control abiertos. Es, en esencia, la contraparte integral de la derivada material.

### La Ecuación Maestra del RTT

Para una propiedad extensiva B y su correspondiente propiedad intensiva $b = B/m$:

$$\frac{dB_{sys}}{dt} = \frac{d}{dt} \int_{CV} \rho b \, d\mathcal{V} + \int_{CS} \rho b \vec{V}_r \cdot \vec{n} \, dA$$

1. **Término de Volumen (Unsteady):** Tasa de acumulación o disminución de B dentro del CV.
2. **Término de Superficie (Advectivo):** Flujo neto de B a través de las superficies de control. Se utiliza la **velocidad relativa** $\vec{V}_r = \vec{V} - \vec{V}_{CS}$ para considerar superficies en movimiento o deformación (como álabes de turbina).

El RTT se simplifica para flujos estacionarios eliminando el término temporal, igualando el cambio en el sistema al flujo neto a través de las fronteras.

## 8. Conclusiones y Aplicaciones en Ingeniería Real

La maestría en cinemática de fluidos permite al ingeniero predecir el comportamiento del flujo antes de resolver las complejas ecuaciones de fuerzas. En aplicaciones de **PIV (Velocimetría de Imágenes de Partículas)**, la identificación de contornos de vorticidad es lo que permite localizar con precisión el "vórtice de punta de ala" en aeronaves, un factor crítico para la seguridad y la eficiencia.

Desde el cálculo de la aceleración advectiva en boquillas industriales para evitar la cavitación, hasta la aplicación del RTT en el diseño de sistemas de propulsión, los conceptos de este capítulo (derivada material, tensores de deformación y formalismo de control de volumen) constituyen el lenguaje técnico indispensable para la ingeniería de fluidos avanzada.
