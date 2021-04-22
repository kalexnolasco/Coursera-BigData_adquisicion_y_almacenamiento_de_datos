# Ejercicio práctico Hadoop
* Abrimos un terminal de la máquina virtual de cloudera.

## Comandos básicos con archivos
> Versión de Hadoop
```console
[cloudera@quickstart ~]$ hadoop version
```
> Veamos si los servicios están activados y cuál es la calidad de los servicios.
* `Live datanodes`: Nos muestra cuantos datanodes tenemos activos. También podremos observarlos por navegador, abrir datos de calidad del servidor y podremos observar datos del nodo.
```console
[cloudera@quickstart ~]$ hdfs dfadmin -report
```
> Utilicemos HDFS y crear carpeta, copiar ficheros, borrar.
* Crear una carpeta(hadoop):
```console
[cloudera@quickstart ~]$ hdfs dfs -mkdir -p /user/hadoop
```
* Comprobemos que la carpeta existe, listando /user/hadoop
```console
[cloudera@quickstart ~]$ hdfs dfs -ls /user
```
* Copiamos un archivo de pruebas (creemos un archivo /tmp/vaca.txt de ejemplo)
```console
[cloudera@quickstart ~]$ hdfs dfs -put /tmp/vaca.txt /user/hadoop
```
* Listemos /user/hadoop para observar el archivo, que existe.
```console
[cloudera@quickstart ~]$ hdfs dfs -ls /user/hadoop
```
* Mostremos el contenido del fichero(con el comando cat) 
```console
[cloudera@quickstart ~]$ hdfs dfs -cat /user/hadoop/vaca.txt
```
* Eliminar el archivo(cuando ya no lo utilicemos más)
```console
[cloudera@quickstart ~]$ hdfs dfs -rm /user/hadoop/vaca.txt
```
* Si listamos /user/hadoop observamos que el archivo ya no existe
```console
[cloudera@quickstart ~]$ hdfs dfs -ls /user/hadoop
```

## Lanzar un típico trabajo de Hadoop

* llamamos a un ejemplo de Hadoop, llamamos al programa `teragen` con el comando 1000, el resultado estará en una carpeta llamada **terainput**.
* 1000 registros de tamaño 1000
```console
[cloudera@quickstart ~]$ hadoop jar /usr/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen 1000 /user/hadoop/terainput
```
* Con ello se han generado 1000 registros de 100 números aleatorios, ahora lo vamos a ordenar. `terasort`. La carpeta de salida **teraoutput** no debe de existes (no debe estar creada).
```console
[cloudera@quickstart ~]$ hadoop jar /usr/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort /user/hadoop/terainput /user/hadoop/teraoutput
```
* Con lo cual hemos ordenado 100000 bytes. Para comprobar que existen, la lista de datos de salida deben tener 100000 bytes.
```console
[cloudera@quickstart ~]$ hdfs dfs -ls /user/hadoop/teraoutput
```
* Finalmente, eliminamos los datos(utilizamos -rm -r para borrar la carpeta entera)
```console
[cloudera@quickstart ~]$ hdfs dfs -rm -r -skipTrash /user/hadoop/tera*
```