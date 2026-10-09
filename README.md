# Análisis de eficiencia operativa y detección de operadores ineficaces

Proyecto de análisis de datos enfocado en evaluar el desempeño operativo de un servicio de telefonía virtual, identificar posibles problemas en la gestión de llamadas y detectar operadores que requieren seguimiento mediante indicadores de rendimiento.

## Objetivo

Analizar los registros de llamadas de un servicio de telefonía virtual para:

- Estudiar el comportamiento general del tráfico de llamadas.
- Identificar patrones de llamadas entrantes, salientes y perdidas.
- Evaluar los tiempos de espera y los volúmenes de actividad.
- Construir indicadores de desempeño (KPIs) por operador.
- Identificar operadores con posibles señales de ineficiencia operativa.
- Proponer estrategias para mejorar la atención y la gestión de llamadas.

## Herramientas utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Técnicas aplicadas

- Limpieza y preparación de datos.
- Análisis exploratorio de datos (EDA).
- Tratamiento de valores ausentes y registros duplicados.
- Análisis de series temporales de actividad.
- Construcción de indicadores operativos (KPIs).
- Agrupación y segmentación de operadores.
- Análisis de percentiles y umbrales de desempeño.
- Análisis de sensibilidad.
- Visualización e interpretación de resultados.

## Proceso de análisis

El proyecto se desarrolló en las siguientes etapas:

1. **Importación y exploración:** revisión de los datasets de llamadas y clientes.
2. **Preparación de datos:** conversión de fechas, identificación de valores ausentes y eliminación de duplicados exactos.
3. **Análisis exploratorio:** estudio de llamadas entrantes, salientes, internas, externas y perdidas.
4. **Visualización:** representación de distribuciones, duraciones y evolución temporal del tráfico.
5. **Construcción de KPIs:** cálculo de tasas de llamadas perdidas, tiempos promedio de espera y volumen de actividad por operador.
6. **Segmentación:** clasificación de operadores mediante criterios exploratorios basados en percentiles.
7. **Análisis de sensibilidad:** evaluación de la estabilidad de la clasificación con diferentes mínimos de actividad.
8. **Conclusiones:** identificación de oportunidades de mejora y formulación de recomendaciones operativas.

## Principales resultados

Después de la preparación de datos se obtuvieron los siguientes resultados:

| Indicador | Resultado |
|---|---:|
| Registros originales | 53,902 |
| Registros después de limpieza | 49,002 |
| Registros con operador asignado | 41,546 |
| Registros sin operador asignado | 7,456 |
| Operadores identificados | 1,092 |
| Operadores evaluables | 356 |
| Operadores que requieren atención | 62 |
| Operadores dentro de parámetros | 294 |

### Indicadores de desempeño

Se estableció un mínimo exploratorio de **20 llamadas entrantes por operador** para evaluar su desempeño.

Posteriormente, se utilizaron los percentiles 90 para identificar valores relativamente elevados en dos indicadores:

- Tasa de llamadas entrantes perdidas: **3.70%**.
- Tiempo promedio de espera por llamada entrante: **28.82 segundos**.

Estos umbrales representan criterios exploratorios derivados de los datos y no estándares universales de desempeño.

## Segmentación de operadores

Los operadores se clasificaron de acuerdo con la información disponible y las alertas identificadas:

| Segmento | Operadores |
|---|---:|
| Requiere atención | 62 |
| Dentro de parámetros | 294 |
| Muestra insuficiente | 398 |
| Sin llamadas entrantes | 338 |
| **Total** | **1,092** |

Entre los **356 operadores evaluables**, el **17.42%** presentó al menos una alerta de desempeño, relacionada con una tasa relativamente elevada de llamadas perdidas o tiempos de espera.

Los operadores con una muestra insuficiente o sin llamadas entrantes no se consideran automáticamente eficientes o ineficientes, debido a que no existe información suficiente para realizar una evaluación comparable.

## Hallazgo relevante: llamadas sin operador asignado

Uno de los principales hallazgos fue que aproximadamente el **99.1% de las llamadas entrantes marcadas como perdidas no tenía un operador identificado**.

Esta situación limita la posibilidad de atribuir las llamadas perdidas exclusivamente al desempeño individual de los operadores.

Por ello, el análisis destaca la importancia de investigar también los procesos de asignación, enrutamiento y registro de llamadas.

## Análisis de sensibilidad

Se evaluaron tres mínimos de actividad para comprobar cómo cambia la clasificación de operadores:

| Mínimo de llamadas | Operadores evaluables | Operadores con alertas | Porcentaje |
|---|---:|---:|---:|
| 10 | 446 | 80 | 17.94% |
| 20 | 356 | 62 | 17.42% |
| 30 | 296 | 53 | 17.91% |

Aunque el número de operadores evaluables cambia, la proporción general de alertas se mantiene cercana al 18% al recalcular los umbrales para cada escenario.

Este resultado muestra cierta estabilidad descriptiva de la clasificación, aunque no garantiza que siempre se identifique a los mismos operadores.

## Recomendaciones de negocio

**1. Mejorar los procesos de asignación de llamadas.**

Investigar las causas por las cuales numerosas llamadas entrantes perdidas no cuentan con un operador identificado.

**2. Implementar seguimiento a operadores con alertas.**

Evaluar los casos identificados considerando su carga de trabajo, horarios y responsabilidades antes de establecer medidas correctivas.

**3. Monitorear indicadores operativos periódicamente.**

Crear reportes de seguimiento sobre las tasas de llamadas perdidas, tiempos promedio de espera y volúmenes de actividad.

**4. Establecer criterios diferenciados de desempeño.**

Adaptar las evaluaciones según las funciones de los operadores, distinguiendo entre actividades de atención entrante y llamadas salientes.

## Limitaciones del análisis

- Los umbrales empleados son exploratorios y dependen de la distribución de los datos.
- No se dispone de información detallada sobre los objetivos, turnos y responsabilidades individuales de los operadores.
- Una parte importante de las llamadas perdidas no tiene operador identificado.
- La eliminación de duplicados exactos supone que estos representan registros repetidos; esta condición debería validarse con información del sistema de origen.
- La identificación de alertas no demuestra por sí sola que un operador tenga un desempeño deficiente.

## Conclusión

El análisis permitió identificar posibles problemas tanto en el desempeño individual de ciertos operadores como en los procesos generales de gestión de llamadas.

Los resultados muestran que una estrategia de mejora debería combinar el seguimiento mediante KPIs con la revisión de los procedimientos de asignación y enrutamiento.

La metodología proporciona una base para priorizar investigaciones operativas y apoyar decisiones orientadas a mejorar la calidad del servicio.

## Archivos

- `proyecto_sprint_15.ipynb`: notebook principal con el análisis completo.
- `telecom_dataset_new.csv`: registros de llamadas utilizados para el análisis.
- `telecom_clients.csv`: información general de los clientes.
- `requirements.txt`: dependencias necesarias para ejecutar el proyecto.

## Instalación de dependencias

Instalar las librerías desde la terminal:

`pip install -r requirements.txt`

## Ejecución

1. Descargar o clonar el repositorio.
2. Instalar las dependencias.
3. Abrir `proyecto_sprint_15.ipynb` en Jupyter Notebook o Visual Studio Code.
4. Verificar que los archivos CSV se encuentren en la misma carpeta que el notebook.
5. Ejecutar todas las celdas en orden.