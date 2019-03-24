# UMA-non-motion-trigger
Proyecto para la UMA. Pulsera que activa un LED tras un periodo de inactividad de un sensor de movimiento.
## Motivaci�n
Las personas mayores son muy vulnerables. Este proyecto est� pensado como prototipo de una pulsera que las personas mayores puedan llevar en la mu�eca o como brazalete y que alerte ante el evento de una caida.
## Cambios en el dise�o
Inicialmente se piensa en este dispositivo como un dispositivo IoT implementado con un microcontrolador ESP32. Este se conecta a WiFi y mediante un sensor aceler�metro env�a una se�al de alerta cuando se produce un movimiento excesivamente brusco.

Para ajustarse al contenido de la asignatura de Tecnolog�a Electr�nica, se realiza varios cambios en el dise�o de este dispositivo:
- Limitaci�n: Busca realizar el dispositivo con integrados digitales y anal�gicos. Eliminando la presencia del microcontrolador.
- Simplificaci�n: Cambia el sensor aceler�metro por un tilt sensor.

## Dise�o
Usa 4 bloques diferenciados:
 - Generador de pulsos. Tiene por entrada la se�al del sensor. Dentro de este deferencia dos bloques funcionales:
  - Circuito RC.
  - Operacional con conf. trigger-schmitt.
 - Reloj r�pido.
 - Contador.
 - Astable. Para el flash del LED.