Estos modelos temporales antes citados [8], [19], [20] se
basan en la generación de relaciones empíricas entre datos
satelitales y los datos de campo (del vector). Esto significa
que sólo pueden construirse modelos en lugares donde esté
disponible la información de campo. En este marco, y con
el objetivo final de mejorar la aplicación operativa
presentada por Porcasi y colaboradores en 2012 [13], nos
planteamos en este trabajo el objetivo específico de generar
una metodología para espacializar los modelos temporales
generados siguiendo la metodología de German 2018 [20],
basados en el concepto de Distancia Ambiental
Normalizada (NED).




Donde coef ji representa los coeficientes del modelo de la
ciudad j para la variable i, y envVar_i(j) representa la
variable ambiental i evaluada en la posición correspondiente
a la ciudad j. Es decir para cada ciudad j, hay un conjunto
diferente de coeficientes,



donde J corresponde a la ciudad más cercana. Una mejora
en este enfoque, es utilizar un promedio de los N modelos
conocidos ponderados por el inverso de la distancia de este
nuevo punto X a cada una de las ciudades J donde se
dispone de un modelo. Es decir, el modelo de la ciudad más
cercana pesará más y el de la más alejada pesará menos, es
decir:




Donde Lj representa la distancia normalizada de la ciudad J
a X (la localización geográfica de la nueva ciudad).






El problema de las soluciones anteriores, es que realmente es más
razonable pensar que el comportamiento de la población del  
vector/mosquito en una ciudad en el punto X será más coincidente con  
el de una ciudad que es más similar ambientalmente y no con aquella  
que está más cerca. En ese sentido, se debería utilizar (en el  
esquema del vecino más cercano) el modelo de la ciudad J que posea un
medio ambiente más similar al del pueblo ubicado en X. En otras
palabras, así como “más cerca”, significa típicamente coordenadas  
geográficas (o posiciones) similares; en el sentido  
ecológico/ambiental, podemos pensar "más cerca" como que sus  
variables ambientales son similares. De esta forma  aparece  
naturalmente  el  concepto de Distancia Ambiental.
