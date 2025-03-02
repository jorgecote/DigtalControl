# Descomposición en Fracciones Parciales
La descomposición en fracciones parciales es una técnica utilizada en cálculo y álgebra para simplificar expresiones racionales, es decir, fracciones donde el numerador y el denominador son polinomios. Esta técnica es especialmente útil para resolver integrales y transformadas de Laplace, ya que permite descomponer una fracción compleja en una suma de fracciones más simples que son más fáciles de manejar.
## 1. Casos de Descomposición en Fracciones Parciales
1.1  Raíces Reales Distintas

Si el denominador tiene raíces reales distintas, la descomposición es de la forma: 

$G(s)=\frac{A}{s+p1}+\frac{B}{s+p2}+\frac{C}{s+p3}$

1.2  Raíces Reales Repetidas

Si el denominador tiene raíces repetidas, se debe considerar: 

$G(s)=\frac{A}{s+p}+\frac{B}{(s+p)^{2}}+\frac{C}{(s+p)^{3}}$

1.3  Raíces Complejas Conjugadas

Cuando el denominador tiene términos cuadráticos irreducibles: 

$G(s)=\frac{As+B}{s^{2}+bs+c}+\frac{Cs+D}{s^{2}+ds+e}$

## 2. Conceptos Claves
🔑 Fracción Propia:

Una fracción donde el grado del polinomio del numerador es menor que el grado del polinomio del denominador.

🔑 Fracción Impropia:

Una fracción donde el grado del numerador es mayor o igual al grado del denominador. En estos casos, se debe realizar una división de polinomios antes de aplicar la descomposición.

🔑 Raíces de un Polinomio:

Los valores de la variable que hacen que el polinomio sea igual a cero.

## 3. Ejemplos

💡 Ejemplo 1: Obtener la descomposición en fracciones parciales de:  

$G(s)=\frac{2s^{2}-4}{(s+1)(s-2)(s-3)}$

Solución

1. Expresión en fracciones parciales:  $G(s)=\frac{2s^{2}-4}{(s+1)(s-2)(s-3)}=\frac{A}{s+1}+\frac{B}{s-2}+\frac{C}{s-3}$
2. Multiplicamos ambos lados por el denominador común:  $2s^{2}-4= A(s-2)(s-3)+B(s+1)(s-3)+C(s+1)(s-2)$
3. Expandimos y agrupamos términos en $s^{2}$, s  y constantes:

  - $$A+B+C=2$$

 - $$-5A-2B-C=0$$

 -  $$6A-3B-2C=-4$$

4. Se reuelve el sistema de ecuaciones:

  -  $$A=2, B=-1, C=1$$

5. Sustitución en la fracción parcial:

$$\frac{2}{s+1}-\frac{1}{s-2}+\frac{1}{s-3}$$

## 4. Código en MATLAB 

💡 Código en MATLAB:

```
syms s
G = (2*s^2 - 4) / ((s+1)*(s-2)*(s-3));
fracciones_parciales = partfrac(G);
disp(fracciones_parciales);
```


## 5. Ejercicios

📚 Ejercicio 1: fracciones parciales de la siguiente fracción:

$$\frac{9x^{2}+34x+14}{(x+2)(x^{2}-x-12)}$$

Solución

A primera vista, la fracción pareciera tener un factor cuadrático en el denominador. Sin embargo, podemos factorizar esta expresión de la siguiente forma:

$$x^{2}-x-12=(x+3)(x-4)$$

Entonces, la expressión solo tiene factores lineales:

$$\frac{9x^{2}+34x+14}{(x+2)(x^{2}-x-12)}=\frac{9x^{2}+34x+14}{(x+2)(x+3)(x-4)}$$

Dado que solo tenemos factores lineales, las fracciones parciales tienen la siguiente forma:

$$\frac{9x^{2}+34x+14}{(x+2)(x+3)(x-4)}=\frac{A}{x+2}+\frac{B}{x+3}+\frac{C}{x-4}$$

