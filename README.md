# Deteccion temprana de Alzheimer con machine learning

Repositorio academico para analizar un dataset sintetico de pacientes y construir modelos predictivos que clasifiquen el diagnostico de Alzheimer.

**Responsable del repositorio:** Renzo Salazar Chavez

## Resumen

El proyecto evalua variables demograficas, clinicas, cognitivas y de estilo de vida para identificar predictores asociados al diagnostico de Alzheimer. La variable objetivo es binaria:

- `0`: Sin diagnostico de Alzheimer
- `1`: Con diagnostico de Alzheimer

El flujo de trabajo incluye analisis exploratorio, pruebas estadisticas, seleccion de variables, preprocesamiento, comparacion de modelos y validacion del rendimiento.

## Dataset

- Fuente: Kaggle, `rabieelkharoua/alzheimers-disease-dataset`
- Tipo: dataset sintetico de pacientes
- Registros: 2,149 pacientes
- Archivo esperado: `alzheimers_disease_data.csv`

Por defecto, el script descarga el dataset con `kagglehub`. Tambien puedes descargarlo manualmente y colocarlo en `data/alzheimers_disease_data.csv`.

## Resultados principales

| Modelo final | Accuracy | F1-Score | AUC aproximado |
| --- | ---: | ---: | ---: |
| Random Forest | 0.9535 | 0.9333 | 0.98 |

Random Forest fue seleccionado como modelo final por su rendimiento y robustez. El arbol de decision obtuvo resultados muy cercanos; la prueba de McNemar reportada en el analisis dio `p = 0.125`, por lo que no se observo una diferencia estadisticamente significativa entre ambos modelos, aunque Random Forest mantiene una mejor estabilidad como ensamble.

Variables mas relevantes:

- Evaluacion funcional
- Actividades diarias
- MMSE
- Quejas de memoria
- Problemas de conducta

## Estructura del repositorio

```text
alzheimers-disease-ml/
├── data/                 # Instrucciones para obtener el dataset
├── docs/                 # Resumen metodologico y guia de publicacion
├── models/               # Modelos generados localmente
├── reports/              # Metricas y graficos generados
├── src/
│   └── alzheimers_analysis.py
├── .gitignore
├── README.md
└── requirements.txt
```

## Como ejecutar

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python src/alzheimers_analysis.py
```

Si ya tienes el CSV descargado:

```powershell
python src/alzheimers_analysis.py --data-path data/alzheimers_disease_data.csv
```

El script genera:

- `reports/model_metrics.csv`
- `reports/confusion_matrix.png`
- `reports/random_forest_feature_importance.png`
- `reports/bootstrap_summary.json`
- `models/best_model.joblib`

## Nota de publicacion

Esta version esta preparada para GitHub como repositorio personal de Renzo Salazar Chavez. Los PDFs originales del informe y la presentacion no se incluyen como archivos principales porque contienen una portada grupal. Si decides subir documentos originales del curso, conserva los creditos correspondientes.

## Limitaciones

El dataset es sintetico y el modelo no debe usarse como herramienta clinica real. Los resultados son utiles para fines academicos, demostracion de metodologia y portafolio de ciencia de datos.
