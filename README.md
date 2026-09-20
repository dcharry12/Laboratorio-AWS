

# Laboratorios en AWS academy

- **Actividad:4** Laboratorio en AWS
- **Estudiante:** Daniel Felipe Charry Fuentes
- **Docente:** Rodrigo Fernandez Aranda
- **Curso:** Teoría de la Computación 2 - Virtual

## Sobre esta actividad

En este repositorio dejo consignada la evidencia de los tres laboratorios guiados de Amazon SageMaker realizados como parte de la Actividad 4.

* Laboratorio 3.1 – Amazon SageMaker: creación e importación de datos.
* Laboratorio 3.2 – Amazon SageMaker: exploración de datos.
* Laboratorio 3.3 – Amazon SageMaker: codificación de datos categóricos.

## Evidencia de acceso a la plataforma de laboratorio

<img width="1823" height="812" alt="evidencia" src="https://github.com/user-attachments/assets/04ff0f58-f517-4bd3-8d3b-26cde29d9313" />


# Laboratorio 3.1 – Amazon SageMaker: Creación e importación de datos

### ¿Qué hice y por qué?

En este laboratorio el objetivo era dejar lista una instancia de cuaderno en SageMaker y aprender a moverme dentro de JupyterLab antes de trabajar con datos reales. Hice lo siguiente:

1. **Creé una instancia de cuaderno** llamada `MyNotebook`, de tipo `ml.t3.medium`, con la plataforma `Amazon Linux 2023, Jupyter Lab 4`. Dejé el volumen en 5 GB y el rol de IAM que me sugirió la consola (con permisos de SageMaker y S3), porque para este laboratorio no necesitaba nada adicional.
2. **Abrí JupyterLab** una vez la instancia pasó de estado *Pending* a *InService*, y entré directamente a crear mi propio notebook para no perder tiempo revisando plantillas de ejemplo.
3. **Creé mi notebook** (`lab31.ipynb`) y agregué el código para descargar el dataset de la columna vertebral (Vertebral Column Dataset, del repositorio de UCI) directamente desde su URL, extraerlo con `zipfile` y cargarlo en un `DataFrame` de Pandas usando `scipy.io.arff`.
4. Al ejecutar la celda del import me salió `ModuleNotFoundError: No module named 'scipy'`, porque el kernel no lo trae instalado por defecto. Lo resolví agregando `!pip install scipy` en una celda antes del import y volviendo a correr todo.
5. **Cargué los datos** del archivo (`column_2C_weka.arff`) en un `DataFrame` y revisé las primeras filas con `df.head()` para confirmar que la carga había funcionado.

### Pasos y capturas

## 1. Ingreso al laboratorio guiado
Entré a la plataforma de AWS Academy Learner Lab y abrí la guía del Laboratorio 3.1, donde se explican los objetivos: iniciar una instancia de cuaderno de SageMaker, crear un cuaderno de Jupyter, ejecutar código y celdas de Markdown, y descargar datos desde una fuente externa.

<img width="589" height="299" alt="image" src="https://github.com/user-attachments/assets/47b1768d-5c58-4acc-a95f-4a88209b2565" />


## 2. Acceso a la consola de Amazon SageMaker AI
Una vez inicié la sesión de laboratorio, entré a la consola de AWS y navegué hasta el servicio de Amazon SageMaker AI, donde se gestionan los modelos, cuadernos y flujos de trabajo de machine learning.

<img width="589" height="297" alt="image" src="https://github.com/user-attachments/assets/17ec6dad-9993-4a41-a0be-7f66fafddcb3" />


## 3. Sección de Notebooks y repositorios Git
Dentro de SageMaker, fui a la opción "Notebooks" en el panel izquierdo para crear una nueva instancia de cuaderno, ya que en ese momento no había ningún recurso creado.

<img width="589" height="292" alt="image" src="https://github.com/user-attachments/assets/88393f0f-4259-4561-898b-08d4c9bef2fb" />


## 4. Configuración de la instancia del cuaderno
Configuré los parámetros de la nueva instancia:
- Nombre: `MyNotebook`
- Tipo de instancia: `ml.t3.medium`
- Plataforma: Amazon Linux 2023, Jupyter Lab 4
- Volumen: 5 GB
- Rol de IAM asignado con permisos sobre SageMaker y S3

