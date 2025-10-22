21/10/2025
<strong>Tags</strong>: 
# Fundamentos de Bases de datos
# Ideas principales

En estos días he anotado las siguientes cosas que considero importantes: 

Es importante tener un buen disenio de la base de datos, ya que esto conlleva a una integridad referencial, optimizacion de espacio, eficiencia en las consultas y una escalabilidad del sistema.

El disenio tiene 3 etapas: 
- Disenio Conceptual:  Modelo entidad-relación
	- Abstracción del dominio del problema 
	- Independiente del SGBD
- Disenio lógico: Mapeo a modelo relacional
	- Definición de esquemas
	- Normalizacion
- Disenio fisico: Implementacion en SGBD
	- Optimizacion para rendimiento
	- Setencias DDL

### Sentencias DDL 
Las sentencias DDL (Data Definition Language) en SQL son un conjunto de comandos usados para definir, modificar y gestionar la estructura de la base de datos, se usan para crear modificar o eliminar objetos de una base de datos, como tablas, indices, vistas, entre otros. 

### Modelo Entidad Relación
Elementos:
- Entidades: Objetos del mundo real con existencia independiente.
- Atributos: Propiedades que describen entidades, pueden ser simples osea no divisibles, compuestos osea subdivisibles, multivaluados osea múltiples valores y derivados osea calculados por ejemplo la edad desde fecha_nacimiento.
- Relaciones: Asociaciones entre entidades , pueden haber relaciones binarias entre dos entidades, ternarias entre tres entidades y relaciones recursivas cuando una entidad esta relacionada consigo misma
- Cardinalidad: Grado de participación en relaciones, uno a uno, uno a muchos, muchos a muchos.

### Categorías de entidades
- Identidad fuerte: Se puede definir únicamente por sus propios atributos, en cambio, una entidad débil no. En general las entidades fuertes existen por si mismo en el modelo de datos y tiene una clave primaria propia. (Tiene entidad propia)
- Una entidad asociativa es aquella que relaciona entidades o elementos dentro de un conjunto de entidades.
- Las entidades débiles dependen de una fuerte para existir, no tienen claves primarias sino que incluye la clave de otra entidad.
### Claves de entidad
Una clave o llave es un atributo (o conjunto de atributos) que identifica de manera única una fila dentro de una table.
- Superclave: Conjunto de atributos que juntos definen una entidad en un conjunto de entidades.
- Clave conocida: Es una superclave mínima, es decir, contiene el menor numero posible de atributos para seguir siendo una superclave. Identifica de forma única una fila.
- Clave primaria: Es una clave candidata seleccionada por el diseniador de la base de datos para identificar únicamente el conjunto de entidades.
- Clave extranjera: Identifica la relación entre entidades atributo que referencia a otra entidad.
- Clave alternativa: Clave candidata no elegida como primaria como cédula si Id es la clave primaria. 
### Atributos
- Valores Múltiples: Se denota mas de un valor del atributo, como varios números para una persona
- Valor único: Contienen solo un valor de atributo. 

Los tipos se pueden combinar. Pueden haber atributos de valor único simples y atributos de valores múltiples compuestos. 

### Etc
En las relaciones de muchos a muchos, podemos crear una tercer tabla (Tabla de unión o asociativa) esta tabla contiene las claves externas que hacen referencia a las claves primarias de las tablas implicadas.

Diferencias entre Entidad Unión y Entidades Asociativas:

- Entidades Unión: Actúan como intermediarias entre dos tablas de la relación. Mantiene los atributos específicos y contribuye a la asociación n:m. Ademas de permitir almacenar detalles adicionales dentro de ella.
- Entidades Asociativas: Conectan directamente las dos tablas implicadas en la relación n:m. Contienen  atributos específicos de las relaciones y establecen conexión entre las tablas. Proporciona una representación directa de la relación. Capturando información necesaria dentro de la entidad asociativa. 





# Resumen







# Estudiar


