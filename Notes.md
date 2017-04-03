
### RDD : transformations & actions

Les transformations retournent un ensemble de données (RDD, dataframe)
Exemple : map, filter, flatmap, groupBy

Les actions retournent une valeur, un résultat
Exemple : reduce, fold, aggregate, distinct, collect, count, take, foreach

Les transformations sont lazy et les actions eager. C'est de cette façon que Spark optimise la gestion des flux réseau.
Par défaut, les RDD sont recalculés à chaque fois qu'on applique une action dessus.

Quand on persiste un RDD en mémoire, s'il n'y a pas assez de RAM dispo, par défaut le reste du RDD est recalculé à chaque action.
Pour éviter ça il faut préciser que l'on veut persister sur disque les données.


### Clustering des programmes

Un job Spark est composé d'un Driver programme sur le master et d'éxecutor sur les workers node.
Le spark context est défini au niveau du driver. <br>
Le driver et les worker communiquent au travers de Yarn.

### Pairs RDD

Les RDD clés/valeurs sont traités de manière particulière par Spark et ont des méthodes supplémentaires :
Transformations : 
  * groupByKey (retounr un RDD (clé, liste de valeur)
  * reduceByKey (retourne un RDD (clé, valeur))
  * join
  * keys
  * mapValues
  * leftOuterJoin / rightOuterJoin
  
Actions : 
  * countByKey
  
Pour créer un pairRDD, on peut utiliser un RDD et utiliser la fonction map dessus.