<img width="589" height="276" alt="image" src="https://github.com/user-attachments/assets/d1ccc640-3141-4d1f-a0a4-016886bbee44" />


## 5. Instancia en funcionamiento
Después de crear la instancia, esta pasó al estado **InService**, lo que indica que ya estaba lista para usarse. Desde ahí pude abrir el entorno con las opciones "Abrir Jupyter" o "Abrir JupyterLab".

<img width="589" height="106" alt="image" src="https://github.com/user-attachments/assets/77ada081-4057-4d19-825e-adfcb6b6b3dc" />


## 6. Trabajo en el cuaderno Jupyter (lab31.ipynb)
Dentro de JupyterLab creé el cuaderno `lab31.ipynb` y ejecuté el código para importar los datos:
- Instalé la librería `scipy` con `pip install scipy`.
- Importé las librerías necesarias (`warnings`, `requests`, `zipfile`, `io`, `pandas`, `arff`).
- Descargué el dataset comprimido (`vertebral_column_data.zip`) desde el repositorio de UCI Machine Learning mediante `requests.get()` y lo descomprimí con `zipfile`.
- Cargué el archivo `column_2C_weka.arff` y lo convertí en un DataFrame de pandas para visualizar los datos.

<img width="589" height="282" alt="image" src="https://github.com/user-attachments/assets/574615ba-1a16-4193-88de-ad5b7f55dcb6" />


## 7. Verificación de los datos importados
Finalmente, con `df.head()` visualicé las primeras filas del dataset, confirmando que los datos se importaron correctamente. El DataFrame contiene columnas como `pelvic_incidence`, `pelvic_tilt`, `lumbar_lordosis_angle`, `sacral_slope`, `pelvic_radius`, `degree_spondylolisthesis` y `class`, correspondientes a mediciones biomecánicas de columna vertebral.

<img width="589" height="120" alt="image" src="https://github.com/user-attachments/assets/51520190-f8a3-4d6a-9ea3-a6eff347cd9d" />

# Laboratorio 3.2 – Amazon SageMaker: Exploración de datos

### ¿Qué hice y por qué?

En este laboratorio el objetivo era explorar el conjunto de datos ya importado en el laboratorio anterior, usando estadísticas y gráficos para entender mejor su comportamiento. Hice lo siguiente:

1. **Verifiqué que la instancia** `MyNotebook` siguiera en estado *InService* y abrí el notebook `3_2-machinelearning.ipynb`, donde se plantea el escenario de negocio: detectar anomalías en pacientes ortopédicos según seis características biomecánicas.
2. **Repetí la configuración inicial** (instalar `scipy` e importar los datos) porque cada notebook funciona de forma independiente, así que las librerías y los datos deben cargarse de nuevo aunque ya se hayan usado antes.
3. **Ejecuté `df.describe()`** para obtener una primera impresión numérica de los datos (conteo, media, desviación estándar, mínimos, máximos y cuartiles) antes de pasar a las visualizaciones.
4. Al graficar con `matplotlib` me encontré con el mismo tipo de error del laboratorio anterior (`ModuleNotFoundError`), así que instalé la librería con `!pip install matplotlib` y luego sí pude generar el gráfico general con `df.plot()`.
5. **Profundicé la exploración** con gráficos de densidad por característica, boxplots agrupados por clase, una matriz de dispersión y, finalmente, un mapa de calor de correlación (instalando `seaborn` de la misma forma), para identificar qué variables se relacionan más entre sí y con la clase de diagnóstico.

### Pasos y capturas

## 1. Ingreso al laboratorio guiado
Entré a la plataforma de AWS Academy y abrí la guía del Laboratorio 3.2, cuyos objetivos son explorar y mostrar estadísticas mediante Pandas, y usar gráficos para explorar características de los datos.

<img width="589" height="299" alt="image" src="https://github.com/user-attachments/assets/d5295296-c9df-4a6b-905a-d77d33e47721" />


## 2. Acceso al panel de Amazon SageMaker AI
Ingresé a la consola de AWS y entré al panel general de Amazon SageMaker AI, donde se ve un resumen de los recursos activos (dominios, perfiles de usuario, instancias de cuaderno, etc.).

<img width="589" height="299" alt="image" src="https://github.com/user-attachments/assets/fff3d4a3-a133-4faf-875e-6dbcfea6f42f" />


