# UMA-non-motion-trigger
Proyecto para la UMA. Pulsera que activa un LED tras un periodo de inactividad de un sensor de movimiento. :octocat:
## Motivaci�n
Las personas mayores son muy vulnerables. Este proyecto est� pensado como prototipo de una pulsera que las personas mayores puedan llevar en la mu�eca o como brazalete y que alerte ante el evento de una caida y, proporcionarles as�, ayuda con la mayor urgencia posible.
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
- [X] 74HC191	x 1
- [ ] 74HC04	x 1
- [ ] 74HC08	x 1
- [X] 74HC00	x 1
- [ ] 74HC86	x 1
- [X] 74HC244	x 1
- [X] 10k resistor	x 3
- [ ] 70k resistor	x 1
- [ ] 5.83k resistor	x 1
- [ ] 3k resistor	x 1
- [ ] 3.9k resistor	x 1
- [ ] 1N4001	x 2
- [X] TL082	x 1
- [X] LM555	x 1
- [X] 10n capacitor	x 3
## Lista de distribuidores

## Justificaci�n de los componentes
En este apartado se describe con detalle los motivos que han llevado a escoger los modelos de integrados entre otros modelos. Antes de empezar se debe comentar que este se trata de un prototipado. Por lo que por simplicidad del proyecto se han procurado escoger componentes con los que se encuentra el dise�ador familiarizado. Por otro lado, se ha escogido tecnolog�a CMOS de alta velocidad.
### 74HC191 : contador 4 bits -->
Este es un contador de 4 bits con una entrada /LOAD as�ncrona, activa a nivel bajo --> Seg�n la hoja de caracter�sticas necesita un ancho de pulso de 16 ns con ``Vcc=4.5V`` para tener la certeza de que se ha introducido el valor del preset en la cuenta. Este es un tiempo muy reducido, a�n as�, tendremos que procurar que se cumpla este tiempo en nuestra se�al /LOAD cada vez que queramos realizar el reseteo de la cuenta.
El valor de preset que introducimos es el ``0000``. Junto con la se�al D/U y /CTEN a nivel bajo permitimos el avance de la cuenta.
### LM555
## Calculo de resistencias del trigger-schmitt
## Calculo de frecuencia del LM555_astable
Este componente tiene dos dos resistencias (t�picamente llamadas ``RA`` y ``RB``) y un condensador ``C``. Esta configuraci�n funciona como un multivibrador. El condensador ``C`` se carga a trav�s de ``RA + RB`` y se descarga a trav�s de ``RB``. La relaci�n entre estas dos resistencias dar� el ciclo de trabajo de la se�al de salida.
Lo primero que se debe saber es el periodo de reloj que se necesita --> Se supone que 10 segundos sin se�al del sensor es suficiente para tener que activar la alarma. Esta activaci�n viene dada por el MSB del contador. Antes ha tenido que pasar por varios valores
```
0000
0001
0010
0011
0100
0101
0110
0111
```
8 valores que se reparten en 10 segundos : Tenemos un periodo de reloj de 0.8 Hz.
Esa frecuencia de reloj es bastante baja y se necesitar�a usar unos valores de ``C``, ``RA`` y ``RB`` muy altos. Es prefer�ble usar un biestable D como divisor de frecuencia. De esta manera lograr�amos obtener una se�al de reloj de ciclo de trabajo del 50% de la frecuencia deseada.
Esta configuraci�n del biestable D divide la frecuencia del reloj por 2. Si se utilizan dos biestables. La frecuencia deseada como salida del LM555 es de 3.2 Hz. --> Para esta frecuencia, si se utiliza un condensador de 100nF se tiene:
```
C = 100n
RA = 1M
RB = 1.75M
```
**NOTA : Investigar por qu� la simulaci�n reloj_contador no concuerda con el resultado obtenido anal�ticamente**