# 🧪 Guía para uso de gemelos digitales de Quanser 

**Uso de Qube-Servo 2 y Simulink con QUARC**

---

## Introducción

1.  Registrarse en https://portal.quanser.com/Accounts/Login?returnUrl=/ utilizando su correo institucional
2.	Abrir Matlab, descargar e instalar el complemento Quanser interactive Labs for Matlab
   
![Complemento QUARC matlab](https://github.com/jorgecote/DigtalControl/blob/main/images/plantilla/Quanser%20interactive%20labs.png)

*Figura 1: Complemento Quanser interactive labs para gemelos digitales*


> En este laboratorio, crearemos un modelo Simulink básico utilizando bloques **QUARC** para manejar el motor de corriente continua y medir el ángulo correspondiente.

![Simulink Model con QUARC](https://github.com/jorgecote/DigtalControl/blob/main/images/plantilla/diagrama%20bloques.PNG)

*Figura 2: Modelo Simulink para controlar el motor y leer el ángulo en el Qube-Servo 2*

---
## Lanzar aplicación en matlab
1. En el command window de matlab digitar QLabs.setup y pulsar enter.
2. Posteriormente digitar QLabs.launch y pulsar enter.
3. Se abrirá una ventana emergente con la opción de abrir una de las 3 plantas
   
![Gemelos digitales ecci](https://github.com/jorgecote/DigtalControl/blob/main/images/plantilla/gemelos%20ecci.PNG)
 
*Figura 3: Gemelos digitales disponibles para universidad ECCI*

4. Pulsar en el motor DC Qube 2 y se abrirá otra ventana emergente como la siguiente:

![interfaz qube servo](https://github.com/jorgecote/DigtalControl/blob/main/images/plantilla/interfaz%20qube%20servo.PNG)

*Figura 4: Gemelos digitales disponibles para universidad ECCI*

---
## Configuración del Modelo

1. Abre **MATLAB** y abre un modelo en blanco para iniciar en Simulink.
2. Abre la ventana del **Simulink Library Browser** haciendo clic en el icono correspondiente.

![QUARC componentes](https://github.com/jorgecote/DigtalControl/blob/main/images/plantilla/componentes%20quanser.png)

*Figura 5: Componentes QUARC en Simulink Library Browser*

3. Expande:  
   `QUARC Targets → Data Acquisition → Generic → Configuration`
4. Arrastra el bloque `HIL Initialize` al modelo Simulink.
5. Haz doble clic en el bloque `HIL Initialize` para configurarlo.
6. Configura en la pestaña **Main**:
   - **Board type**: `qube_servo2_usb`
   - Haz clic en **Defaults** para aplicar las opciones por defecto.
   - **Board identifier**: `0@tcpip://localhost:18920`  
     *(Para usar el Qube-Servo 2 virtual con disco)*
   - Marca la opción **Active during normal simulation**
   - Haz clic en **OK**

![Configuración HIL](images/plantilla/Quanser_conf.PNG)
 
*Figura 6: Configuración bloque HIL*

7. Verifica que el disco del Qube-Servo 2 esté abierto en **Quanser Interactive Labs**.

---

## Ejecutar el Modelo

8. Ejecuta el controlador QUARC con el botón **Run** de la pestaña **Simulation**.

![Run Simulation](https://github.com/jorgecote/DigtalControl/blob/main/images/plantilla/boton%20run.png)

*Figura 7: Botón "Run" en la pestaña Simulation*

9. Si no hay errores, la tira LED del Qube-Servo 2 se pondrá **verde**.

![qube servo conectado](https://github.com/jorgecote/DigtalControl/blob/main/images/plantilla/qube%20servo%20verde.PNG)

*Figura 8: Tira led del Qube servo en verde*

11. El botón "Run" ahora será un botón "Stop". Haz clic en él para detener el modelo.

---

## Acelerando el Motor DC

11. Añade el bloque `HIL Read Encoder Timebase` desde:  
    `QUARC Targets → Data Acquisition → Generic → Timebases`
12. Arrástralo al modelo.
13. Haz doble clic y configura:
    - **Main tab**: Marca **Active during normal simulation**
    - **Advanced tab**: Establece **Buffer overflow mode** en `Synchronize`
14. Conecta el bloque como en la Figura 1 *(sin el bloque HIL Write Analog todavía)*.
15. Añade `HIL Write Analog` desde:  
    `QUARC Targets → Data Acquisition → Generic → Immediate I/O`
16. Configúralo:
    - **Main tab**: Marca **Active during normal simulation**
17. Conecta el bloque `Constant` con `HIL Write Analog`, como se muestra en la Figura 1.

> 💡 **Stall Detection**: Monitorea el voltaje y la velocidad del motor. Si permanece inmóvil por más de 20 segundos con voltaje mayor a ±5V, la simulación se detiene para prevenir sobrecalentamiento.

![Stall Detection](https://github.com/jorgecote/DigtalControl/blob/main/images/plantilla/stall%20torque%20detector.png)

*Figura 9: Subsistema de detección de bloqueo (Stall)*

18. Ejecuta el controlador QUARC nuevamente.
19. Establece el bloque `Constant` a `0.5` para aplicar 0.5V al motor.  
    Observa la dirección de rotación del disco y verifica la medición del encoder.

---

## Lectura del Encoder

20. Establece el tiempo de parada (`Stop Time`) en `5 segundos`.
21. Usa el `Manual Switch` para cambiar el bloque de entrada a un `Pulse Generator` con:
    - Amplitud: `0.15`
    - Periodo: `10 s`
    - Ancho de pulso: `20%`
22. Ejecuta el controlador nuevamente. Se aplicará 0.15V por 2 segundos.
23. Observa cuántas vueltas da la rueda de inercia.  
    El bloque `Display` muestra los **conteos del encoder** (proporcionales al ángulo del disco).

> 📷 Usa la vista superior (Top View) en Quanser Interactive Labs para ver las revoluciones.

24. Compara el número de conteos del encoder con las vueltas observadas.
25. Revisa cómo el encoder se reinicia al relanzar la simulación.  
    Registra tus observaciones.
26. Determina cuántos conteos produce el encoder por **una vuelta completa**. Regístralo.
27. Ajusta el bloque `Gain` para convertir conteos a **grados** (ganancia del sensor).
28. Ejecuta la simulación y verifica que el ángulo mostrado en `Display` sea correcto.  
    Registra el valor de ganancia utilizado.

29. Puedes volver a usar el bloque `Constant` con un valor de 0.15V para experimentar.
30. Detén el modelo haciendo clic en el botón **Stop**.  
    La tira LED volverá a ponerse **roja**.
31. Cierra **Quanser Interactive Labs**.

---