## 3. Verificación de la instancia de cuaderno
Fui a la sección "Notebooks" y confirmé que la instancia `MyNotebook` seguía en estado **InService**, lista para abrirse en JupyterLab.

<img width="589" height="296" alt="image" src="https://github.com/user-attachments/assets/521dacae-c9e9-45cb-b184-4d4eef0f3adf" />


## 4. Apertura del notebook del laboratorio
Abrí el cuaderno `3_2-machinelearning.ipynb`, donde se presenta el escenario empresarial: mejorar la detección de anomalías en pacientes ortopédicos a partir de seis características biomecánicas, clasificando a los pacientes como *normal* o *anormal*.

<img width="1907" height="921" alt="image" src="https://github.com/user-attachments/assets/75c410cf-77e1-4e23-8f7f-6190805cb9bb" />


## 5. Configuración del laboratorio (carga de datos)
Como este laboratorio continúa el anterior, ejecuté nuevamente las celdas de configuración necesarias para instalar `scipy` e importar los datos (`warnings`, `requests`, `zipfile`, `io`, `pandas`, `arff`), dejando el DataFrame listo para trabajar.

<img width="589" height="284" alt="image" src="https://github.com/user-attachments/assets/34505cd8-14cf-4c4a-a4de-d4b731d2493a" />


## 6. Estadísticas descriptivas con describe()
Ejecuté `df.describe()` para obtener las estadísticas de cada característica del conjunto de datos (conteo, media, desviación estándar, mínimo, máximo y cuartiles) de las seis variables biomecánicas.

<img width="589" height="287" alt="image" src="https://github.com/user-attachments/assets/b8e582aa-a912-4dd3-8f46-e44fc10d987c" />


## 7. Instalación de matplotlib y gráfico general
Instalé la librería `matplotlib` con `pip install matplotlib` y luego grafiqué todas las variables con `df.plot()`, obteniendo una vista general del comportamiento de los datos a lo largo de las 310 observaciones.

<img width="589" height="267" alt="image" src="https://github.com/user-attachments/assets/c1c5dda5-ef93-4149-ad15-400ad3f01339" />


## 8. Gráficos de densidad (KDE) por característica
Generé gráficos de densidad (`kind='density'`) para cada una de las seis características, organizados en una cuadrícula de 4x2, con el fin de observar la distribución individual de cada variable.

<img width="589" height="299" alt="image" src="https://github.com/user-attachments/assets/26f2f508-7f19-492b-a68c-701a3e2ecefc" />


## 9. Boxplots agrupados por clase
Usé `df.groupby('class').boxplot()` para comparar visualmente las características entre los dos grupos de clase (Normal y Anormal), identificando diferencias y posibles valores atípicos entre ambos grupos.

<img width="589" height="297" alt="image" src="https://github.com/user-attachments/assets/3524b9fd-fb57-4ec0-a159-bfe253bf27ed" />


## 10. Matriz de dispersión (scatter matrix)
Con `pd.plotting.scatter_matrix()` generé una matriz de dispersión que muestra la relación entre cada par de variables, además de la distribución individual de cada una en la diagonal.

<img width="589" height="302" alt="image" src="https://github.com/user-attachments/assets/8c9172b8-9a19-415b-a317-e771f612dbe6" />


## 11. Mapa de calor de correlación
Instalé `seaborn`, calculé la matriz de correlación con `df.corr()` y generé un mapa de calor (`sns.heatmap()`) que muestra visualmente el grado de correlación entre las variables. Se observa una alta correlación entre `pelvic_incidence` y `sacral_slope` (0.81), y una correlación moderada entre `degree_spondylolisthesis` y la variable `class` (0.44).

<img width="589" height="288" alt="image" src="https://github.com/user-attachments/assets/e4b79f28-4325-436d-bb54-aec18fc2a182" />

## Conclusión

Este laboratorio permitió comprender la importancia del análisis exploratorio antes de entrenar cualquier modelo de aprendizaje automático. A través de las estadísticas descriptivas, los gráficos de densidad, los boxplots y el mapa de calor de correlación, fue posible identificar patrones relevantes en los datos biomecánicos, como la fuerte relación entre `pelvic_incidence` y `sacral_slope`, así como la influencia de `degree_spondylolisthesis` sobre la variable de clasificación (`class`). Este tipo de análisis resulta clave para tomar decisiones informadas sobre qué características priorizar y qué transformaciones aplicar en las siguientes etapas del proyecto de machine learning.

