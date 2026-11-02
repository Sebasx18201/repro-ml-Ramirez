# Manifiesto de datos

| Campo | Valor |
|---|---|
| Nombre del archivo en `data/raw/` | `DadosV3.csv` |
| Fuente (institución) | Kaggle Open Datasets |
| Dataset | Sport Services Dataset |
| URL exacta de descarga | https://www.kaggle.com/datasets/saurabhshahane/sport-services-dataset |
| Fecha de descarga | 24 de octubre del 2026 |
| Licencia o condiciones de uso | Open Data Commons — Database Contents License (DbCL) v1.0 (según el informe del proyecto) |
| ¿Se permite redistribuir? | PENDIENTE: verificar las condiciones aplicables antes de redistribuir el archivo. |
| Filas × columnas (raw) | 14 942 × 47 |
| MD5 del archivo raw | `7651033e85d057d52b27b1cfa4a67755` |
| MD5 del archivo processed | `7f668c20ebe1f8c985985f86c7546db8` |

## Diccionario de las variables usadas

El modelo realiza una clasificación binaria para predecir si un socio abandona su membresía en ActivaFit.

| Variable | Tipo | Descripción | Unidad / categorías |
|---|---|---|---|
| `Dropout` | Objetivo | Indica si el socio abandonó su membresía. | Binaria: 0 = permanece; 1 = abandona. |
| `Age` | Numérica | Edad del socio. | Años. |
| `EnrollmentDuration` | Numérica | Duración de la afiliación del socio. | Duración registrada por el dataset; unidad no especificada aquí. |
| `LifetimeValue` | Numérica | Valor acumulado asociado al socio durante su relación con el centro deportivo. | Importe; moneda no especificada aquí. |
| `AverageFrequency` | Numérica | Frecuencia promedio de asistencia del socio. | Frecuencia; periodo de referencia no especificado aquí. |
| `RealNumberOfVisits` | Numérica | Número real de visitas registradas para el socio. | Conteo de visitas; periodo de referencia no especificado aquí. |
| `NumberOfActivities` | Numérica | Número de actividades registradas para el socio. | Conteo. |
| `NumberOfRenewals` | Numérica | Número de renovaciones de la membresía del socio. | Conteo. |
| `Gender` | Categórica | Género registrado para el socio. | `Female`, `Male`. |

## Transformaciones de raw a processed

1. Se lee `data/raw/DadosV3.csv` con `;` como separador. El archivo raw solo se lee y no se modifica.
2. Se eliminan los espacios al inicio y al final de los nombres de las columnas mediante `str.strip()`.
3. Se eliminan las filas duplicadas exactas.
4. El código reemplaza los valores de `CODIGOS_FALTANTES` por valores nulos únicamente si la lista contiene elementos. Actualmente `CODIGOS_FALTANTES` está vacía, por lo que no se ejecuta ningún reemplazo.
5. Se eliminan las filas cuyo valor de `Dropout` es nulo.
6. No hay pasos adicionales de limpieza configurados: no se imputan datos ni se eliminan valores atípicos.
7. El resultado se escribe en `data/processed/dataset.csv` mediante `src/prepare_data.py`.
