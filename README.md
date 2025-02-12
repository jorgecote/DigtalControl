# DEFINICION SISTEMAS DINAMICOS, REPASO TRANSFORMADA DE LAPLACE
En clase, los estudiantes expresan con sus propias palabras las definiciones de sistema, sistema dinámico, planta y proceso. Luego, se explica su relación con la materia y se introducen los modelos dinámicos y ecuaciones diferenciales, repasando conceptos clave. Además, se analizan los sistemas lineales y no lineales, considerando la influencia de sus parámetros. Finalmente, se estudia la transformada de Laplace, desde sus fundamentos hasta su inversa, concluyendo con un ejercicio práctico.
## 1. Conceptos
> 🔑 Un *sistema* se define como una combinacion de componentes que actuan en conjunto parea alcanzar un objetivo especifico.
> 🔑 Se considera un *Sitema dinamico* a aquel cuya salida en el presente dependa de una entrada en el pasado.
> 🔑 Se considera un *Sitema estatico* a aquel es aquel cuya salida en un momento dado depende únicamente de la entrada en ese mismo instante.
> 🔑 Un *Proceso* se entiende como una serie de etapas secuenciales que facilitan el desarrollo o la producción de un producto o la consecución de un objetivo.
> 🔑 Una *Planta* se define como la infraestructura fija que posibilita la ejecución de un proceso.
## 2. Modelos dinamicos
Es fundamental desarrollar un modelo matemático que represente la relación entre las variables de interés y el tiempo 
'$$'<a href="http://www.alciro.org/tools/matematicas/editor-ecuaciones.jsp?eq=f(t)
"><img src="http://www.alciro.org/cgi/tex.cgi?f(t)
" title="f(t)
" border="0" /></a>'$$'
Las variables experimentan variaciones a lo largo del tiempo, y para comprender su evolución y comportamiento, es crucial cuantificar la magnitud de estos cambios y analizar cómo influyen en el sistema.
## 3. Sistemas lineales y no lineales
 Un sistema lineal es aquel que cumple con el principio de superposición, lo que significa que la respuesta a múltiples entradas simultáneas es la suma de las respuestas individuales a cada entrada por separado. Además, presenta proporcionalidad, es decir, si la entrada se escala, la salida también lo hace en la misma proporción.
Por otro lado, los sistemas no lineales no cumplen con el principio de superposición. Sin embargo, pueden linealizarse en torno a un punto de operación específico, donde su comportamiento se aproxima al de un sistema lineal.
En resumen, los sistemas lineales son predecibles y más fáciles de analizar matemáticamente, mientras que los no lineales requieren métodos adicionales, como la linealización, para su estudio en ciertos rangos de operación. 
## 3.1. Modelamiento y validación
Al crear un modelo matemático usando leyes físicas, siempre habrá un margen de error en los resultados. Para asegurarse de que el modelo sea preciso, es necesario compararlo con el sistema real. Si la diferencia es demasiado grande, se deben hacer ajustes hasta que el resultado sea suficientemente cercano. 
## 3.2. Influencia de parámetros
Tomando como referencia un resorte, su comportamiento puede ser sinusoidal, presentar un decaimiento exponencial o una combinación de ambos.

## 3. Subsecciones
Las subsecciones pueden utilizarse para sub dividir ciertos temas que se tienen en clases, por ejemplo si se está trabajandolos conversores D/A, puede ser necesario subdividir este en circuito de resistencias ponderadas y circuito de escalera R2R. 
### 3.1. Título de subsecciones
Para la creación de estas subsecciones debe utilizar un tamaño de letra más pequeño, por lo tanto utilice la etiqueta '###' 
### 3.2. Numeración de subsecciones
Siga la numeración de la sección seguida de un punto y luego el número de la subsección.