# Laboratorio 3.3 – Amazon SageMaker: Codificación de datos categóricos

### ¿Qué hice y por qué?

En este laboratorio el objetivo era aprender a codificar variables categóricas de un nuevo conjunto de datos (automóviles), diferenciando entre variables con orden lógico y sin él. Hice lo siguiente:

1. **Verifiqué la instancia** `MyNotebook` en estado *InService* y abrí el notebook `3_3-machinelearning.ipynb`, que trabaja con un dataset distinto al de los laboratorios anteriores: especificaciones de automóviles, su clasificación de riesgo de seguro y sus pérdidas normalizadas.
2. **Importé y exploré los datos** cargando el archivo `imports-85.csv` en un DataFrame (`df_car`), asignando manualmente los nombres de columna porque el archivo no traía encabezado. Confirmé con `df_car.shape` que tenía 205 filas y 25 columnas.
3. **Seleccioné cuatro columnas categóricas** de interés (`aspiration`, `num-of-doors`, `drive-wheels`, `num-of-cylinders`) para trabajar la codificación, todas con valores de texto.
4. **Codifiqué las variables ordinales** (`num-of-doors` y `num-of-cylinders`) usando un diccionario de mapeo y `.replace()`, porque estas sí tienen un orden lógico (más puertas o más cilindros es una cantidad mayor) y convertirlas directamente a su número real conserva esa relación.
5. **Codifiqué las variables no ordinales** con `pd.get_dummies()`: primero `drive-wheels` (generando tres columnas binarias, una por cada tipo de tracción) y luego `aspiration`, esta última usando `drop_first=True` ya que solo tiene dos valores posibles y una sola columna binaria es suficiente para representarla.
6. **Verifiqué el resultado final** con `df_car.head()`, confirmando que todas las columnas quedaron codificadas correctamente y listas para un modelo de machine learning.

### Pasos y capturas

## 1. Ingreso al laboratorio guiado
Entré a la plataforma de AWS Academy y abrí la guía del Laboratorio 3.3, cuyos objetivos son codificar datos categóricos ordinales y datos categóricos no ordinales.

<img width="589" height="300" alt="image" src="https://github.com/user-attachments/assets/6b67de77-1c21-4946-90a4-514582c7fd3f" />

## 2. Acceso al panel de Amazon SageMaker AI
Ingresé a la consola de AWS y entré al panel general de Amazon SageMaker AI para verificar el estado de los recursos disponibles.

<img width="589" height="303" alt="image" src="https://github.com/user-attachments/assets/d71671b4-2c1a-4e2f-af31-21c8c3be7af4" />


## 3. Verificación de la instancia de cuaderno
Fui a la sección "Notebooks" y confirmé que la instancia `MyNotebook` estaba en estado **InService**, lista para abrirse en JupyterLab.

<img width="589" height="300" alt="image" src="https://github.com/user-attachments/assets/4b22b5fc-c7a3-4f0d-acd5-bce4260ec985" />


## 4. Apertura del notebook e introducción al dataset
Abrí el cuaderno `3_3-machinelearning.ipynb`. A diferencia de los laboratorios anteriores, este trabaja con un nuevo conjunto de datos (automóviles) en vez del de columna vertebral. El dataset contiene información sobre especificaciones de vehículos, su clasificación de riesgo de seguro y sus pérdidas normalizadas.

<img width="1919" height="991" alt="image" src="https://github.com/user-attachments/assets/0a8ab38d-cfe9-451f-8666-333ace886c8a" />


## 5. Importación y exploración de los datos
Importé `pandas`, configuré las opciones de visualización y cargué el archivo `imports-85.csv` en un DataFrame (`df_car`), asignando manualmente los nombres de columna ya que el archivo no traía encabezado. Con `df_car.shape` confirmé que el dataset tiene 205 filas y 25 columnas, y con `df_car.head(5)` visualicé las primeras filas.

<img width="589" height="300" alt="image" src="https://github.com/user-attachments/assets/acbae88c-56cd-47bc-b22b-4958c8e935a5" />


