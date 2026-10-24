(cap-ensayos)=
# Apéndice: ensayos geotécnicos

Este apéndice resume los ensayos de campo y de laboratorio que se usan para caracterizar los materiales. En el curso no se estudian en un capítulo aparte: cada estudiante los consulta y los presenta a medida que aparecen los temas relacionados, y forman parte de la participación en clase. El objetivo es que el geólogo sepa qué ensayo pedir, cómo interpretarlo y cuáles son sus limitaciones, más que dominar los detalles de su ejecución.

## Exploración del subsuelo

La exploración busca definir la estratigrafía, la posición del nivel freático y las propiedades de los materiales en el volumen afectado por la obra. Su diseño, es decir, el número, la ubicación y la profundidad de los sondeos, debe partir del modelo geológico preliminar. Los **apiques** o calicatas permiten observar directamente el perfil y tomar muestras de bloque inalteradas, pero se limitan a pocos metros. Los **sondeos** con barreno, lavado o rotación permiten llegar a mayores profundidades; en roca, la perforación con recuperación de núcleos permite calcular el RQD y describir las discontinuidades. La NSR-10 (capítulo H.3) establece el número mínimo y la profundidad de los sondeos según la categoría de la unidad de construcción.

### Toma de muestras

Las **muestras alteradas** conservan la composición pero no la estructura del suelo, y sirven para ensayos de clasificación (granulometría, límites, humedad). Las **muestras inalteradas** conservan en lo posible la estructura, la humedad y el estado de esfuerzos, y son indispensables para ensayos de resistencia y compresibilidad. Se toman con tubos de pared delgada (Shelby) en suelos finos, con muestreadores de pistón en suelos blandos o tallando bloques en apiques. Ninguna muestra es totalmente inalterada: la relajación de esfuerzos, la perturbación mecánica y los cambios de humedad la afectan, en especial en suelos residuales con cementación débil.

## Ensayos de campo

### Ensayo de penetración estándar (SPT)

Se hinca un muestreador de cuchara partida con un martillo de 63,5 kg que cae 76 cm, y se cuenta el número de golpes necesario para avanzar 30 cm después de un asentamiento inicial de 15 cm: el valor $N$. Es el ensayo de campo más usado en Colombia, por su sencillez y porque permite recuperar una muestra alterada. El valor de $N$ se corrige por energía del martillo ($N_{60}$) y por esfuerzo efectivo, y se correlaciona con la densidad relativa y el ángulo de fricción de las arenas, la consistencia de las arcillas, la capacidad portante y el potencial de licuación. En suelos con gravas y bloques, como los coluviones, sus resultados son poco confiables.

### Ensayo de penetración de cono (CPT y CPTu)

Un cono con punta de 60° y 10 cm² de área se hinca a velocidad constante, midiendo de manera continua la resistencia de punta y la fricción lateral, y en el piezocono (CPTu) también la presión de poros. Da un perfil continuo y detallado de la estratigrafía, muy útil para detectar lentes delgados, pero no recupera muestras y no penetra materiales gruesos o cementados.

### Ensayos de permeabilidad

El **ensayo Lefranc** se realiza en un tramo de sondeo en suelo, inyectando o extrayendo agua con carga constante o variable, para obtener la conductividad hidráulica. El **ensayo Lugeon** se realiza en roca, inyectando agua a presión en un tramo aislado con obturadores. Su resultado se expresa en unidades Lugeon: una unidad equivale a una absorción de 1 litro por minuto y por metro de sondeo a una presión de 10 bar, aproximadamente $10^{-7}$ m/s. Además, los ensayos de bombeo en pozos dan la conductividad promedio de un acuífero a mayor escala.

### Prospección geofísica

Los métodos geofísicos son indirectos, pero cubren grandes áreas y volúmenes a bajo costo, y permiten extender lateralmente la información de los sondeos. Los **sondeos eléctricos verticales** (SEV) y la tomografía eléctrica miden la resistividad del terreno, que depende del contenido de agua, la porosidad, el contenido de arcilla y la salinidad; sirven para localizar el nivel freático, el contacto con la roca y las zonas saturadas en laderas. Los **métodos sísmicos** de refracción y de ondas superficiales (MASW) miden la velocidad de las ondas, que se relaciona con la rigidez del material; permiten estimar la profundidad de la roca y su grado de fracturación, y son la base para clasificar el perfil de suelo para el diseño sísmico. El georradar, la gravimetría y la magnetometría tienen aplicaciones más específicas. Toda interpretación geofísica debe calibrarse con sondeos.

### Ensayos in situ de resistencia y deformabilidad

La **veleta** de campo mide la resistencia no drenada de arcillas blandas. El **presiómetro** y el dilatómetro miden la deformabilidad del suelo en las paredes de un sondeo. El **ensayo de placa** mide el asentamiento de una placa rígida bajo carga, y el martillo de Schmidt y el ensayo de carga puntual estiman la resistencia de la roca en campo.

### Instrumentación

La instrumentación permite medir el comportamiento del terreno durante y después de la construcción, y es la base del método observacional de Peck. Los **piezómetros** miden la presión de poros; los **inclinómetros** miden los desplazamientos horizontales a lo largo de un sondeo y permiten localizar la superficie de falla de un deslizamiento; los **extensómetros** miden desplazamientos entre puntos; y las **celdas de asentamiento** y las mediciones topográficas o con GNSS registran los movimientos superficiales. En laderas inestables, la combinación de inclinómetros, piezómetros y pluviómetros es la herramienta más eficaz para entender el mecanismo y diseñar sistemas de alerta.

## Ensayos de laboratorio

### Ensayos de clasificación

La **humedad natural** se obtiene secando la muestra al horno a 110 °C. Los **límites de Atterberg** se determinan con la cuchara de Casagrande o el penetrómetro de cono para el límite líquido, y rolando cilindros de 3 mm para el límite plástico. La **granulometría** se determina por tamizado y por hidrómetro, y la **gravedad específica**, con el picnómetro. Con estos ensayos se clasifica el suelo según el USCS (capítulo {ref}`cap-suelos`).

### Compresión simple

Se aplica una carga axial a una probeta sin confinamiento hasta la falla. En suelos cohesivos saturados da la resistencia no drenada, $c_u=q_u/2$; en rocas, la resistencia a la compresión uniaxial $\sigma_{ci}$, que es el parámetro básico de las clasificaciones geomecánicas y del criterio de Hoek-Brown.

### Corte directo

Mide la resistencia al corte en un plano impuesto, bajo esfuerzo normal constante (capítulo {ref}`cap-corte`). Con reversiones o en el equipo de corte anular permite medir la resistencia residual. En roca se usa para medir la resistencia de las discontinuidades.

### Ensayos triaxiales UU, CU y CD

Permiten controlar el drenaje y medir la presión de poros, y reproducir diferentes trayectorias de esfuerzos. El ensayo UU da la resistencia no drenada para el análisis a corto plazo; el CU con medición de presión de poros da los parámetros totales y efectivos; y el CD, los parámetros efectivos para el análisis a largo plazo (capítulo {ref}`cap-corte`).

### Consolidación

El ensayo edométrico da la curva de compresibilidad, los índices $C_c$ y $C_s$, la presión de preconsolidación y el coeficiente de consolidación $c_v$ (capítulo {ref}`cap-consolidacion`).

### Compactación

Los ensayos Proctor estándar y modificado definen el peso unitario seco máximo y la humedad óptima de los materiales para rellenos (capítulo {ref}`cap-compactacion`).
