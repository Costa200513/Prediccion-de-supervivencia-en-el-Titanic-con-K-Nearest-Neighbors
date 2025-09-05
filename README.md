# Predicción de Supervivencia en el Titanic con k-Nearest Neighbors (k-NN)

## Introducción
Este proyecto aplica un modelo de clasificación **k-Nearest Neighbors (k-NN)** para predecir qué pasajeros sobrevivieron al hundimiento del Titanic en 1912.  
El desafío se basa en el dataset de **Kaggle: Titanic - Machine Learning from Disaster**, que contiene datos demográficos y socioeconómicos de los pasajeros.

El modelo se entrena con las variables **Age, Sex y Pclass**, seleccionadas por su relevancia histórica en la probabilidad de supervivencia.  

---

## Justificación de la elección de variables
- **Age**: refleja la edad del pasajero; los niños tenían más probabilidades de ser rescatados.  
- **Sex**: el género fue un factor clave, ya que las mujeres tuvieron una mayor tasa de supervivencia.  
- **Pclass**: indica la clase del boleto, relacionada con el nivel socioeconómico y las posibilidades de acceso a los botes salvavidas.  

---

## Preparación de los datos
1. Se cargó el dataset de entrenamiento `train.csv`.  
2. Se transformaron variables categóricas:  
   - `Sex` → valores numéricos (0 = hombre, 1 = mujer).  
   - `Embarked` → valores numéricos (S = 0, C = 1, Q = 2).  
3. Se completaron los valores faltantes en la columna **Age** con la mediana.  
4. Se eliminó la columna **Cabin** por tener demasiados valores nulos.  
5. Los datos se dividieron en conjuntos de **entrenamiento (80%)** y **validación (20%)**.  
6. Se aplicó **StandardScaler** para normalizar las variables numéricas antes de entrenar el modelo.  

---

## Entrenamiento del modelo
- Se dividieron los datos en **entrenamiento (80%)** y **validación (20%)**.  
- Se entrenó un modelo **KNeighborsClassifier** de `sklearn` con `n_neighbors=5`.  
- Se evaluó el rendimiento con la métrica **accuracy**, obteniendo un valor cercano al **80% en validación**.  

---

## Generación de predicciones
1. Se cargó el dataset de prueba `test.csv`.  
2. Se aplicaron las mismas transformaciones de limpieza y escalado.  
3. El modelo predijo la supervivencia de cada pasajero.  
4. Se generó un archivo **`submission.csv`** con las columnas:  
   - `PassengerId`  
   - `Survived` (predicción del modelo)  

Este archivo está en el formato requerido para realizar la entrega en Kaggle.

---

## Conclusión
El modelo **k-NN** demuestra cómo variables simples como **Age, Sex y Pclass** son determinantes en la supervivencia de los pasajeros:  

- **Mujeres y niños** tuvieron mayores probabilidades de sobrevivir.  
- **Pasajeros de primera clase** presentaron mejores tasas de rescate.  
- **Hombres adultos en tercera clase** fueron el grupo más vulnerable.  

