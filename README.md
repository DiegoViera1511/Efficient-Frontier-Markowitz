# Proyecto de Optimización de Portafolios con el Modelo de Markowitz

### Descripción del problema

- **Objetivo:** Construir un portafolio óptimo que minimice el riesgo y maximice el retorno esperado, utilizando datos históricos de precios de activos
  
- **Contexto**: Este proyecto se enmarca dentro de la gestión financiera y busca aplicar el modelo de Markowitz para seleccionar pesos óptimos para cada activo en el portafolio.

## Aprendiendo sobre finanzas 

El objetivo de invertir en empresas es hacer crecer tu dinero a lo largo del tiempo, para ello repartimos nuestro capital de inversión en diferentes activos confiables y estables. Si la empresa crece, tus acciones (activos) pueden aumentar de valor, y podrías recibir un retorno de inversión alto. El problema está en dado un conjunto de empresas como repartir mi capital de inversión en ellas.

Como un poco de historia, la teoría Moderna de Carteras fue detallada por primera vez por Harry Markowitz. Markowitz dio la teoría de que todo debería tener un equilibrio entre riesgo y rendimiento(la ganancia o pérdida que genera una inversión en relación con el monto inicial invertido), y que este acto de equilibrio podía aplicarse a cualquier activo, siempre que hubiera una medida apropiada para el riesgo, entonces Markowitz sugirió que la volatilidad(que tanto cambia el precio de los activos en el tiempo) era una buena métrica para evaluar el riesgo total, mientas más volátil sea el precio de un activo, mayor será el riesgo de dicho activo para un inversor y si es poco volátil entonces hay poco riesgo para la inversión, lo que Markowitz también notó fue que los activos más riesgosos tenían la capacidad de generar más ganancias que los activos menos riesgosos, sin embargo los activos más riesgosos también tenían más posibilidad de perder más que los activos menos riesgosos y de aquí es donde se formula la estructura riesgo/recompensa. 

Por su trabajo Markowitz recibió el Premio Nobel de Economía, Markowitz sugirió lo siguiente: Los activos se mueven de forma correlacionada y no correlacionada entre sí, por lo tanto algunos activos se moverían juntos de manera similar mientras que otros podrían moverse de manera diferente incluso opuesta, por lo tanto el creía que las correlaciones y covarianzas entre los activos eran importantes, resumió esta en relación en una **matriz de covarianza** llamada Sigma $\Sigma$ , es una matriz formada por las covarianzas de las series temporales de cada activo, algunos activos tendrán covarianzas más altas y otros más bajas.

Markowitz también consideró que había una combinación infinita de asignaciones entre los activos que una porsona podía poner en su portfolio, sin embargo solo había un subconjunto de combinaciones que, según él, eran asignaciones eficientes.

Estas asignaciones eficientes se desarrollaban a lo largo de una curva la cual el económico nombró la **Frontera Eficiente**, se consideró que las asignaciones que se encontraban a lo largo de esta frontera tenían la mejor recompensa para un nivel de riesgo determinado, entonces, ¿ como calculamos esta frontera eficiente usando nuestra **matriz de covarianza** ?

Sea $w = [ w_1 , w_2 , ... , w_n ]$ el vector de pesos ( cuanto de nuestro capital vamos a invertir ) para cada uno de nuestros activos.

Si multiplicamos $w$ por nuestra matriz de covarianza $\Sigma$ por la transposición de $w$ obtenemos un término de volatilidad al cuadrado ( $\sigma^2$ ).

$$ w \cdot \Sigma \cdot w^T = \sigma^2 $$
 
Lo que queremos saber es cuándo se minimiza este valor para un nivel dado de retorno del portafolio, llamaremos a nuestro nivel de retorno $R$, entonces ¿ como calculamos $R$ ?

Sea $ \mu= [r_1 , r_1 , ... , r_n ]$ el vector de retornos esperados donde $r_i$ es el retorno esperado del activo i.

$$\mu \cdot w^T = R$$

Que es lo mismo que 

$$R = r_1 * w_1 + r_2 * w_2 + ... + r_n * w_n$$

Ahora que tenemos nuestras dos ecuaciones. Una la queremos minimizar y otra lo que queremos maximizar, queremos minimizar el riesgo y maximizar el retorno, como estos sistemas son consistentes y subdeterminados obtenemos una curva como solución, la Frontera Eficiente.

Se puede resolver cualquier punto de la curva usando la ecuación :

$$w = \lambda \cdot \Sigma ^{-1} \cdot \mu $$

Donde $\lambda$ es el nivel de riesgo que quiere aceptar ( $\lambda >= 0$)

Nuestro objetivo es equilibrar el riesgo y la recompensa de la inversión de la forma más eficiente posible 

# Modelado del problema 

### Variables

- $w$ vector de proporciones invertidads en cada activo donde $w_i$ es el peso invertido en el activo $i$

- $\Sigma$ matriz de covariancia entre los retornos esperados de los activos

- $\mu$ vector de retornos esperados para cada activo

- $\sigma ^2$ varianza del portfolio

  
### Restricciones

- La suma de los pesos debe ser igual a 1 (invertir todo el capital de inversión):
    $$\sum_{i=1}^{n} w_i = 1$$

- Los pesos son positivos, asumimos que no vendes activos: 
  $$\forall i \; w_i >= 0$$

### Función Objetivo

Minimizar riesgo:
$$
w \cdot \Sigma \cdot w^T = \sigma^2
$$

Maximizar retorno:
$$
\mu \cdot w^T
$$



  
