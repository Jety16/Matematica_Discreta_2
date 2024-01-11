# Codigos lineales

Recordemos c lineal es c subespacio vectorial de {0, 1}

Todo espacio vectorial tiene demsnion (K) y al menos una base


base   (generara)
        LI (C_1 alpha_1 +..... + C_r alpha_r = 0)


Una matriz generadora de un codigo lineal C es una matri cuyas filas Son base de C

Como las filas deben ser base, cualquier matriz generadora deber ser K*N

Observación, Si k-dimencion de C --> a {0,1}k  por ende es |C| = 2^k
Siempre es multiplo de 2

ej sea C el código cuya matriz generadora es 

G= [
    1, 1, 1, 0, 0,
    1, 1, 0, 1, 0
    1, 0, 0, 0, 1
]

Siempre mas facil con G's que tengan la identidad en algun lado.
implica que k es 3 y n = 5
por ende cardinalidad es 8 (2³)

Supongamos G = [
    G1,
    ...,
    Gk    
]

x pertenee a C si y solo si existen coeficientes c_1.... ck talque
X = c_1 g_1 +....+ c_k g_k si y solo si existe un U en {0, 1} ^k tq X = UG


volviendo al ejemplo esto nos permite dar las palabras de C


C_I {
(0,0,0)G , (1,0,0)G
(0,0,1)G, (1,0,1)G,
(0,1,0)G (1,1,0)G,
(0,1,1)G, (1,1,1)G
}


==
los numeros me indican las filas, si tengo dos numeros sumo las filas looooool

C_I{
00000, 111000,
10001, 01101,
11010, 00110,
01011, 10111
}


el delta es el menor peso de hammilt cantidad de unoss minima.
d(c)=2
esto no corrije errores


Matriz de checkeo.

una matriz h es una matriz de chequeo de un codigo c 
si C = Nu(H) = {y en {0,1}^n tal que H y^transpuesta = 0}


Si H es matriz de chequeo de C entonces
d(c) min número de columnas de H linealmente dependientes
= min {r tq existe r columnas L.D de H}
prueba:

recursiva(?)

sea m = min{r: tq existe column LD de H}
denotaremos la j-esima columna de h por H^(j)

Pof definicion de m, existen j_1, j_r tq H^(j_1)... H^(j_r) que son LD

entonces existen C1, ..., Cr perteneciente a }0, 1}
no  todos nulos 

C1*H^(j1) +++ Cr*^(jr) = 0

sea e_i = 0,....,1,0000
donde 1 en i lugar



He^t__i = H^(i)



sea X = C_1 e_j1 +++ Cr e_jr

H*X^t = H(C_1 e_j^t ++++ Cr e_jr^t)
= 0

entonces X pertenece a C

como x!= 0 pue slo ci no son puros ceros
entonces d(c) <= peso hamilet de X
pero en realidad los C_I son todos uno
porque si alguno fuese cero tendria una cantidad menos de col LD de H

 entonces ||X|| = r  entonces d<=r = m

 por otro lado sea X != 0 entocnes d (c) = ||x||
 por ende x = ei1 ++eid(c)
 0 = HX^t = H⁽i1

 colorario

 si H no tiene la columna 0 ni columnas repetidas y C = Nu(H) entonces d(c) >= 3, i.e C corrige al menos un error

 como H ^(j) != 0 paratodo j
 entonces min{{r: existe r columna ld de H} H>=2}

 supongamos que fuese 2 --> existe j1, j2 entonces H^(j1) + H^(j2) = 0
 --> H^(j1) = H^(J2) l aunica forma q la suma sea sero es q sean iguales, contradice hiportecis, fín


 ej C = nu(H) con 

 H = [
    1 0 1 1 0 0 0,
    0 1 1 0 1 0 0,
    1 0 1 0 0 1 0,
    0 1 0 0 0 0 1,
 ]

 como H no tien ela columna 0 si n columna repetida d(c) >= 3


 Como calcular dm C a partir de H
 suponiendo que las filas H dean LI.
 cualquier fila extra las cuales sean combinacion lineal de alguna que ya de 0 no aportan nada poque va a seguir siendo 0

usaos teoriam si T:V->W es una transf lineal
entonces
dim  b == tm Nu(i) + dim (tm( T))

aca tomamos T(x) = HX^t 
V ={0,1} ^n  

n = k + dim(Im)^T


pero dm(im(t))  0 dim (espacion de H )
rango columna
 rango fila (por el teorema ddel rango)
 numero  de filas si suponemos que las filas  son Li

k = n -num filas


propiedad si H es de la forma [A / I] y C = nu(H)

entonces G = [I/A^t] es Generadora de C viceversa, si G = I/A^t es generadora [A/I] es de chequeo tambien vale con (I/A) es A^t / I


por ejemplo G = [
    11100
    11010
    10001
]

luego H = [
    10 111
    01 110
]


prba sea W = { UG * U {0,1}^k} con G = (I/A^t)


queremos ver W = C

sea X perteneciente a W --> Existe U : x = UG = U[I | A^t]


obsrvacion ( si no no trabajamos en Z2 ponemos el A^t le ponemos el -)


pero dim w = k

y dim C= k 

entonces w=c

decodificar es leerla los beats donde está la identidad


supongamo sC = Nu(H) d(c) >=3 se manda x perteneciente a C, llega z
y huebo a lo sumo un error (ie d(x,z) <=1)
si z=x --> Hz^t = H x^t = 0
si d(x,z) =1 --> z= x+ ej pa algun j

Hz² = H^t (=0) + He_j^t = H ^j

H = [
    1 0 0 1 1 0 1
    0 1 0 1 1 1 0
    0 0 1 0 1 1 1
]


n = 7
k = n-3 = 4
|c|=16
sup que llegue z = 1001010

H * z^t = H1 + H4 + H6

los unos en z me dicen columnas a sumar





nombando columnas


si H tiene todas las columnas no lunas codigo se llama de codigo de hamming
hay muchos pero son todas equivalentes, tan transposicionadas
prop los códigos de hamming  son perfectos.

pba como no tiene columnas repetids ni ceros d >= 3
pero siempre están e_1`t, e_2^t y (e_1 + e_2)^t d = 3

c es perfecto en este codigo si y solo si
|c| = 2^n / 1+n
pero H tiene todas las columans no nulas si son r filas son 2^r -1 columnas 

esto implia que n es 2^r-.1 

|C| = 2 ^k

PERO K = CARDINAL DE COLUMNAS - CARDINAL DE FILAS DE h
= 2 ^R - 1 -R

