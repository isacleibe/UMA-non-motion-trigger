# UMA-non-motion-trigger
Proyecto para la UMA. Pulsera que activa un LED tras un periodo de inactividad de un sensor de movimiento.
## Motivación
Las personas mayores son muy vulnerables. Este proyecto está pensado como prototipo de una pulsera que las personas mayores puedan llevar en la muñeca o como brazalete y que alerte ante el evento de una caida.
## Cambios en el diseño
Inicialmente se piensa en este dispositivo como un dispositivo IoT implementado con un microcontrolador ESP32. Este se conecta a WiFi y mediante un sensor acelerómetro envía una señal de alerta cuando se produce un movimiento excesivamente brusco.

Para ajustarse al contenido de la asignatura de Tecnología Electrónica, se realiza varios cambios en el diseño de este dispositivo:
- Limitación: Busca realizar el dispositivo con integrados digitales y analógicos. Eliminando la presencia del microcontrolador.
- Simplificación: Cambia el sensor acelerómetro por un tilt sensor.

## Diseño
Usa 4 bloques diferenciados:
 - Generador de pulsos. Tiene por entrada la señal del sensor. Dentro de este deferencia dos bloques funcionales:
  - Circuito RC.
  - Operacional con conf. trigger-schmitt.
 - Reloj rápido.
 - Contador.
 - Astable. Para el flash del LED.