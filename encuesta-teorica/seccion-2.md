[Volver](README.md)
#### SECCION 2.

[Seccion anterior](seccion-1.md)

+ Conceptos de Data Lake

es un nuevo concepto. solo unas pocas literaturas academicas hablan.
la definen como "una nueva metodologia que permite un repositorio de datos masivos basados en el bajo costo de tecnologias que implementan la captura, refinamiento, archivo, y exploracion de datos brutos dentro de una organizacion"

la idea basica es simple, todos los datos emitidos por una organizacion seran almacenados en una estructura de datos llamada Data Lake o laguna de datos. Seran almacenados en su formato original. La complejidad del procesamiento y transformacion de carga de datos en el almacen de datos sera eliminada. el costo inicial puede ser reducido. una vez que los datos estan ubicados en la laguna, estaran disponibles para su analisis por cualquiera en la orgnizacion. 
- todos los datos se cargan desde sistemas fuente
- no se rechazan datos
- los datos se almacenan a nivel de hoja en un estado sin transformar o casi sin transformar

2.1 paisaje de datos actual. 

llendo al nucleo hay dos operaciones en el procesamiento de datos, transaccional y analitico. operaciones diarias como OLTP. procesos analiticos seran realizados por systenas tales como OLAP. Estos systemas operan en intervalos regulares definidos en modo batch o en lotes. 
Como los datawarehouse tardan tiempo en ser creados, en su lugar aparecen los datamarts que son mas chicos que los datawarehouse y tienden a almacenar datos de una parte de la organizacion. 
hay dos enfoque 
- el de Inmon: define un datawarehouse como orientado a un tema, integrado, variante en el tiempo (cargadis y posteriormente consultado con timestamp para su analisis), no volatil, por lo tanto, no hay recopilación actualizada de datos en apoyo de la toma de decisiones de gestión. Los datos son estables y no son cambiados o borrados una vez cargados. Su enfoque es de *arriba hacia abajo*. 
- el de Kimball: anima a la creacion del datamart primero. luego este es combinado  con otros para un datawarehouse organizacional, por lo tanto su enfoque es de *abajo hacia arriba*
Un *datawarehouse* funciona mejor con mapa de bits indexado, esta intensionalmente construido para responder consultas de datos historicos que no pueden ser manejados por sistemas para operaciones diarias. 

2.2. Data Lake (Implementacion Arquitectonica)

usa una arquitectura plana para almacenar datos en su estado bruto. cada entidad de dato esta asociado con un identificados unico y un conjunto de metadatos extendido, y los consumidores pueden usar esquemas especialmente diseñados para consultar datos relevantes, que resultaran en un pequeño conjunto de datos que puede ser analizado, para ayudar a responder una pregunta del consumidor. En esencia, *data lake* son datos respiratorios donde todos los datos en una empresa, es decir, datos estructurados, semiestructurados, no estructurados + datos binarios, se almacenan en conjunto independientemente del tipo, formato o estructura. la comprensión de la naturaleza de los datos se delega al cliente de datos en el momento de la recuperación de los datos (es decir, en el momento de la consulta). cuando se recuperan los datos, el usuario transformará esos datos de acuerdo con las partes de la empresa para adquirir información empresarial.

muchas implementaciones de data lake son originalmente basados en apache hadoop. HADOOP es una herramienta especialmente preparada para el procesamiento por lotes de carga de datos de grandes datos o big data. 
HADOOP tiene dos principales componentes: 

+ HDFS (hadoop distributed file system) 
+ motor de mapreduce

el sistema de HDFS maneja el punto único de falla y escalabilidad replicando múltiples copias de bloques de datos en diferentes nodos del clúster. todos los datos almacenados en estos bloques de datos seran procesados en el enfoque mapreduce. los datos seran recuperados como una lista de pares *llave-valor* es decir fase del mapa. las mismas claves de los datos se mezclarán, clasificarán y enumerarán en grupos para realizar las operaciones necesarias, es decir, reducir la fase. todos los datos producidos por una empresa se volcarán en el clúster de hadoop del lago de datos.


data lake para la carga en tiempo real, usa un framework de procesamiento de stream tal como apache spark o apache flink. 
data lake puede incluir una *semantica DB*, un modelo conceptual y agregar una capa de contexto para definir el significado de datos su interrelacion con otros datos.
la estrategia incluye almacenamiento de todo tipo de datos desde base de datos SQL y noSQL combinando los conceptos de OLTP con OLAP. base de datos SQL son usados para almacenar datos estructurados. NoSQL para almacenar semi estructurados y no estructurados. Todas las transacciones seran almacenadas en el lago de datos sin cambio en su formato.

2.3 sugerencia para mejorar el lago de datos

cada elemento tiene un identificador unico y etiquetas de metadatos. El orden de llegada de datos debe ser mantenido. Los datos y esquema de requerimiento no estan predefinidos de antemano hasta que se consulten los datos. Este es el esquema de solo lectura de data lake. 
Otros autores sugieren que la separacion del nivel del data lake puede ser manejado de dos formas. a) *conectado a la estructura de datos* y otra es b) *centrado en el tiempo de vida*. 

a) puede ser dividio en 3 capas: _dato en bruto_, _conjunto de datos diario aumentado_ e _información de terceros_, respectivamente

b) **basado en el tiempo de vida del dato**: *categorizado* menor a 6 meses, datos viejos pero activos, datos archivados que necesitan ser retenidos en medios más lentos y menos costosos. 
**El manejo de metadatos es un aspecto importante en data lake**. 
Como los esquemas no estan predefinidos, deben confiar en los metadatos durante el tiempo de consulta para el proceso de analisis. Los metadatos son agregados cuando los datos son almacenados. Un autor sugiere un framework para el manejo de metadatos para la alineación en la construcción del lago de datos utilizando openxML Data Lake con un prototipo. Las claves para crear un lago de datos exitoso se sugieren a continuación.

a) data lake deberia enfocarse en la principal prioridad de la estrategia corporativa.

b) aplicar una estrategia de integracion datos de solida

c) establecer una estrategia de incorporación moderna. La carga se puede hacer por lotes o alimentacion por goteo. prestar atencion a los procesos de inyeccion de metadatos sobre la marcha.

d) Adopte nuevas estrategias de gestión de datos mediante la adopción de la ingestión temprana y el procesamiento de ejecución adaptativa, como mapreduce, spark o flink, que permiten flexibilidad. derivar metadatos en el momento de la incorporación. crear un modelo analitico sobre la marcha. Estender el procesamiento de manejo de datos y estrategias a todos los datos. El analisis de datos deberia aplicarse en cualquier lugar de la canalización de datos. Modernizar la infraesrtctura de integracion de datos. 

e) aplicar algoritmos de aprendizaje automatico para generar valor comercial real. este flujo de trabajo deberia ser repetible. 

[Siguiente Seccion](seccion-3.md)

