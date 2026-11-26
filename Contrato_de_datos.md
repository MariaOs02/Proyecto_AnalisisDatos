| columna | tipo | ¿puede faltar? | ejemplo | descripción |
| :--- | :--- | :---: | :--- | :--- |
| `encounter_id` | entero | no | `2278392` | Identificador único de cada hospitalización o encuentro clínico. |
| `patient_nbr` | entero | no | `8222157` | Identificador único del paciente (permite rastrear reingresos múltiples). |
| `age` | texto | no | `[70-80)` | Rango de edad del paciente agrupado en intervalos de 10 años. |
| `gender` | texto | no | `Female` | Sexo biológico (`Male` o `Female`). Registros con `Unknown/Invalid` se excluyen en limpieza. |
| `race` | texto | sí | `Caucasian` | Grupo racial o étnico reportado (`?` se estandariza como nulo). |
| `admission_type_id` | entero | no | `1` | Código numérico del tipo de ingreso (1: Emergencia, 2: Urgencia, 3: Electivo, etc.). |
| `discharge_disposition_id` | entero | no | `1` | Código del destino al alta (1: Casa; excluye códigos de fallecimiento/hospicio). |
| `time_in_hospital` | entero | no | `4` | Días totales transcurridos entre la admisión y el alta (rango: 1 a 14). |
| `num_lab_procedures` | entero | no | `41` | Cantidad de pruebas de laboratorio realizadas durante la estancia. |
| `num_procedures` | entero | no | `0` | Cantidad de procedimientos médicos (no de laboratorio) realizados. |
| `num_medications` | entero | no | `12` | Número de medicamentos distintos administrados durante el encuentro. |
| `number_diagnoses` | entero | no | `9` | Número total de diagnósticos registrados en el sistema para ese ingreso. |
| `A1Cresult` | texto | sí | `>8` | Resultado de HbA1c (`Norm`, `>7`, `>8`). Cuando no se midió (`"None"`) se convierte a nulo (`NaN`) en limpieza. |
| `insulin` | texto | no | `Steady` | Estado de prescripción de insulina (`No`, `Down`, `Steady`, `Up`). |
| `change` | texto | no | `Ch` | Indica si hubo cambio o ajuste en la medicación para la diabetes (`Ch` / `No`). |
| `diabetesMed` | texto | no | `Yes` | Indica si el paciente tiene algún medicamento antidiabético prescrito (`Yes` / `No`). |
| `readmitted` | texto | no | `<30` | Estado de reingreso hospitalario (`<30` días, `>30` días, o `NO` reingresó). |
