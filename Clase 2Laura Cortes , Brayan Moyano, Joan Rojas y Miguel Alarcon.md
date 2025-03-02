# Transformada inversa y Raíces reales iguales

## 1. Transformada inversa

El método operacional (la inversa de Laplace) convierte funciones senoidales y
exponenciales en algebraicas lineales, facilitando operaciones como derivación e
integración y predicciones gráficas. También podríamos decir que es donde covertimos
una variable líneas algebraicas etc en S.

## 2. Definicion

La transformada inversa con raíces reales iguales se refiere a un proceso utilizado para encontrar la respuesta temporal de un sistema cuando el polinomio característico de su ecuación diferencial 
tiene raíces repetidas. En estos casos, las soluciones generales incluyen términos polinomiales multiplicados por exponentes, lo que implica una combinación de funciones exponenciales 
y términos de orden creciente (como t e^{at}, t^2 e^{at}, etc.). Este tipo de transformada inversa es común en el análisis de sistemas dinámicos y control, donde se requieren 
métodos especiales para tratar las raíces repetidas, y en MATLAB, se puede resolver utilizando técnicas como fracciones parciales o herramientas como residue.

## 3. Tabla con la principales transformadas inversas

![image](https://github.com/user-attachments/assets/d0bcc623-72d4-4d12-983f-a0429bea5a85)

En esta tabla podemos ver como se transforman las variables y dan un claro ejemplo de como se puede pasar de seno, coseno etc a transformada de Laplace.

## 4. ejemplo

$Y(s)=\frac{6s+2}{(s+0,5)(s^{2}+3,4s+2,4)}$

factorizamos

$Y(s)=\frac{6s+2}{(s+0,5)(s+1)(s+2,4)}$

$\frac{A}{(s+0,5)}+\frac{B}{(s+1)}+\frac{C}{(s+2,4)}$

$=A((s+1)(s+2,4))+B((s+0,5)(s+2,4))+C((s+0,5)(s+1))=6s+2$

$A(s^{2}+3,4s+2,4)+B(s^{2}+2,9s+1,2)+C(s^{2}+1,5s+0,5)=6s+2$

1) $A+B=0$

2) $3,4A+2,9B+1,5C=6$

3) $2,4A+1,2B+O,5C=2$

Despejando el sistema 3x3 por metodo de sustitucion queda que:

$A=-B-C$

2.Reemplazamos 1 en 2

$3,4(-B-C)+2,9B+1,5C=6$

$=-0,5B-1,9C=6$

$B=\frac{6-1,9C}{-0,5}$

Remplazamos las variables en 3

$2,4(-B-C)+1,2B+0,5C=2$

$2,4(-(\frac{6-1,9C}{-0,5})-C)+1,2(\frac{6-1,9C}{0,5}+0,5C=2$

$\frac{-14,4+4,56C}{-0,5}+\frac{7,6-2,28C}{-0,5}+0,5C=2$

$\frac{28,8}{1}-\frac{4,56C}{-0,5}-35,2+\frac{2,28C}{0,5}+\frac{0,5C}{1}=2$

$28,8-35,2-9,12C+4,56C+0,5C=2$

$-6,4-2,4C-4,06C=2$

$-6,46C=2+6,4$

$C=\frac{8,4}{-6,46}$

$C=-1,3$

REMPLAZAMOS EN 1

$A=-(\frac{6-1,9(-1,3)}{-0,5})$

$A=-(\frac{6+2,47}{-0,5})$

$A=-(\frac{8,47}{-0,5})$

$A=16,94+1,3$

$A=18,24$

PARA ALLAR B PODRIAMOS DECIR QUE REMPLAZANDO A NOS DIO B

$B=16,94$

POR LO QUE CUANDO SE REMPLAZO EN A Y SE OBTUVO B

## 5. RAICES REALES IGUALES

nos referimos a una situación que ocurre cuando la ecuación característica de un sistema
o ecuación diferencial tiene dos raíces reales y coincidentes.

$G(s)=\frac{N(s)}{(s+p)^{n}}$

$G(s)=\frac{NA(s)}{(s+p)^{1}}+\frac{B}{(s+p)^{2}}+\frac{C}{(s+p)^{3}}+...+\frac{(Z)}{(s+p)^{n}}$

EJEMPLO

$G(s)=\frac{2s^{2}+6s+5}{(s+2)(s+1)^{2}}$

$G(s)=\frac{A}{s+2}+\frac{B}{s+1}+\frac{C}{(s+1)^{2}}$

$\frac{A}{s+2}+\frac{(s+1)B+C}{(s+1)^{2}}=2s^{2}+6s+5$

$A(s+1)^{2}+B(s+1)(s+2)+C(s+2)$

$A(s^{2}+2s+1)+B(s^{2}+3s+2)C(s+2)$

FORMAMOS LAS ECUACIONES

$1. A+B=2$

$2. 2A+3B+C=6$

$3. A+2B+2C=5$

SUSTITUIMOS EN 1

$1.A=2-B$

SUSTITUIMOS EN 2

$2.2(2-B)+3B+C=6$

$4-2B+3B+C=6$

$4+B+C=6$

$B=6-4-C$

$B=2-C$

$SUSTITUIMOS EN 3

$3.(2-(2-C)+2(2-C)+2C=5$

$2-2+C+4-2C+2C=5$

$4+C=5$

$C=\frac{5}{4}$

$C=1.25$

SUSTITUIMOS 1

$1.A=2-(2-1.25)$

$A=1.25$

SUSTITUIMOS EN 2

$B=2-1$

$B=1$


## 6 .CONCLUCIONES

Si el discriminante es igual a cero ( b 2 − 4 a c = 0 ), entonces las raíces de la ecuación
cuadrática son reales e iguales. Con este concepto podríamos decir que nuestro
denominador es de mayor orden que el numerador.

EJERCICIO 1

$F(s)=\frac{s^{2}+2s+3}{(s+1)(s+2)^{2}}$

$\frac{A}{s+1}+\frac{(s+2)B}{(s+2)(s+2)}+\frac{C}{(s+2)^{2}}=2s^{2}+2s+3$

$\frac{A}{s+1}+\frac{(s+2)B+C}{(s+2)^{2}}=2s^{2}+2s+3$

$A(s+2)^{2}+B(s+1)(s+2)+C(s+1)$

$A(s^{2}+s+1)+B(s^{2}+3s+2)+C(s+1)$

$1.A+B=2$

$2.A+3B+C=2$

$3.A+2B+C=3$

METODO DE SUSTITUCION EN 1

$A=2-B$

SUSTITUIMOS A EN 2

$(2-B)+3B+C=2$

$2-B+3B+C=2$

2+2B+C=2$

$2B+C=2-2$

$B=-\frac{C}{2}$

SUSTITUIMOS EN 3 B Y A

$2+\frac{C}{2}-C+C=3$

$\frac{C}{2}=3-2$

$C=1*2$

$C=2$

SUSTITUIMOS EN 2 C Y B

$A+3(\frac{2}{2})+2=2$

$A+3+2=2$

$A=2-3-2$

$A=-3$

SUSTITUIMOS EN 1 A

$-3+B=2$

$B=2+3$

$B=5$

## 7. Referencias

1) ejercicios propuestos en clase
2) Ejercicios desarrollados

