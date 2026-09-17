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

# Laboratorio 3.1 – Amazon SageMaker: Creación e importación de datos

Para este laboratorio ingresé al entorno de AWS Academy y seguí la guía correspondiente al Módulo 3, donde se trabaja la implementación de una canalización de aprendizaje automático usando Amazon SageMaker.

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
