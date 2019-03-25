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
### Tecnolog�a
Se escoge tecnolog�a CMOS para la implementaci�n de este proyecto.

## Lista de componentes
Lista de componentes que se debe comprar para la realizaci�n de este proyecto:
```
[ ] 74HC191	x 1
[ ] 74HC04	x 1
[ ] 74HC08	x 1
[ ] 74HC00	x 1
[ ] 74HC86	x 1
[ ] 74HC244	x 1
[ ] 10k resistor	x 3
[ ] 70k resistor	x 1
[ ] 5.83k resistor	x 1
[ ] 3k resistor	x 1
[ ] 3.9k resistor	x 1
[ ] 1N4001	x 2
[ ] TL082	x 1
[ ] LM555	x 1
[ ] 10n capacitor	x 3
```
## Lista de distribuidores