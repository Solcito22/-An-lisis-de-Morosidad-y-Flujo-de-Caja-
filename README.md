# -Analisis-de-Morosidad-y-Flujo-de-Caja-
El propósito de este proyecto es auditar una cartera histórica de 2.466 facturas comerciales de la división financiera de IBM para identificar ineficiencias en el circuito de cobranzas. 
![Clientes con mayor promedio morosidad.xlsx](https://github.com/user-attachments/files/28360482/Clientes.con.mayor.promedio.morosidad.xlsx)


El propósito de este proyecto es auditar una cartera histórica de 2.466 facturas comerciales de la división financiera de IBM para identificar ineficiencias en el circuito de cobranzas.
El análisis busca responder a tres preguntas críticas de negocio:
¿Qué clientes concentran el mayor riesgo de impago y promedian más días de atraso (DaysLate)?
¿Cómo afectan las disputas comerciales (Disputed) al tiempo de recuperación del capital?
¿Cuánta liquidez de la compañía se encuentra actualmente retenida debido a estas fricciones operativas?

La creación del proyecto se divide en tres etapas fundamentales: ETL (Extracción y Limpieza), Modelado (Procesamiento) y Visualización.

1)-Extracción y Limpieza de Datos con Power Query
La materia prima del proyecto es un archivo crudo en formato .csv extraído de Kaggle. El proceso de preparación consistió en:
*Conexión e Importación: Se cargó el archivo utilizando el motor de Power Query en Excel para garantizar un proceso auditable y replicable.
*Normalización de Tipos de Datos: Se validó que las columnas cuantitativas (invoiceAmount) estuvieran en formato numérico decimal y las temporales o de conteo (DaysLate) como números enteros, evitando errores comunes de cálculo.
*Depuración del Modelo: Se eliminaron las columnas que no aportaban valor al análisis financiero (como paperlessBill), reduciendo el peso del archivo y optimizando el procesamiento.

![Reporte Ejecutivo de Morosidad](https://github.com/user-attachments/assets/ce43bd84-877e-41da-8ccc-1d3b406b41e7)


2)-Procesamiento y Modelado con Tablas Dinámicas
Una vez consolidados los datos limpios en la hoja de cálculo, se construyeron matrices de resumen para aislar las variables clave:
*Construcción del Ranking de Morosidad: Se agruparon los registros por el identificador único del cliente (customerID). Se transformó la métrica predeterminada de "Suma" a "Promedio" de días de atraso, ordenando los resultados de mayor a menor para exponer el Top de Clientes Críticos.
*Cruces de Variables de Negocio: Se integró la variable cuantitativa de montos (invoiceAmount) junto al promedio de atraso para medir la concentración de la deuda.

3)-Visualización Ejecutiva (Gráficos Dinámicos)
Para que los datos sean interpretables a primera vista:
Se transformaron las matrices numéricas en un Gráfico de Barras Dinámico, incorporando etiquetas de datos para identificar los desvíos financieros de manera inmediata, sin necesidad de leer la tabla completa.
![Visualización de los Datos](https://github.com/user-attachments/assets/ca4a687c-0edb-40f6-a054-57d0ddeb7b44)


Hallazgos Clave y Conclusiones del Análisis
Tras procesar las 2.466 facturas en el modelo dinámico, se detectaron los siguientes puntos críticos para la salud financiera de la empresa:

⚠️ Concentración del Riesgo en la Cartera de Clientes
El análisis de morosidad reveló que el comportamiento de pago no es uniforme. Al ordenar el ranking de clientes por el Promedio de DaysLate, se identificó un grupo crítico de cuentas que duplica la media de retraso general.
El impacto: Estas cuentas retrasan de manera sistemática la entrada de efectivo, obligando a la empresa a buscar financiamiento externo para cubrir los costos operativos de corto plazo.

El impacto: El dinero retenido en facturas disputadas representa un capital ocioso atrapado en el circuito administrativo. Cada día que una factura pasa en disputa es un día donde la liquidez de la empresa se reduce, afectando directamente el ratio de rotación de cuentas por cobrar.
