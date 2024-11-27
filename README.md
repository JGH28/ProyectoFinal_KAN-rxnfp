# Universidad de Guadalajara
## Centro Universitario de Ciencias Exactas e Ingenierías
### Ing. Biomédica
### Materia: Métodos Biomédicos de IA
### Profesor: Daniel Farfán

## Proyecto Final - KAN para Clasificación de Reacciones Químicas

### Integrantes del equipo:
Héctor Manuel Godínez Lozano
José de Jesús González Hernández
Diana Romina Miranda Grijalva

## Objetivo del Proyecto
El objetivo principal de este proyecto es utilizar **Kolmogorov-Arnold Networks (KANs)** para clasificar reacciones químicas basadas en sus representaciones SMILES. Al implementar KANs, buscamos mejorar la interpretación y el desempeño del modelo para identificar la **superclase** de cada reacción a partir de su SMILES, un formato ampliamente utilizado para representar la estructura de moléculas y reacciones químicas.

## ¿Por qué usar KANs?
Las **KANs** (Kolmogorov-Arnold Networks) son un tipo de red neuronal inspirada en el teorema de representación de Kolmogorov-Arnold. Este teorema establece que cualquier función continua multivariante puede ser representada como una composición finita de funciones univariantes y la operación de suma. Las KANs aprovechan esta propiedad para aprender representaciones más complejas de los datos, como las relaciones no lineales presentes en las reacciones químicas. Esto las convierte en una herramienta poderosa para tareas de clasificación y análisis interpretables.

## ¿Qué son las KANs?
Las **KANs** son una forma de redes neuronales donde la función de activación no es una operación simple como una suma ponderada, sino que emplea **funciones univariantes** que operan en conjunto. En otras palabras, las KANs pueden descomponer problemas complejos en componentes más simples, lo que les da una alta capacidad de interpretación.

En este proyecto, el objetivo de utilizar KANs es que nos permiten no solo clasificar las reacciones químicas en superclases, sino también entender cómo las KANs "interpretan" los datos. Este enfoque también nos permite observar qué partes de la secuencia SMILES son más relevantes para la clasificación, lo cual es fundamental para interpretar el modelo.

## Estructura del Proyecto
1. **Preparación del Entorno y los Datos**:
   - Instalación de librerías necesarias.
   - Carga y preparación del dataset `schneider50k.csv` con reacciones químicas en formato SMILES.

2. **Preprocesamiento de Datos**:
   - Conversión de las reacciones SMILES en representaciones numéricas mediante codificación **one-hot** con **padding** para asegurar que todas las secuencias tengan la misma longitud.

3. **Definición y Entrenamiento del Modelo KAN**:
   - Construcción de una red KAN para clasificar las reacciones por su **superclase**.
   - Uso de optimizadores como **LBFGS** y funciones de pérdida para entrenar el modelo.

4. **Evaluación del Modelo**:
   - Cálculo de la precisión durante el entrenamiento y la validación.
   - Uso de funciones de métricas personalizadas para evaluar el rendimiento del modelo.

5. **Visualización y Resultados**:
   - Generación de gráficos para visualizar cómo el modelo se ajusta a los datos.
   - Mostrar la fórmula simbólica aprendida por el modelo.

## Instalación
### Requisitos
- **Python 3.9**
- **PyTorch 2.2.2**
- **PyKan 0.2.8**
- **scikit-learn 1.1.3**
- **scipy 1.13.1**
- **matplotlib 3.6.2**
- **pandas**

### Instalación usando Conda
```bash
# Crear un entorno virtual
conda create -n KAN_rxnfp python=3.9

# Activar el entorno virtual
conda activate KAN_rxnfp

# Instalar las dependencias
conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
pip install pykan
pip install pandas matplotlib scikit-learn
```
### Uso
1. Preparar el Dataset: Asegúrate de que el archivo schneider50k.csv esté disponible.
2. Ejecutar el Jupyter Notebook: Abre y ejecuta el notebook KAN_Model.ipynb para entrenar el modelo y generar las predicciones.

### Notas
* El dataset schneider50k.csv se obtuvo de rxn4chemistry GitHub.
* El modelo fue entrenado utilizando un subconjunto de datos debido a limitaciones de recursos computacionales. Es recomendable trabajar con el dataset completo para obtener mejores resultados.

### Explicación Adicional
#### Optimización y Entrenamiento
El optimizador LBFGS fue elegido debido a su capacidad para encontrar un óptimo local en problemas no lineales, algo que es común en redes neuronales como las KANs. Este optimizador es eficiente cuando se trata de modelos con muchos parámetros, como el de este proyecto.

## ¿Por qué utilizar KANs?
A diferencia de las redes neuronales tradicionales, las KANs tienen una ventaja importante: la capacidad de ser interpretables. Esto significa que no solo podemos obtener una clasificación, sino también visualizar y entender qué partes de la entrada están influyendo en la decisión del modelo.

Para más detalles sobre KANs, puedes consultar los siguientes enlaces de la documentación oficial:

- [PyKan GitHub - Hello KAN](https://github.com/KindXiaoming/pykan/blob/master/hellokan.ipynb)
- [PyKan GitHub - Protein Sequence Classification](https://github.com/KindXiaoming/pykan/blob/master/tutorials/Community/Community_2_protein_sequence_classification.ipynb)

## Perspectivas

Creemos que una mejora significativa en el rendimiento del modelo se lograría al contar con una computadora que pueda manejar adecuadamente las 50,000 reacciones del dataset y entrenar con el número necesario de épocas. Esto permitiría obtener una precisión (accuracy) mucho mejor y, además, posibilitaría la visualización completa del modelo. Con más poder computacional y tiempo de entrenamiento, podríamos aprovechar al máximo las capacidades de las KANs para clasificar con mayor exactitud.
