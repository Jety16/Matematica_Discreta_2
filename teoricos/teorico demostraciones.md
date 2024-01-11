### Clase teorica 5/5
## Complejidad de algoritmos que vimos de matching


### Algoritmo de hallar Matching maximal

- Matching inicial : Revitar cada fila: o(n) por n filas --> O(n²)

- Extender Matching en un lado: Mismo analisis -> O(n²)

- Hay O(n) exteniones de matching entonces la complejidad del matching es O(n³)

- Si se hace con Dinitz se puede ver que es O(n²,5) ya que por la estructura del grafo. (no lo van a demostrar) pero tiene el coste añadido de crear el network


### Minimizar Maximo

- Ordenar las n² entradas -_> O(n² / log(n²)) =>  O(n²/log n)  (caso general, puden haber casos que sean O²)

- Usando Busqueda Binaria O(log(n²)) hay que hacer algoritmo de hallar matchin maximal nos queda entonces O(2log(n)) = O(log(n)) Complejidad total O(n³ log n) o usando dinitz O(n²,5 log n)


### ALgoritmo hungaro de minimizar suma
Mas complicao debido a los cambios de matriz, tenemos que saber cuantos tenemos, 
usamos
- #### Lema: Luego de que el algoritmo  realiza un cambio de matriz asociado a un S con |S| > | Vecinos(S) |, si se sigue corriendo el algoritmo a partir del matching parcial que se tenia entonces crece el matching o crece "S".
(o extiendo el matchin por un lado o me vuelvo a detener y ese S va a contener extrictamente a S

### PBA: 
Al cambiar la matriz suammos m = min S * no(Vecinos(S)), restamos m de S, suammos m a vecinos(S) y luego , si continuamos desde el matching parcial, buscamos "Nuevos ceros".
Cualquier nuevo cero entrara en S * No(Vecinos(S)) supongamos que está en la fila y columnas  j => i en S, j en no(vecinos(S)) (es decir la columna j no tenía etiqueta) la columna j la etiqueteamos con i.

Al Chequear Si la columna "j" está libre o forma parte del matching, tenemos
- Si está  libre -> extendemos el matching -> crece el matching
- Si forma parte del matching -> Existe fila K tal que (k, j) es parte del matching

En particular "j" es un vecino de "k", por ende K NO pertenece a S, pues j No pertenece a los Vecinos(S)
Pero el Algoritmo al checkear J va a agregar a K al NUEVO S (noOooOo)

el S crece.


Colorario peude haber a lo sumo o(n) cambios de matriz antes de extender el matchin en un lado (pues S puede crecer a lo sumo O(n) veces)


Teorema: La complejidad del hungaro como lo dimos en clase O(N⁴)

Pba Restar min de una fila: O(n) => restamos minimo cada filas O(N2) 
similar Restar Min de cada Columnas O(n")

hallar matching inicial O(n²)

El matching inicial se puede extender a losumo O(n) veces  veces comp(hungaro) = O(n²) + O(n)
(complejidad de xtender el matchin de un lado)
Para extender el matching hay que revisar las filas buscando 0, cada busqueda es O(n)

Luego a lo sumo n, si o si extendemos el matching pero en el medio quizas, deberiamos hacer el cambio de matrices si se guimos con el matching parcial que teniamos, no hace falta reescanear  las filas de S.
Ademas, por el lema, sabemos que hay cambios de matrices menor igual O(n) antes de extender el matching

COmplejidad de extender el matchin en un lado

    CM1L = O (n²)  +   O(n)   *   CCM
escanear n filas    +   #n cambio matriz   +  (complejidad de hacer un cambio de matriz)


Cuanto cuesta cambiar la matriz?

- Calcular m = min S por No(Vecinos(s))  --> O(|S por No(Vecinos(S))| = O(n²)

- Restar m de S, sumar m a vecinos(S) ambos O(n²)

entonces CCM = O(n^2) + O(n²) + O(n²) + O(n²)

Complejidad hungaro entonces
O² + O(n)(O(n²) + O(n)*O(n²))
== > O(n⁴)


Teorema: El hungaro se puede codificar en O(n³)
pba: La clave es codificarlo de forma tal que CCM sea O(n)
Si lo logramos, queda 
Complejidad hungar = O(n²) + O(n) (O(n²) + O(n)O(n)) = O(n³)

- 1 Debemos hallar un minimo de O(n²) elementos en O(n)
- 2 Debemos cambiar O(n²) elementos en O(n) trasladamos.

Para hacer lo del minimo, parte del costo de hallar el m, se traslada a la parte donde escaneamos filas
    m = min S x NoVecinos(S)
    = Min { C_x, y ; x en S, y no en (vecinos(s)}
    = y no en vecinos(S) --> min (min {C_x, y}) ==> min U_y 

esa se puede circular en O(n) haciendo m = min U_y siempre que tengamos ya calculado los U_y ( los cuales se calculan cuando te fijas si vas a gregar o no un vecino e sdecir mientras calculas la matriz)


para calcular los U_y demora O(n) pero lo demos hacer cuando escaneamos una fila, al buscar 0's, en los "no 0" actualizamos U_y
si n ohay un 0 calculamos U_y si hay 0 actualizo (ni era tan dificil explicarlo asi)


Para 2, hacemos una "resta y sua virtual", vamos a indicar cuanto le deberiamos restarle pero sin restarle.

Usamos un "RF(x) que indique cuanto restarle a la fila(X) y un "SC(y) que indique cuanto sumarle a la columna(Y)

restar m de s es simplemente hacer RF(X) + = m Para todos x en S -> O(n)
Sumarle m a lso vecinos de s y bueno misma logica pero SC(y) += m es O(n)

Problema Chequeo de ceros


en vez de algo como If(0 == C[x][y])) se chequea if (0==C[x][y] - RF[x] + SC[y]) ---> (O(1))

fin