## 6. Selección de columnas categóricas a codificar
Revisé los nombres de todas las columnas con `df_car.columns` y seleccioné cuatro columnas de interés (`aspiration`, `num-of-doors`, `drive-wheels`, `num-of-cylinders`) para trabajar la codificación, todas con valores de tipo texto.

<img width="589" height="216" alt="image" src="https://github.com/user-attachments/assets/0a04b263-3303-4f4f-8959-6fd0ca005479" />


## 7. Codificación de variables ordinales
Para las columnas con orden lógico (`num-of-doors` y `num-of-cylinders`), creé un diccionario de mapeo (por ejemplo, "two" → 2, "four" → 4) y usé `.replace()` para convertir los valores de texto en sus equivalentes numéricos, generando las nuevas columnas `doors` y `cylinders`.

<img width="589" height="264" alt="image" src="https://github.com/user-attachments/assets/a8483892-ae06-45e3-9c54-a8eaadb05627" />


## 8. Codificación de variables no ordinales con get_dummies
Para la columna `drive-wheels`, que no tiene un orden lógico entre sus valores (fwd, rwd, 4wd), usé el método `pd.get_dummies()` para generar tres columnas binarias nuevas: `drive-wheels_4wd`, `drive-wheels_fwd` y `drive-wheels_rwd`, donde cada una indica con `True`/`False` si esa observación corresponde a ese tipo de tracción.

<img width="589" height="264" alt="image" src="https://github.com/user-attachments/assets/c742eacd-607b-45be-86d3-5d97acb3a716" />



## 9. Codificación binaria simplificada con drop_first
Para la columna `aspiration`, que solo tiene dos valores posibles (std y turbo), apliqué `get_dummies()` especificando `drop_first=True`, de forma que solo se generó una columna (`aspiration_turbo`), evitando redundancia: si el valor es `False`, se sobreentiende que es `std`.

<img width="589" height="264" alt="image" src="https://github.com/user-attachments/assets/1a0c0b68-d3e8-4f58-864b-bd24f37d760b" />


## 10. Verificación final del DataFrame
Con `df_car.head()` confirmé que el DataFrame final contenía todas las columnas codificadas correctamente: `num-of-doors`, `num-of-cylinders`, `doors`, `cylinders`, `drive-wheels_4wd`, `drive-wheels_fwd`, `drive-wheels_rwd` y `aspiration_turbo`, todas listas para ser usadas en un modelo de machine learning.

<img width="589" height="178" alt="image" src="https://github.com/user-attachments/assets/1e02873b-de0e-47b8-b979-36bfc9d9e252" />


## Conclusión

Este laboratorio permitió comprender la diferencia entre codificar variables categóricas ordinales y no ordinales, dos técnicas fundamentales en el preprocesamiento de datos para machine learning. Mediante el mapeo manual con `.replace()` y el uso de variables dummy con `get_dummies()`, fue posible transformar columnas de texto en representaciones numéricas interpretables por los algoritmos, evitando introducir relaciones de orden inexistentes entre categorías como `drive-wheels`. Esto sienta las bases necesarias para continuar con las siguientes etapas del proyecto de machine learning, como el entrenamiento de modelos predictivos.

## Consideración Final

Desarrollar estos tres laboratorios me permitió entender, de manera práctica, cómo se ve el inicio de un proyecto real de machine learning: desde configurar el entorno y traer los datos, hasta explorarlos y dejarlos listos para un modelo. En el primer laboratorio aprendí a montar una instancia en SageMaker y a conectarme con una fuente externa para importar los datos, una parte que parece básica pero de la que depende que todo lo demás funcione bien más adelante.

Con el segundo laboratorio entendí por qué es tan importante explorar los datos antes de modelarlos, ya que los gráficos y las estadísticas me ayudaron a ver relaciones y comportamientos que no se notan solo mirando la tabla de números. En el tercero, en cambio, aprendí algo que no tenía tan claro: no todas las variables categóricas se codifican igual, hay que fijarse si tienen un orden lógico o no, porque de eso depende usar `.replace()` o `get_dummies()`, y equivocarse ahí puede afectar todo el modelo después.

En general, esta actividad me dejó claro que la mayor parte del trabajo en un proyecto de machine learning está en preparar bien los datos, no solo en entrenar el modelo. También me sirvió para perder el miedo a los errores típicos de Python, como los módulos que faltan, y para moverme con más soltura en un entorno como AWS SageMaker.


