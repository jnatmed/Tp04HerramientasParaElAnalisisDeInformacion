[Volver](README.md)
#### SECCION 3.

[Anterior](seccion-2.md)

3.1. desviacion del data lake del datawarehouse. 

datawarehouse debe cargar los datos (write/ escribirlos) luego se consultan, por eso es esquema de escritura. 
data lake cambia el orden del prosamiento de los datos. No hay esquema predefinido. Cuando los datos son extraidos de la fuente a la laguna de datos, el requerimiento de metadata es especialmente agregado en el dato. de esta forma data lake puede manejar  tanto escritura pesada como lectura pesada. Los datos no son transformados hasta que son requeridos. Momento en el cual son transformados de acuerdo a una forma usando el metadato agregado al comienzo. De esta forma el gasto en el preprocesamiento puede ser evitado en data lake. 

3.2 comparacion

+ datos: almacena la mayor cantidad de datos en gran porcentaje a diferencia de DW llega al 20% aprox

+ procesamiento: DW esta limitado a su naturaleza resumida y estructurada.

+ cost: bajo cost para DL

+ agilidad: mas agil DL

+ security: DW por antiguedad y robuztes es mas seguro.

+ users: los analistas y cientificos prefieren mas DW y no tanto al DL 

[siguiente seccion](seccion-4.md)

