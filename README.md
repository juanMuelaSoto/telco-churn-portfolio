# Predicción de Fuga de Clientes (Telco Customer Churn)

![Python](https://img.shields.io/badge/Python-3.9-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

## Descripción del Proyecto
Este proyecto es una solución **End-to-End de Ciencia de Datos** diseñada para identificar clientes con alta probabilidad de abandonar la compañía de telecomunicaciones (Churn).

El objetivo no es solo predecir, sino **entender las causas raíz** de la fuga para proponer acciones preventivas que impacten directamente en la retención y el *Revenue* de la empresa.

---

## Contexto de Negocio & Problemática
En la industria de telecomunicaciones, el costo de adquirir un nuevo cliente es **5 a 25 veces mayor** que retener a uno existente.
* **Problema:** La empresa enfrenta una tasa de cancelación significativa pero no sabe exactamente *quién* se va ni *por qué*.
* **Solución:** Un modelo de clasificación binaria que asigna una probabilidad de fuga a cada cliente.
* **Impacto:** Permite al equipo de marketing enfocar su presupuesto de retención (descuentos, llamadas) solo en los clientes de alto riesgo.

---

## Insights Clave del Análisis (EDA)
Durante el Análisis Exploratorio de Datos, descubrimos patrones críticos:

1.  **El "Valle de la Muerte":** La mayoría de las fugas ocurren en los primeros **6 meses**. Si logramos que el cliente supere ese umbral, su fidelidad aumenta exponencialmente.
2.  **Contratos Mensuales = Peligro:** Los clientes con contrato "Month-to-month" tienen una tasa de cancelación alarmantemente alta en comparación con los de contrato anual.
3.  **Fibra Óptica:** Curiosamente, los usuarios de Fibra Óptica rotan más que los de DSL, lo que sugiere posibles problemas técnicos o de precio/calidad en ese servicio específico.


---

## Metodología

El flujo de trabajo siguió el ciclo de vida estándar de Data Science:

1.  **Limpieza de Datos:** Manejo de valores nulos y conversión de tipos de datos (`TotalCharges` de object a float).
2.  **EDA (Exploratory Data Analysis):** Análisis univariado y bivariado para entender el comportamiento del cliente.
3.  **Feature Engineering:**
    * **One-Hot Encoding** para variables categóricas.
    * **Scaling** para variables numéricas (evitando *Data Leakage* al ajustar solo en train).
4.  **Modelado:** Comparación entre **Regresión Logística** (Baseline) y **Random Forest**.
5.  **Evaluación:** Enfoque en métricas de **Recall** debido al desbalance de clases (es más costoso no detectar a un cliente que se va).

---

## Resultados del Modelo

| Modelo | Accuracy | Recall (Clase Churn) | Observación |
| :--- | :---: | :---: | :--- |
| **Regresión Logística** | 80% | ~55% | Gran interpretabilidad (pesos de variables). |
| **Random Forest** | 79% | ~50% | Mejor manejo de no-linealidad, pero tiende al overfitting si no se ajusta. |

> **Decisión:** Se priorizó la interpretabilidad de la Regresión Logística para explicar al negocio qué factores impulsan la fuga.

### Factores de Riesgo Identificados (Top Drivers)
Las variables que más empujan a un cliente a irse son:
1. Tener servicio de **Fibra Óptica**.
2. Tener un contrato **Mensual**.
3. No tener servicio de **Soporte Técnico**.

---

## Estructura del Repositorio

```text
├── data/                # Dataset crudo y procesado
├── images/              # Gráficas generadas para el reporte
├── notebooks/           # Telco_Churn_End_to_End.ipynb,Jupyter Notebook con el análisis paso a paso
├── README.md            # Descripción del proyecto
└── requirements.txt     # Librerías necesarias