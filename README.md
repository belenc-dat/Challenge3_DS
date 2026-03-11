# Challenge3_DS
Retención de Clientes (Churn)
Descripción del Proyecto
Este proyecto busca identificar factores de cancelación (churn) de clientes y desarrollar modelos predictivos para anticipar qué clientes podrían abandonar el servicio. El objetivo es ofrecer recomendaciones estratégicas para mejorar la retención.

Datos
Se utilizó un dataset con información de clientes (demográficos, servicios, facturación, Churn).

Churn: Variable objetivo (0 = No cancela, 1 = Cancela).
Variables clave: tenure, Monthly, Total, InternetService, Contract, PaymentMethod, gender, SeniorCitizen, Partner, Dependents, PhoneService, MultipleLines, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies, PaperlessBilling, Daily.
Metodología
Limpieza de Datos: Carga, eliminación de customerID y manejo de nulos en Total.
Preprocesamiento: Eliminación de outliers (Z-score < 3), One-Hot Encoding para categóricas, y manejo de multicolinealidad (VIF).
Balanceo de Clases: Verificación de Churn y aplicación de SMOTE en el entrenamiento si hay desbalance.
Análisis Exploratorio: Correlaciones (Pearson, Spearman) y visualizaciones clave (tenure, Monthly, Total).
Modelado Predictivo: División de datos (70/30 estratificado) y entrenamiento de Regresión Logística (LR), Random Forest (RF) y K-Nearest Neighbors (KNN).
Evaluación: Métricas de rendimiento (classification_report, confusion_matrix, roc_auc_score) y validación cruzada (f1_macro).
Importancia de Características: Análisis con Permutation Importance y feature importances de Random Forest.
Modelos y Resultados
Modelo	Accuracy (Test)	AUC (Test)	F1-macro (CV)	Principales Características (Importancia)
Regresión Logística	0.74	0.864	0.773	tenure, Contract_two_year, InternetService_fiber_optic, Monthly, Total, PaymentMethod_electronic_check
Random Forest	0.81	0.846	0.824	Total, Monthly, tenure, PaymentMethod_electronic_check, InternetService_fiber_optic, PaperlessBilling
K-Nearest Neighbors	0.70	0.771	0.773	tenure, Total, Monthly, PaymentMethod_electronic_check, InternetService_fiber_optic
Observaciones Clave:

Random Forest fue el mejor en Accuracy y F1-macro en el test, con buen rendimiento pero signos de sobreajuste en el entrenamiento.
Regresión Logística tuvo el AUC más alto, excelente para discriminar y con buen recall para la clase Churn.
KNN fue el modelo con menor rendimiento.
Las variables tenure, Monthly, Total, InternetService_fiber_optic, Contract_two_year y PaymentMethod_electronic_check fueron consistentemente las más influyentes.

Recomendaciones
Las cancelaciones están fuertemente ligadas a la antigüedad (tenure), el costo (Monthly, Total) y los servicios (InternetService_fiber_optic, OnlineSecurity, TechSupport).

Los clientes nuevos (tenure baja) y aquellos con precios altos o contratos cortos tienen mayor riesgo.

Estrategias sugeridas:

Fidelización de Nuevos Clientes: Ofrecer beneficios iniciales para aumentar la tenure.
Revisión de Precios: Analizar tarifas para contratos cortos y ofrecer incentivos para contratos de mayor duración.
Mejora de Servicios: Destacar el valor de la seguridad online y soporte técnico.
Análisis Segmentado: Estudiar a fondo segmentos de alto riesgo (ej. fibra óptica, cargos altos) para ofertas personalizadas.
