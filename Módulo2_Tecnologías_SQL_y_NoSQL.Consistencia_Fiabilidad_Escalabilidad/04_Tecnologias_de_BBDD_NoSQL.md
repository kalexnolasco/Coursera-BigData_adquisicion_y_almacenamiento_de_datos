# Tecnologías BBDD NoSQL

## Origen, necesidad

* Recordamos las `4Vs`
    * Volumen: Enorme cantidad de datos
    * Velocidad: Generación y movimiento a gran velocidad.
    * Variedad: Distintos tipos.
    * Veracidad: El grado de confianza en los datos.

* Necesidad de implementación sistemas NoSQL a gran(`enorme`) escala.
![](../images/22_NoSQL.png)
  
## Situación actual. Tipos de aproximación: key-value, wide column store, document store
![](../images/23_NoSQL.png)
* `key-value store`: Registros clave-valor, donde cada clave tiene asociado un valor, y este valor no tiene nada que ver con el resto de valores, ni seguir una estructura definida.
* `wide column store`: Los registros están indexados mediante índices. Las familias de columnas se dividen en sub-columnas, y cada una de estas tiene su clave de columna y su respectivo valor.
* `document store`: Por cada registro tenemos un índice y el valor asociado al índice es lo que se conoce como documento. La estructura interna no debe ser(obligatoriamente) común entre los diversos documentos.

## Introducción a tecnologías actuales: HBASE, Cassandra, MongoDB
### HBASE
* 2007, Apache
* Integración Hadoop, HDFS
* Wde column store
* Escrita en Java, desarrollo a partir de BigTable
* Sistema CP (Consistencia de datos y tolerancia a la partición)
### Cassandra
* 2007 Facebook - 2009 Apache
* Alta escalabilidad y disponibilidad
* Wide column store
* Escrita en Java, muy buena integración con Hadoop y otras plataformas Big Data.
* Sistema AP(disponibilidad y tolerancia a particiones)
### MongoDB
* 2007 !0gen Inc. (MongoDB Inc.)
* Simplicidad en el desarrollo
* Document Store
* Escrita en C++, muy buena integración enm distintos casos de usos.
* Sistema CP (Consistencia de datos y tolerancia a la partición)
## Exploración tecnologías: modelos de datos y arquitectura

### HBASE
![Modelo de datos](../images/24_NoSQL.png)

![Modelo de datos](../images/25_NoSQL.png)
* ¡Vamos a imaginar que almacenamos todos los campos de todas las familias de columnas, la arquitectura de HBase lo que hace es un particionamiento horizontal de los datos, de modo que cada fragmento viene identificado por una clave de fila inicial y una clave de fila final.
![Modelo de datos](../images/26_NoSQL.png)
* Una vez tenemos los datos particionados los datos, estos se distribuyen en diferentes regiones (distintas ubicaciones lógicas).
* Cada una de las regiones está gobernada por un servidor de región, y cada conjunto de regiones que están gobernadas por un servidor de región, pueden estar distribuidas geográficamente.
* En este esquema, hay dos componentes esenciales:
  * HMASTER: Demonio principal del sistema.
  * ZOOKEEPER: Elemento de coordinación distribuida esencial para el funcionamiento de toda la arquitectura.
![Modelo de datos](../images/27_NoSQL.png)
    
### Cassandra
![Modelo de datos](../images/28_NoSQL.png)
![Modelo de datos](../images/29_NoSQL.png)
* Protocolo Gossip: cada nodo tiene comunicación constante y frecuente nodo a nodo. Se intercambian información de estado, tamaño disponible,etc.
![Modelo de datos](../images/30_NoSQL.png)
  
> Esta arquitectura es escalable y se puede repetir en diferentes ubiucaciones. P.e. Dos DataCenter agrupados en un cluster.
![Modelo de datos](../images/31_NoSQL.png)

### MongoDB
* Orientada a documentos: Los datos son más bastos que los de paradigma  en columnas 
* Los documentos se codifican mediante un tipo de datos llamado `BSON` (como json pero binario)
* Representación(Como objeto tipo JSON): 
```javascript
var mydoc = {
    _id: ObjectID("edfjsdlkj32423lk"),
    name:{ first:"Alan", last:"Turing"},
    birth: new Date('Jun 23, 1912'),
    death: new Date('Jun 07, 1954'),
    contribs: ["Turing machine", "Turing test", "Turingery"],
  views: NumberLong(1250000)
}
```
* Unidad Básica de datos: Documento (`BSON`)
  * Los documentos a su vez se pueden apilar en `Coleciones`. **Las bases de datos contienen colecciones de documentos, y estas colecciones podrán ser sub-divididas en chunks**
  ![Modelo de datos](../images/32_NoSQL.png)

> Relaciones que se establece entre los diversos documentos. 
  * MongoDB proporciona una manera de relacionar los datos
      * `mediante enlaces`(utilizando los propios identificadores internos que se generan para cada documento)
      * con `documentos incrustados`(incrustar un sub-documento como valor de un determinado campo).
        ![Modelo de datos](../images/33_NoSQL.png)
        
> Persistencia de datos
![Modelo de datos](../images/34_NoSQL.png)
![Modelo de datos](../images/35_NoSQL.png)
![Modelo de datos](../images/36_NoSQL.png)
  
> Sharding
![Modelo de datos](../images/37_NoSQL.png)
![Modelo de datos](../images/38_NoSQL.png)
![Modelo de datos](../images/39_NoSQL.png)
![Modelo de datos](../images/40_NoSQL.png)
![Modelo de datos](../images/41_NoSQL.png)


## Consideraciones: ¿Cuál escoger?
![Modelo de datos](../images/42_NoSQL.png)