## 4. Ejemplos
Si en algún caso pretende dar un ejemplo explicativo ya sea a través de texto o através de ecuaciones matemáticos, utilizar la palabra 'Ejemplo' seguido de una numeración consecutiva dentro de la clase. Utilice el emoji 💡 antecediendo la palabra.

## 5. Ecuaciones
Para la edición de ecuaciones debe utilizar la etiqueta '$$' al comienzo y final de la ecuación para que la ecuación quede centrada ocupando una línea. Si se quiere que la ecuación quede integrada en el texto debe utilizar la etiqueta '$' al comienzo y final de la ecuación. Las ecuaciones pueden ser editadas utilizando el código LATEX, en el siguiente enlace encuentran un editor de ecuaciones que les genera el código. http://www.alciro.org/tools/matematicas/editor-ecuaciones.jsp . Sin embargo hay muchas otras herramientas que pueden utilizar para esto.

💡**Ejemplo 1:** si se va a representar la ecuación de la ley de Ohm se puede mostrar así $R=\frac{V}{I}$ o también,

$$R=\frac{V}{I}$$

## 6. Figuras
Todas las figuras que incluya deben ser generadas por ustedes, **no utilizar las figuras de las presentaciones**. Para incluir figuras puede seguir los siguientes pasos:
* Primero escribimos ![]().
* Después escribimos, dentro de los corchetes, el texto alternativo. Este es opcional y solo entra en acción cuando no se puede cargar la imagen correctamente.
* Después escribimos, dentro de los paréntesis, la ubicación del archivo (ya sea una url o una ubicación dentro de algun folder local). Se recomienda poner las imágenes en una carpeta que se llame imágenes dentro del repositorio github para que no tengan problemas al cargar las imágenes.

💡**Ejemplo 2:**

![Figura de prueba](images/plantilla/Captura2.PNG)

Figura 1. Figura de prueba

Incluya la respectiva etiqueta a modo de descripción de la figura y mantenga numeración consecutiva para todas las figuras de la clase.

## 7. Tablas
En caso de necesitar la inclusión de tablas para organizar información se recomienda el uso de la herramienta del siguiente enlace https://www.tablesgenerator.com/markdown_tables , la cual permite organizar la información dentro de la tabla y genera el código markdown automáticamente:

💡**Ejemplo 3:** 

| **Resultado** | **x = número de intentos hasta primer éxito** |
|---------------|-----------------------------------------------|
|       S       |                       1                       |
|       FS      |                       2                       |
|      FFS      |                       3                       |
|      ...      |                      ...                      |
|    FFFFFFS    |                       7                       |
|      ...      |                      ...                      |

Tabla 1. Tabla de ejemplo

Cada tabla debe llevar la etiqueta que describa su contenido y numeración consecutiva para todas las tablas

## 8. Código
Teniendo en cuenta que el curso requiere del desarrollo de código matlab, c, c++ u otro. Si requiere incluir pequeños segmentos de código en los apuntes hágalos de la siguiente manera:

💡**Ejemplo 4:**
```
var sumar2 = function(numero) {
  return numero + 2;
}
```

## 9. Ejercicios
Deben agregar 2 ejercicios con su respectiva solución, referentes a los temas tratados en cada una de las clases. Para agregar estos, utilice la etiqueta #, es decir como un nuevo título dentro de la clase con la palabra 'Ejercicios'. Cada uno de los ejercicios debe estar numerado y con su respectiva solución inmediatamente despues del enunciado. Antes del subtitulo de cada ejercicio incluya el emoji 📚

## 10. Conclusiones
Agregue unas breves conclusiones sobre los temas trabajados en cada clase, puede ser a modo de resumen de lo trabajado o a indicando lo aprendido en cada clase

## 11. Referencias
Agregue un subtítulo al final donde pueda poner todas las referencias consultadas incluyendo el origen o fuente de los ejercicios planteados. Tambien dentro del texto referencie los textos o artículos consultados y las figuras y tablas dentro de la explicación de las mismas.
