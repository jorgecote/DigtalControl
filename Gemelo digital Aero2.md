# 🧪 Guía para uso del gemelo digital Quanser Aero 2

**Uso de Aero 2 y Simulink con QUARC**

---

## Introducción

1.  Registrarse en https://portal.quanser.com/Accounts/Login?returnUrl=/ utilizando su correo institucional
2.	Abrir Matlab, descargar e instalar el complemento Quanser interactive Labs for Matlab
   
![Complemento QUARC matlab](https://github.com/jorgecote/DigtalControl/blob/main/images/plantilla/Quanser%20interactive%20labs.png)

*Figura 1: Complemento Quanser interactive labs para gemelos digitales*

---
## Lanzar la aplicación en MATLAB
1. En la ventana de comandos de MATLAB (Command Window), digite `QLabs.setup` y pulse Enter.
2. Posteriormente, digite `QLabs.launch` y pulse Enter.
3. Se abrirá una ventana emergente con la opción de abrir una de las plantas disponibles.

`![Figura 2: Gemelos digitales disponibles]`
 
4. Pulsar en el **Quanser Aero** y se abrirá otra ventana emergente con la interfaz del gemelo digital.

`![Figura 3: Interfaz del gemelo digital Quanser Aero]`

---
## Configuración del Modelo Simulink

1. Abre **MATLAB** y, en la ventana de comandos, escribe `simulink` para abrir un nuevo modelo en blanco (Blank QUARC Model si está disponible, si no, un Blank Model normal).
2. Abre la ventana del **Simulink Library Browser** haciendo clic en el icono correspondiente en la pestaña de Simulación.

`![Figura 4: Componentes QUARC en Simulink Library Browser]`

3. Expande la siguiente ruta en el navegador de librerías:  
   `QUARC Targets → Data Acquisition → Generic → Configuration`
4. Arrastra el bloque `HIL Initialize` al modelo Simulink. Este bloque es esencial para establecer la comunicación con el gemelo digital.
5. Haz doble clic en el bloque `HIL Initialize` para abrir su ventana de configuración.
6. Configura los siguientes parámetros en la pestaña **Main**:
   - **Board type**: `quanser_aero2_usb` (Seleccionar de la lista desplegable).
   - Haz clic en el botón **Defaults** para aplicar las opciones por defecto para esta planta.
   - **Board identifier**: `0@tcpip://localhost:18000`  
     *(Esta dirección es la clave para conectarse al gemelo digital del Aero en lugar de a una planta física. Puede variar si se tienen varias instancias abiertas.)*
   - Asegúrate de que la opción **Active during normal simulation** esté marcada.
   - Haz clic en **OK** para cerrar la ventana.

`![Figura 5: Configuración del bloque HIL para el Aero 2 virtual]`
 
7. En la interfaz de **Quanser Interactive Labs**, asegúrate de que el Aero 2 esté configurado en modo 1-DOF (pitch-only):
    a. Desbloquea el eje de pitch (inclinación).
    b. Bloquea el eje de yaw (giro).
    c. Asegúrate de que ambos rotores estén en posición horizontal.

---

## Ejecutar el Modelo

8. Para ejecutar el controlador QUARC, simplemente presiona el botón **Run** de la pestaña **Simulation** en Simulink.

`![Figura 6: Botón "Run" en la pestaña Simulation]`

9. Si la conexión y la configuración son correctas y no hay errores, la tira de LED en la base del Aero 2 virtual se pondrá de color **verde**.

`![Figura 7: Tira LED del Aero 2 en verde indicando conexión exitosa]`

10. El botón "Run" se convertirá en un botón "Stop". Puedes hacer clic en él en cualquier momento para detener la simulación.

---

## Acelerando el Motor DC (Thruster 0)

11. Añade el bloque `HIL Write Analog` a tu modelo. Lo encontrarás en:  
    `QUARC Targets → Data Acquisition → Generic → Immediate I/O`
12. Configúralo haciendo doble clic y marcando la opción **Active during normal simulation** en la pestaña **Main**. Este bloque enviará un voltaje al canal 0, que controla el motor del thruster 0.
13. Añade un bloque `Constant` de la librería de Simulink (`Simulink → Sources`) y conéctalo a la entrada del bloque `HIL Write Analog`.
14. Ejecuta el controlador QUARC de nuevo con el botón **Run**.
15. Haz doble clic en el bloque `Constant` y establece su valor en `1.5`. Esto aplicará 1.5V al motor. Observa cómo la hélice del thruster 0 comienza a girar en el gemelo digital.

---

## Leyendo el Tacómetro

16. Añade el bloque `HIL Read Other` a tu modelo desde la misma ubicación que el `HIL Write Analog`:  
    `QUARC Targets → Data Acquisition → Generic → Immediate I/O`
17. Haz doble clic en el bloque para configurarlo. En el campo **Channels**, introduce el número `14000`. Este es el canal designado para leer el tacómetro del motor 0.

`![Figura 8: Configuración del bloque HIL Read Other]`

18. Conecta la salida del bloque `HIL Read Other` a un bloque `Gain` (`Simulink → Math Operations`) y la salida de este a un bloque `Display` (`Simulink → Sinks`), de forma similar a la Figura 1.
19. El valor que entrega el tacómetro está en `counts/s`. Para visualizar una medida más útil como **RPM (revoluciones por minuto)**, es necesario ajustar la ganancia. Sabiendo que hay un número específico de cuentas por cada revolución del motor, ajusta el valor del bloque `Gain` para realizar esta conversión.
20. Ejecuta de nuevo el controlador QUARC.
21. Cambia el valor del bloque `Constant` a un voltaje mayor, por ejemplo, `15V`. Confirma que la lectura del tacómetro en el `Display` es positiva y que la hélice gira en una dirección coherente.
22. Mide la relación entre el voltaje del motor (en el rango de 0-24V) y la velocidad de la hélice en RPM.
23. Para detener el modelo, haz clic en el botón **Stop**. La tira de LED del Aero 2 volverá a ponerse **roja**.
24. Cierra **Quanser Interactive Labs** cuando hayas finalizado.
