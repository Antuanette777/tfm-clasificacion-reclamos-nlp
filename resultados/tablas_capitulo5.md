### Tabla 7. Distribución de clases y longitud

| label            |     n |   palabras_media |   palabras_mediana |   porcentaje |
|:-----------------|------:|-----------------:|-------------------:|-------------:|
| credit_reporting | 34955 |            209.4 |              141   |         58.3 |
| debt_collection  |  7478 |            194.8 |              124   |         12.5 |
| credit_card      |  5098 |            216.2 |              162   |          8.5 |
| bank_account     |  4679 |            218.3 |              155   |          7.8 |
| mortgage         |  2414 |            296.9 |              213.5 |          4   |
| money_transfer   |  2337 |            186.1 |              118   |          3.9 |
| consumer_loan    |  2005 |            225.7 |              162   |          3.3 |
| student_loan     |  1034 |            224.6 |              179   |          1.7 |

### Tabla 8. Resultados globales

| Modelo       | Exactitud       | Precisión macro   | Exhaustividad macro   | F1 macro        | IC 95 % F1 macro (semilla 42)   | F1 ponderado    |
|:-------------|:----------------|:------------------|:----------------------|:----------------|:--------------------------------|:----------------|
| Naive Bayes  | 0.7877 ± 0.0042 | 0.6720 ± 0.0049   | 0.7559 ± 0.0081       | 0.7009 ± 0.0044 | [0.6907; 0.7143]                | 0.7950 ± 0.0040 |
| SVM lineal   | 0.8495 ± 0.0043 | 0.7649 ± 0.0064   | 0.7988 ± 0.0134       | 0.7804 ± 0.0073 | [0.7775; 0.7995]                | 0.8509 ± 0.0046 |
| RoBERTa-base | 0.8287 ± 0.0061 | 0.7316 ± 0.0025   | 0.8238 ± 0.0025       | 0.7702 ± 0.0017 | [0.7577; 0.7792]                | 0.8354 ± 0.0052 |

### Tabla 9. F1 por clase

| clase            |   Naive Bayes |   SVM lineal |   RoBERTa-base |   n_prueba (semilla 42) |
|:-----------------|--------------:|-------------:|---------------:|------------------------:|
| bank_account     |        0.7466 |       0.8033 |         0.8088 |                     936 |
| consumer_loan    |        0.5355 |       0.6457 |         0.6205 |                     401 |
| credit_card      |        0.6541 |       0.762  |         0.7491 |                    1019 |
| credit_reporting |        0.8789 |       0.9161 |         0.8963 |                    6992 |
| debt_collection  |        0.6639 |       0.732  |         0.709  |                    1496 |
| money_transfer   |        0.6488 |       0.7352 |         0.7622 |                     467 |
| mortgage         |        0.773  |       0.8671 |         0.8622 |                     483 |
| student_loan     |        0.7063 |       0.7821 |         0.7536 |                     207 |

### Tabla 10. Coste computacional

| Modelo       | Parámetros   |   Entrenamiento (s) |   Inferencia CPU (ms/reclamo) | Inferencia GPU (ms/reclamo)   | Memoria GPU pico (GB)   |
|:-------------|:-------------|--------------------:|------------------------------:|:------------------------------|:------------------------|
| Naive Bayes  | 800,000      |                  11 |                          0.16 | —                             | —                       |
| SVM lineal   | 800,000      |                  14 |                          0.16 | —                             | —                       |
| RoBERTa-base | 124,651,784  |                1653 |                         98.01 | 2.52                          | 5.1                     |

### Tabla 11. McNemar con Holm

|   semilla | comparación                 |   p (McNemar) |   p ajustado (Holm) | significativo (α=0,05)   |
|----------:|:----------------------------|--------------:|--------------------:|:-------------------------|
|        42 | Naive Bayes vs SVM lineal   |   6.93893e-95 |         2.08168e-94 | True                     |
|        42 | Naive Bayes vs RoBERTa-base |   1.43629e-19 |         1.43629e-19 | True                     |
|        42 | SVM lineal vs RoBERTa-base  |   1.49213e-23 |         2.98426e-23 | True                     |
|        43 | Naive Bayes vs SVM lineal   |   7.12645e-77 |         2.13793e-76 | True                     |
|        43 | Naive Bayes vs RoBERTa-base |   9.88807e-43 |         1.97761e-42 | True                     |
|        43 | SVM lineal vs RoBERTa-base  |   0.000271306 |         0.000271306 | True                     |
|        44 | Naive Bayes vs SVM lineal   |   5.28072e-95 |         1.58422e-94 | True                     |
|        44 | Naive Bayes vs RoBERTa-base |   1.49525e-33 |         2.9905e-33  | True                     |
|        44 | SVM lineal vs RoBERTa-base  |   3.1742e-11  |         3.1742e-11  | True                     |

### Tabla 12. F1 macro por longitud

| Tramo (palabras)   |   Naive Bayes |   SVM lineal |   RoBERTa-base |   n (semilla 42) |
|:-------------------|--------------:|-------------:|---------------:|-----------------:|
| ≤100               |        0.6425 |       0.7262 |         0.7002 |             4090 |
| 101–250            |        0.7224 |       0.7979 |         0.8012 |             4741 |
| 251–500            |        0.7251 |       0.8041 |         0.7929 |             2301 |
| >500               |        0.6845 |       0.7884 |         0.7815 |              869 |

### Tabla 13. Partición temporal

| Modelo       |   F1 macro (temporal) |   Exactitud (temporal) |   F1 macro (aleatoria, semilla 42) |
|:-------------|----------------------:|-----------------------:|-----------------------------------:|
| Naive Bayes  |                0.7018 |                 0.7993 |                             0.7032 |
| SVM lineal   |                0.7665 |                 0.8429 |                             0.7886 |
| RoBERTa-base |                0.7744 |                 0.8357 |                             0.7688 |

