Golang course III

Como prepararse para una entrevista (en Golang)

0_ Siempre aprender algo en una entrevista

1_ El mas importante, conocer bien tu CV

2_ Ser claro para hablar, preferentemente, tener algo armado para decir cuando
pregunten por nuestra experiencia

3_ Para la parte practica:
 	a_ Si es online coding, ejercitarse en algoritmia como Hackerrank, codility, project euler.
 	b_ Conocer los conceptos de BigO, complejidad temporal, complejidad espacial BigO(1) - worst case scenario & best case
 	c_ SIEMPRE, empezar por un algoritmo de fuerza bruta, para despues buscar una mejor opcion, NUNCA no escribir nada
 	d_ Conocer los distintos tipos de algoritmos, brute force, greedy, etc y los algorimos de busqueda mas comunes
 	como bubble sort, merge sort, quick sort... Hay infinidad de material en internet.

 	e_ Si es un challenge, recuerden los siguientes items:
 		* Leer perfectamente el enunciado, cualquier error ahi es mas grave que un bug en el codigo
 		* No hacer cosas de menos pero tambien no hacer muchas cosas de mas que no esten solicitadas
 		* Escribir SIEMPRE test unitarios (si pueden test de integracion o de comportamiento o de performance (jmeter) tambien)
 		* Escribir SIEMPRE comentarios
 		* Escribir SIEMPRE un readme donde diga como se compila, como se ejecuta, si hacen falta otros softwares (bases de datos,
 		cache, libreria o lo que fuese) PS: Docker es bueno
 		* Dejar ejemplos, troubleshooting
 		* Algo que suma MUCHO, es, en caso de no tener por ejemplo, una base de datos que el enunciado diga que hay que usar, 
 		explicar porque se eligio esa, asi tambien con las librerias y basicamente todo lo que requiera explicacion.

 4_ Preguntas sobre Golang

 - Punteros y operador '&'
 - Slices, arrays y maps (cuando usar cada uno y sus diferencias)
 - operadores make, new, close y range
 - Concurrencia:
 	Goroutines, que son y como se crean. Saber minimamente como trabajan internamente
 	Channels - operador select
 	waitgroup, mutex (paquete sync)
 - Tools de go como ser: go get, build, run, test, fmt, vet ...
 - go modules
 - paquetes comunes como errors, strings, fmt, json, http
 - librerias para bases de datos SQL y noSQL
 - Manejo de errores
 - Interfaces
 - Closures
 - defer, panic y recover
 - Makefile
 - Dockerfile (logicamente si saben usar docker, sino no es imprescindible)
