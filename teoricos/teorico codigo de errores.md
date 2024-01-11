# Codigo de correcion de errores



    Emisor --medio-(con ruido)--> Receptor
    
Culpa del ruido lo que mando peude no ser lo que llega D:

- Ejemplo


    No lo hago -----> Yo lo hago

Queremos tener una forma de que solo haya 1 forma de encontrar sentido

Tenemos un conjunto "Codigo" Que son las palabras que tienen "sentido"

Hay que elegir las palabras con menor probabilidad de error.


## Codigos:
Codigo (Binario de Bloque) Es un subconjunto de {0, 1}^n para algun n fijo.
Suponemos que todas las palabras tienen la misma longitud.

el codigo morse no es en bloque porque las palabras tienen distinto largow

La ventaja de los codigos de bloques es que como tan todos con misma longitud, contas las palabras re izi.

- Supocisión: (no siempre se cumple hay q catchear esas exceptionalidades):
El canal de transmision puede cambiar bits, pero no agregar o sustraer.
- Supocisión: Tambien suponemos que la probabilidad de cambiar 0 -> 1 es igual a la de 1 -> 0 y es la misma para todos los bits e independiente entre los bits. ( no es siempre asi normalmente que se cambie independientemente es raro ya que se suelen desencadenar cambios en kadena)

- Si llamamos p a esa probabilidad va desde 0< p< 1/2 ya que si es 0 no hacemo na y si es 1/2 quiere decir q cada bit es tirar una moneda.


#### Probabilidad de t errores = P^t (pete 🤙) 

def la dsitrnacia de hamming entre 2 palabras x, y {0, 1} ^n es 

    d_h (x,y) = # de bits de diferencia entre x e y 🤙
Propiedad: d_h es una distancia

Es decir

- A 🤙 d_h (x,y) = d_h(y,x)
- B 🤙 d_h (x,y) >= 0
- C 🤙 d_h(x,y) = 0 <--> x = y
- D 🤙 desigualdad trianqular d_h(x,y) <= d_h(x,z)+ d_h(z,y)

a,b,c es obvio waso

Solo probamo D

#### Prueba de D :d

tomemos x,y,z  
    
    alfa = {i: X<sub>i</sub> = y<sub>i</sub>}
    beta = {i: Y<sub>i</sub> = z<sub>i</sub>}
    gama = {i: X<sub>i</sub> = z<sub>i</sub>}


i pertenece a alfa y beta
entonces 

    X<sub>i</sub> = Y<sub>i</sub> = Z<sub>i</sub> --> x<sub>i</sub> = z<sub>i</sub>
    entonces alfa y beta pertenece a gama

por morgan no gama pertenece a no alfa union no beta por ende su cardinalidad es menor que la de la union y la union es menor o igual que la suma de la cardinalidad de los elementos en al union


cardinalidad no gama es la D_h(x,z) <= d_h(x,y) + d_h(y,z)
fin