Ahora, vamos a multiplicar a toda la expresión por $(x+2)(x+3)(x−4):$

$$9x^{2}+34x+14=A(x+3)(x−4)+B(x+2)(x−4)+C(x+2)(x+3)$$

Podemos encontrar el valor de A al usar $x=-2:$

$$9(-2)^{2}+34(-2)+14=A(-2+3)(-2-4)+B(-2+2)(-2-4)+C(-2+2)(-2+3)$$

$$−18=−6A$$

$$A=3$$

Podemos encontrar el valor de B al usar $x=−3:$

$$9(-3)^{2}+34(-3)+14=A(-3+3)(-3-4)+B(-3+2)(-3-4)+C(-3+2)(-3+3)$$

$$−7=7B$$

$$B=−1$$

Podemos encontrar el valor de C al usar $x=4:$

$$9(4)^{2}+34(4)+14=A(4+3)(4-4)+B(4+2)(4-4)+C(4+2)(4+3)$$

$$294=42C$$

$$C=7$$

Entonces, las fracciones parciales son:

$$\frac{9x^{2}+34x+14}{(x+2)(x+3)(x-4)}=\frac{3}{x+2}+\frac{1}{x+3}+\frac{7}{x-4}$$

📚 Ejercicio 2: Expresa a la siguiente fracción en fracciones parciales:

$$\frac{5x+7}{(x+1)^{2}(x+2)}$$

Solución

El denominador de la fracción tiene un factor lineal $(x+1)$ y un factor repetido $(x+2)^{2}$ En este caso, las fracciones parciales tienen la siguiente forma:

$$\frac{5x+7}{(x+1)^{2}(x+2)}=\frac{A}{x+1}+\frac{B}{(x+1)^{2}}+\frac{C}{x+2}$$

Para encontrar los valores de A, B y C, vamos a multiplicar a toda la expresión por $(x+1)^{2}(x+2):$

$$5x+7=A(x+1)(x+2)+B(x+2)+C(x+1)^{2}$$

Al usar el valor $x=−1$ , tenemos:

$$5(-1)+7=A(-1+1)(-1+2)+B(-1+2)+C(-1+1)^{2}$$

$$2=B$$

$$B=2$$

Al usar el valor $x=−2$ , tenemos:

$$5(-2)+7=A(-2+1)(-2+2)+B(-2+2)+C(-2+1)^{2}$$

$$−3=C$$

$$C=−3$$

Finalmente, encontramos el valor de A al comparar a los coeficientes con el término $x^{2}.$ No tenemos términos en el lado izquierdo y tenemos: $Ax^{2}+Cx^{2}$ en el derecho:

Usando el valor $C=−3$ en esta ecuación, encontramos el valor de $A=3.$ Entonces, tenemos:

$$\frac{5x+7}{(x+1)^{2}(x+2)}=\frac{3}{x+1}+\frac{2}{(x+1)^{2}}+\frac{3}{x+2}$$

## 6. Conclusiones

La descomposición en fracciones parciales es una técnica fundamental para simplificar funciones racionales y resolver ecuaciones algebraicas en cálculo y análisis de señales.

Se pueden manejar distintos casos según el tipo de raíces del denominador.

Matlab permite automatizar estos cálculos de forma eficiente.

## 7. Referencias

https://es.wikipedia.org/wiki/Descomposición_en_fracciones_simples

https://www.khanacademy.org/math/algebra2/x2ec2f6f830c9fb89:poly/x2ec2f6f830c9fb89:partial-fraction/v/partial-fraction-expansion

Ejercicio 1, Ejercicio 2: Ejemploneurochispas. Recuperado el [2/3/2025], de

https://www.neurochispas.com/wiki/ejercicios-resueltos-de-fracciones-parciales/#2-10-ejercicios-resueltos-de-fracciones-parciales
