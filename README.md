# 🛡️ Detección de Fraude en Reclamos de Seguros

Este proyecto realiza un **Análisis Exploratorio de Datos (EDA)** completo y desarrolla un **Modelo de Machine Learning predictivo** en Python para preclasificar reclamos de seguros de autos bajo sospecha de fraude.

El objetivo principal es identificar patrones característicos en reclamos fraudulentos y dotar a la aseguradora de una herramienta inteligente que clasifique riesgos de forma preventiva, reduciendo pérdidas financieras y optimizando los tiempos del equipo de auditoría.

---

## 📊 Resumen Ejecutivo del Negocio

El fraude en reclamaciones de seguros representa pérdidas de miles de millones de dólares anuales en el sector. En este conjunto de datos, aproximadamente el **24.7%** de las reclamaciones registradas fueron marcadas como fraude. 

A través de un enfoque cuantitativo y predictivo, este análisis demuestra que:
1. **La gravedad del siniestro (`incident_severity`)** es la variable con mayor correlación e importancia para discriminar fraudes.
2. Los accidentes clasificados como **Major Damage (Daño Mayor)** tienen una tasa de fraude del **60.5%**, contra 6.7%-12.9% en el resto de las categorías.
3. El fraude no se correlaciona fuertemente de forma lineal con variables aisladas como la **Edad** o la **Antigüedad del cliente**, lo que ratifica la necesidad de aplicar **modelos multivariables de Machine Learning (como Random Forest)** para capturar interacciones complejas.

---

## 🛠️ Tecnologías y Librerías Utilizadas

El análisis se desarrolló íntegramente en un entorno de **Jupyter Notebook** utilizando el stack clásico de Data Science en Python:

*   **Pandas:** Carga, manipulación y limpieza del dataset.
*   **NumPy:** Operaciones vectoriales y manejo de valores faltantes (`NaN`).
*   **Seaborn & Matplotlib:** Generación de gráficos informativos de alta calidad estética (histogramas, boxplots, diagramas de barras).
*   **Scikit-Learn:** Preprocesamiento de variables (`LabelEncoder`, `train_test_split`) y desarrollo de modelos de Machine Learning (`RandomForestClassifier` y métricas de validación como matriz de confusión, reporte de clasificación, curva ROC y AUC).

---

## 📁 Estructura del Repositorio

*   `insurance_claims_analysis.ipynb`: Notebook principal interactivo con la narrativa paso a paso, código de análisis, gráficos y entrenamiento del modelo.
*   `cleaned_insurance_claims.csv`: Dataset limpio y preparado utilizado para el modelado.
*   `README.md`: Este archivo con la explicación general y hallazgos.

---

## 🧠 Flujo de Trabajo y Metodología

1.  **Exploración y Limpieza**: Identificación de valores nulos (codificados originalmente como `'?'`) y tratamiento estadístico de los mismos. Remoción de variables administrativas ruidosas (como ID de pólizas y coordenadas exactas).
2.  **Análisis de Variable Target**: Diagnóstico del desbalanceo moderado de clases (75.3% legítimo vs. 24.7% fraude) y selección de métricas adecuadas de evaluación.
3.  **Visualizaciones Ejecutivas**: Generación de análisis univariado y bivariado cruzando variables predictoras clave contra la variable respuesta.
4.  **Machine Learning**: Separación estratificada de datos (80% entrenamiento, 20% testeo) y entrenamiento de un clasificador **Random Forest** con balanceo de pesos.
5.  **Evaluación**: Análisis exhaustivo del modelo mediante matriz de confusión, reporte de clasificación (Precision, Recall, F1) y la **Curva ROC-AUC** (**0.82** en el set de prueba).

---

## 🚀 Cómo Ejecutar el Proyecto Localmente

Para clonar y correr este análisis en tu computadora, sigue los siguientes pasos:

1.  **Clonar el repositorio:**
    ```bash
    git clone https://github.com/Luciozanettini/insurance-fraud-analysis.git
    cd insurance-fraud-analysis
    ```

2.  **Instalar las dependencias recomendadas:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Iniciar Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```
    Abre el archivo `insurance_claims_analysis.ipynb` y ejecuta todas las celdas secuencialmente.

---

## 📈 Conclusión del Modelo

| Métrica (set de prueba, 200 reclamos) | Valor |
|---|---|
| ROC-AUC | **0.82** |
| Accuracy | 0.81 |
| Recall de fraude | 0.69 |
| Precisión de fraude | 0.60 |

Las variables con mayor importancia en el modelo son:
1.  **Incident Severity (Severidad del Incidente)**: ~19% de la importancia total.
2.  **Insured Hobbies (Hobbies del asegurado)**: ~9%.
3.  **Property / Vehicle / Total Claim (Montos reclamados)**: ~5-6% cada una.

Con esta solución, la compañía puede prefiltrar reclamos sospechosos y enviarlos a un canal prioritario de investigación, mejorando los márgenes del negocio y acelerando el cobro para clientes con reclamos legítimos.
