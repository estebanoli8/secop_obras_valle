** Análisis de Datos I - 252
Unidad 2
Taller 2. Comparte tu Análisis univariado
POR ESTEBAN OLIVEROS **

---

Descripción de la importancia de la columna: La ley 80 es clara sobre el manejo presupuestal y lo límites de las adciones presupuestales en un Contrato Público.
Por esto la variable valor_contrato en el dataset principal y la variable valor_total en el data set de facturación es la elegida como variable central de este análisis
puesto que se busca identificar las adiciones presupuestales injustficadas y los patrones que nos permitan posteriormente predecir dichos fenómenos asociados a la corrupción.
Se espera poder llevar esta tecnología a una implantación en el sector público en coordinación con interesados ciudadanos y privados para que haya mayor
transparencia y eficiencia en el gasto. La ejecución de contratos alrededor de las obras públicas en Colombia sistemáticamente presentan grandes daños
al herario público y a la dignidad de la ciudadanía (relevancia)


La información fue obtenida de los data sets de datos.gov.co (datos abiertos colombia) que están actualizados día a día de manera automatica desde secop.gov.co
(contratación pública colombia)


Análisis univariado en Python (2 puntos)
Se realizó un análisis univariado que permitió observar la distribución de manera gráfica la variable de interés que está dada en millones de pesos colombianos y es in INT de 64 bits.

=====================================
El tamaño del data set principal es de 19,766,430 (contratos) y filtrando solamente los del Valle del Cauca (especificidad)
se detectaron: 1,238,619 (contratos) y al de nuevo filtar solamente los contratos asociados a las obras públicas (sin interventoriás o apoyo a la gestión) se obtuvieron 
 21,079 (contratos). Estos registros fuerond esacrgados en .parquet y vienen acompañados de otras 21 variables descriptoras del contrato.
=====================================

El análisis estadístico básico se presenta a continuación relacionando también la segunda variable de interés el tiempo (de inicio y de finalización del contrato):

	valor_contrato	  fecha_inicio_ejecuci_n	fecha_fin_ejecuci_n
 
count	2.104300e+04	15851	16123
mean	1.401092e+09	2017-07-06 08:04:23	  2017-12-02 14:09:27
min	1.000000e+00	  2004-07-08 00:00:00	  2004-08-07 00:00:00
25%	1.735654e+07	  2014-05-19 12:00:00	  2014-09-11 00:00:00
50%	6.000000e+07	  2017-10-10 00:00:00	  2018-01-06 00:00:00
75%	3.199978e+08	  2020-11-27 00:00:00	  2021-05-19 12:00:00
max	3.480000e+12	  2025-08-26 00:00:00	  2038-08-04 00:00:00
std	2.593907e+10	  NaN	NaN


Posteriomente se realizó una división de los datos para un analisis más comparable diviendo los contatos en 4 rangos de valor_contrato:

'Bajo (0 - 1.000 millones)'
'Medio (1.000 - 10.000 millones)'
'Alto (10.000 - 100.000 millones)'
'Muy Alto (> 100.000 millones)'

Se realizó análisis del estado del proceso contractual
Se realizó inspección de texto del objeto contractual y categorización por sector (Cartera) onteniendo que los contratos se distribuyen así:

educación	2637
transporte	2305
vivienda	1666
servicios públicos	1637
salud	1404
mejoramiento	1251
deporte	1185
medio ambiente	812
tecnología	735
seguridad	582
cultura	511
otro	6318

Calculando el acumulado desde se encuntra que los sectores con mayor inversión histórica son:
1- Infraestructura y transporte
2- Deporte
3- Servicios públicos


Se realizó un análisis bivariado
Se realizó cuenta de contratos / modalidad de selección
Se realizó cuenta de contratos / tipo de contrato
Se realizó cuenta de contratos / municipio valle
Se realizó cuenta de contratos / nivel entidad ejecutora
Se realizó gráfica de valor de contratos / fecha firma contrato (nube de puntos)
Se realizó gráfica de valor de contratos / duración de contrato (se calculo con la fecha incio-fecha fin)

gráfica de valor de contratos / fecha firma contrato (nube de puntos)gráfica de valor de contratos / fecha firma contrato (nube de puntos)


Conclusiones del análisis 
La infromación de valor_contato es confiable, consistente y está disponible en el 100% de los casos.

No requiere un procesamiento ni imputaciones hasta el momento.

La mayor inversión acumulado coincide con el tamañlo de los mayores Municipios del valle.

Cali es el municipio con mayor inversión, sin embargo no hay indicios aún de que sea el municpio de mayor riesgo.

En cuanto a las fechas sí se encontraron datos faltantes, por no ingreso del usuario contratante. Se evidenciarion patrones
 gráficos en la relacion vlor contrao / tiempo ejecución

El data set es ciertamente sencillo sin embargo se prevee una dificultad para poder predecir 

Se exploró el data set facturación (casi 17 millones de registros) se unifició y se obtuvieron solamente 449 de los 21.079 registros (valle-obras)
por lo cual se evidencia que el dataset facturas no está completo para el caso de estudio.

Trabajo futuro
Se explorará si dentro de esos 449 resgitros hay presencia de sobre costos mayores al 30% y se analizará un posible modelo para intentar predecir 
la ocurrencia futura de dicho fenómeno.
