# Laboratorio 3.1 - Amazon SageMaker (Creación e importación de datos)

**Autor:** Santiago Nieto Rodriguez

## Tarea 1 - Creación de un cuaderno de Jupyter con Amazon SageMaker

**Qué hice:** Creé la instancia de cuaderno `MyNotebook` en Amazon SageMaker AI, tipo `ml.m4.xlarge`, con la configuración de ciclo de vida `ml-pipeline`, y esperé a que pasara al estado `InService`.

**Por qué:** Es el entorno base donde se ejecutan los notebooks de las siguientes tareas del laboratorio.

**Evidencia:**
![Configuración de la instancia](evidencias/tarea2_configuracion_instancia.png)
![Instancia creada (Pending)](evidencias/tarea3_instancia_creada.png)
![Instancia en estado InService](evidencias/tarea1_instancia_inservice.png)

## Tarea 2 - Introducción a JupyterLab

**Qué hice:** Exploré la interfaz de JupyterLab (barra de menú, kernel, tipos de celda) y ejecuté por completo el notebook de ejemplo `PythonCheatSheet.ipynb`.

**Por qué:** Familiarizarme con el entorno de trabajo antes de manipular datos reales en los laboratorios 3.2 y 3.3.

**Evidencia:**
![Notebook ejecutado completo](evidencias/tarea4_notebook_ejecutado.png)

## Tarea 3 - Apertura de un cuaderno de muestra

**Qué hice:** Localicé el notebook de muestra `linear_learner_mnist.ipynb` (algoritmo Linear Learner sobre el dataset MNIST), generé una copia editable fuera de la carpeta de solo lectura, agregué mi nombre en una celda de Markdown al inicio, y recorrí su contenido sin ejecutar las celdas de código (requieren un bucket de Amazon S3, según indica el enunciado).

**Por qué:** Familiarizarme con la estructura de un notebook de entrenamiento de modelos de Amazon SageMaker antes de trabajar con datos propios.

**Evidencia:**
![Copia del notebook con nombre en markdown](evidencias/tarea5_linear_learner_copia.png)

## Tarea 4 - Importación de datos

**Qué hice:** Creé un nuevo cuaderno (`vertebral_column_analysis.ipynb`), instalé la dependencia `scipy` en el kernel `conda_python310`, y agregué código para descargar y extraer el conjunto de datos de la columna vertebral (UCI Machine Learning Repository) en formato `.zip`. Cargué el archivo `column_2C_weka.arff` en un DataFrame de Pandas usando `scipy.io.arff`.

**Por qué:** Es el primer paso para trabajar con datos reales en los laboratorios guiados de exploración y codificación de variables.

**Evidencia:**
![Notebook con imports, descarga y DataFrame cargado](evidencias/tarea6_vertebral_notebook_ejecutado.png)
![Archivos extraídos del zip](evidencias/tarea7_archivos_extraidos.png)

## Evidencia adicional

**Acceso a la plataforma del laboratorio:**
![Acceso institucional](evidencias/acceso_plataforma.png)

**Gestión del repositorio (colaborador invitado):**
![Colaboradores del repositorio](evidencias/gestion_repositorio.png)

# Laboratorio 3.2 - Amazon SageMaker (Exploración de datos)

## Sección 3a - Describir los datos

**Qué hice:** Ejecuté el notebook oficial del laboratorio (`3_2-machinelearning.ipynb`) usando mi cuenta institucional de AWS. Exploré la forma, columnas, tipos de datos y estadísticas descriptivas del conjunto de datos de columna vertebral, y visualicé la distribución de cada característica mediante gráficos de densidad, histogramas y boxplots.

**Por qué:** Entender la forma y calidad de los datos (valores atípicos, distribución) antes de construir cualquier modelo de aprendizaje automático.

**Evidencia:**
![Exploración de datos](evidencias/tarea8_exploracion_datos.png)

## Sección 3b - Encontrar correlaciones

**Qué hice:** Convertí la columna `class` (originalmente en bytes) a valores numéricos mediante un mapeador, y analicé la relación entre `degree_spondylolisthesis` y el objetivo mediante un diagrama de dispersión. Generé la matriz de correlación completa y la visualicé como mapa de calor con Seaborn.

**Por qué:** Identificar qué características tienen mayor relación con el diagnóstico (normal/anormal), como insumo para la selección de variables en laboratorios posteriores.

**Evidencia:**
![Matriz de correlación y heatmap](evidencias/tarea9_correlaciones.png)

# Laboratorio 3.3 - Amazon SageMaker (Codificación de datos categóricos)

## Codificación de variables ordinales

**Qué hice:** Cargué el dataset de automóviles (`imports-85.csv`) y lo reduje a cuatro columnas categóricas. Codifiqué `num-of-doors` y `num-of-cylinders` usando diccionarios mapeadores con `.replace()`, ya que sus valores tienen un orden natural (cantidad de puertas/cilindros).

**Por qué:** Los modelos de machine learning requieren entradas numéricas; para variables ordinales, un mapeo directo conserva el orden relativo entre categorías.

## Codificación de variables no ordinales

**Qué hice:** Codifiqué `drive-wheels` (3 valores) con `pd.get_dummies()` estándar, y `aspiration` (2 valores) con `get_dummies(drop_first=True)` para evitar redundancia.

**Por qué:** Para variables sin orden natural, asignar números directamente introduciría una jerarquía artificial; la codificación one-hot evita ese sesgo.

**Evidencia:**
![Codificación ordinal y no ordinal](evidencias/tarea10_codificacion_categorica.png)