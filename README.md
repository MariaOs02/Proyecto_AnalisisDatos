# Proyecto_AnalisisDeDatos
Pipeline de limpieza, validación mediante contrato de datos y análisis de factores clínicos asociados al reingreso hospitalario temprano en pacientes con diabetes.

## Objetivo: Análisis de Reingreso Hospitalario Temprano en Pacientes con Diabetes

Proyecto de análisis de datos clínicos basado en el repositorio *Diabetes 130-US hospitals for years 1999-2008* (UCI Machine Learning Repository). Implementa un [Contrato de Datos](Contrato_de_datos.md) para garantizar la calidad y trazabilidad del procesamiento antes del cálculo de indicadores clínicos.

## 📋 Brief del Proyecto

| Campo | Definición |
| :--- | :--- |
| **USUARIO** | Coordinación de calidad clínica y gestión hospitalaria |
| **FUENTE** | Archivos `diabetic_data.csv` e `IDS_mapping.csv` (UCI Machine Learning Repository, ID: 296) |
| **DESTINO** | Dataset analítico limpio (`.parquet` / `.csv`) con 17 variables clave y reporte de KPIs |
| **TRES KPI** | 1. Tasa de reingreso temprano (`<30 días`) sobre egresos vivos.<br>2. Estancia hospitalaria promedio (`time_in_hospital`) por tipo de reingreso.<br>3. Tasa de reingreso temprano según ajuste de medicación (`change`). |
| **FRECUENCIA** | Ejecución bajo demanda (*batch* histórico) |
| **CALIDAD MÍNIMA** | Sin `encounter_id` duplicados; valores `?` convertidos a `NaN`; exclusión de egresos por fallecimiento/hospicio (`discharge_disposition_id` 11, 13, 14, 19, 20, 21); estancia entre 1 y 14 días |
| **TERMINÓ BIEN** | El pipeline es repetible (mismo conteo en corridas sucesivas), entrega aproximadamente **99,340 filas válidas** tras aplicar las exclusiones (desde 101,766 crudas), y los **3 KPI** caen en rangos clínicos razonables: Rangos aproximados (1) tasa global de reingreso `<30 días` entre **8% y 15%**, (2) estancia promedio entre **3 y 6 días**, y (3) tasa de reingreso `<30 días` por grupo de `change` (`Ch` vs. `No`) entre **8% y 16%**. |
| **FUERA** | Modelos predictivos de Machine Learning, agrupación de códigos ICD-9 y análisis de costos |
