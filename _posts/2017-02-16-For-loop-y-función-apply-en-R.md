En este artículo vamos a ver de manera sencilla como usar for loops y la función apply en R. El uso de una u otra dependerá sobre todo de nuestras necesidades de velocidad, de manera que la función apply es más rápida y sencilla de usar. Pero siempre es conveniente conocer todas las alternativas.

Empezamos con un for loop muy básico:

```
for(i in 1:100){
print("Hello world!")
print(i*i)
}
```

En este ejemplo, todo lo que se encuentre dentro de las llaves {} se repetirá 100 veces, porque el for loop toma a la i como el contador de loops. Lo que hace R es crear un vector i con 1:100 en él.

Otro ejemplo:

```
for (age in c(10,11,12,13,14,15)){
print(paste("The age is", age))
}
```

```
[1] "The age is 10"
[1] "The age is 11"
[1] "The age is 12"
[1] "The age is 13"
[1] "The age is 14"
[1] "The age is 15"
```

Y un último ejemplo para confirmar que hemos entendido como funciona un loop:

```
x <- c(1,2,3,4,5,6)
count <- 0
for (i in x) {
if(i %% 2 == 0)  count = count+1
}
print(count)
```

Este loop itera 6 veces sobre el vector c. Para cada iteración de i, R toma el valor del vector x. R cuenta el número de números pares que hay en el vector x, por tanto la respuesta es 3.

Como decíamos al principio, en la mayoría de los casos será más apropiado utilizar la función apply que escribir un for loop.

Apply es una familia de funciones que tienen diferentes usos, y esta familia la componen las siguientes funciones: apply, lapply, sapply, vapply, mapply, rapply y tapply.

Apply es el cabeza de esta familia, opera sobre matrices de la siguiente forma: apply(X, MARGIN, FUN, ...), donde:

* X es la matriz sobre la que opera.
* MARGIN es un vector donde se indica el subíndice sobre el cual la función se aplicará. 1 indicaría la fila y 2 la columna, mientras que c(1,2) indicaría fila y columna.
* FUN es la función a aplicar. En caso de funciones del tipo +, %+%, etc., el nombre de la función deberá ir entre comillas.
* ... argumentos opcionales para la función.

Vamos a ver un ejemplo, usando los datos del dataset cars, incluido en R base. Por ejemplo, vamos a ver como obtener la suma de la variable speed, así como la media:

```
apply(cars,2,sum)
apply(cars,2, mean)
```
```
> apply(cars,2,sum)
speed  dist 
  770  2149 
> apply(cars,2, mean)
speed  dist 
15.40 42.98 
```

[Fuente 1](http://crained.com/787/how-to-program-a-for-loop-in-r/) / [Fuente 2](http://crained.com/796/how-to-use-the-apply-function-in-r/)