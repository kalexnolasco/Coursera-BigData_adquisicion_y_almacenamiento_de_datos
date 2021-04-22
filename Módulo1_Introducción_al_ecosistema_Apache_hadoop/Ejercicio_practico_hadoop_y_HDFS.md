# Ejercicio práctico Hadoop y HDFS


## Pregunta 1
Las primeras veces que se utiliza el ecosistema Hadoop es necesario comprobar que tanto los servicios relacionados con el repositorio de datos como los relacionados con la ejecución de trabajos funcionan correctamente.

En este ejercicio vamos a realizar una pequeña comprobación del buen funcionamiento de varios servicios relacionados con Hadoop

* Comprobar la salud de HDFS. ¿Está funcionando bien?
* Ciclo de creacion, lectura y eliminación de un archivo en HDFS. 
* Lanzar un trabajo sencillo de prueba
* Comprobar los resultados obtenidos en HDFS

Primero, debes descargar un archivo de datos de prueba "texto.txt" para resolver una serie de cuestiones. Para ello:

* Entra en la máquina virtual MV_Cloudera,
* Abre el navegador web, y,
* Descarga los datos desde esta dirección: http://www.gutenberg.org/cache/epub/2000/pg2000.txt y cámbiale el nombre a texto.txt

A continuación, realiza los siguientes pasos:
* Comprueba que HDFS y Hadoop funcionan correctamente en la máquina virtual 
* Descarga el fichero de datos "texto.txt" a una carpeta de usuario en la maquina virtual
* Crea una carpeta de datos de entrada en HDFS
* Copia el archivo "texto.txt" a la carpeta de datos de entrada en HDFS
* Utiliza la biblioteca de ejemplos de Hadoop para contar las palabras en el archivo texto.txt usando una llamada parecida a:
```console
hadoop jar /usr/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar wordcount <carpeta HDFS de entrada> <nueva carpeta HDFS de salida>
```

Es importante asegurarse de que la carpeta de entrada contiene nuestro achivo de texto y que no existe la carpeta de salida en HDFS.

Resuelve la siguiente pregunta completando el comando hadoop del punto 5:

Comprueba el resultado en la carpeta de salida en HDFS. ¿Cuántas veces aparece la palabra "vaca" en el archivo de texto part-r-00000?
* Respuesta->5