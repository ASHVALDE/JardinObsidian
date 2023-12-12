---
{"dg-publish":true,"permalink":"/proyectos-electronica/debrick-k552/"}
---

Hola, probablemente estén aquí por una de dos, o tienen curiosidad y estaban viendo mi pagina, o porque como yo les gusta joder con electrónica, y mientras estaban intentando flashear un firmware a sus teclados lo terminaron brickeando, en cualquiera de los casos les quiero explicar un poco que hice y porque:
### ¿ Teclados Mecanicos ?

El Kumara k552 es el teclado mecánico de gama Media-Baja mas vergas que se puede encontrar, Un teclado mecánico es un teclado un poco mas "Premium" que los teclados tradicionales por la forma como funciona, un teclado tradicional;

Un teclado tradicional tienen dos membranas plásticas en todo el teclado parecidas al forro de un celular, cuando uno presiona una tecla la membrana plástica de encima hace contacto con la de abajo hace que dos placas conductores conecten, permitiendo el paso de la corriente.

![tec_1.gif](/img/user/Proyectos%20Electronica/Media/tec_1.gif)

Por el contrario los teclados mecánicos tienen mecanismos mecánicos (Valga la redundancia ) por cada una de las teclas, esto tiene muchísimos beneficios:

- Uno puede personalizar el sentir de cada tecla dependiendo de que Mecanismo ( Switch's ) le coloque a su teclado, dentro de las muchas cosas que se pueden elegir están:

	- La fuerza para el accionamiento
	- El punto de accionamiento: (Algunas personas prefieren que la tecla se pulse a la mitad del recorrido o otras preferimos pulsar la tecla por completo para que se registre la accion)
	- Sonido: Algunas personas prefieren teclas que suenan mas al pulsar cada tecla mientras que otras pueden sonar incluso menos que los teclados de membrana

- La calidad de construcción es mucho mayor
- Son un poco mas pesados y no se mueven tanto de sitio


Otra de las diferencias con el teclado mecánico es que el teclado de membrana al ser dos placas algo que se hace para ahorrar dinero, es que pueden conectar las teclas como una matriz y esto provoca que dos teclas que cuando uno presiona una tecla en una fila, toda esa fila se desactiva , esto no sucede en los teclados mecánicos por lo general porque tienen cada una su propio mecanismo y van conectadas directamente al chip controlador

Mas info de esto en https://landing.coolermaster.com/faq/anti-ghosting/

![Pasted image 20231211171145.png](/img/user/Proyectos%20Electronica/Media/Pasted%20image%2020231211171145.png)


Los teclados mecánicos por el contrario tienen la ventaja de que cada mecanismo va conectado directamente al chip controlador entonces no presentan este ghosting.

En resumen los teclados mecánicos funcionan distinto y tienen muchas ventajas con respecto a los teclados de membrana




### ¿ Brickeo ?

Cuando se tiene un microcontrolador programable como es el caso de los Arduinos, teclados o aparatos con electrónica "inteligente", estos obligatoriamente tienen un firmware

"El firmware o soporte lógico inalterable es un **programa informático que establece la lógica de más bajo nivel que controla los circuitos electrónicos de un dispositivo de cualquier tipo**. " - https://es.wikipedia.org/wiki/Firmware

Cuando se realiza una modificación en el firmware se corre el riesgo de dañar permanentemente el dispositivo y el Kumara k552 no es una excepción, esto puede suceder porque se modifica el firmware con la lógica de otro dispositivo, porque no esta bien programado el nuevo firmware o porque no se termina de quemar.

En mi caso le monte al chip controlador del teclado un firmware de una versión que no correspondía ( el k556 ), y dado a que el firmware no correspondía y este controla absolutamente todo del teclado también deshabilito la interfaz USB por lo cual no volvió a prender y no podía quemarle ningún firmware 



### Solución

Para recuperar el teclado es necesario

1) Desconectar el teclado del computador xd 
2) Instalar Zadig
https://zadig.akeo.ie
3) Instalar la herramienta para modificar el firmware del kumara

https://www.sonix.com.tw/article-en-4336-30356 - Buscan el 
SONiX_USB_MCU_ISP_Tool_V2.3.3.1.zip

Si no lo encuentran el link directo es 

https://www.sonix.com.tw/files/1/F1932A4438F3645AE050007F01006657


4) Remover todas las teclas con la pieza plástica que viene en la caja ( o con mucha paciencia si lo botaron como yo )
5) Buscar los tornillos que hay en la placa y quitarlos
6) Quitar los tornillos de la parte de atrás del teclado y empujar la board desde atras
7) Conectar el contacto metálico señalado en la imagen con la tierra ( El cable negro del cable USB ), Tendrías que conectarlo con el pin que sale del conector

![Pasted image 20231211192631.png](/img/user/Proyectos%20Electronica/Media/Pasted%20image%2020231211192631.png)
8) Abrir Zadig, conectar el cable haciendo contacto en los dos pines y conectar el USB al computador con los dos pines conectados, una vez conectado ya puedes soltar el cable que conecta la tierra y el pin que activa el modo directo

9) en Zadig buscar el nuevo USB Device que aparece cuando conectamos el teclado
![Pasted image 20231211193007.png](/img/user/Proyectos%20Electronica/Media/Pasted%20image%2020231211193007.png)
10) anotan el USB ID y se van la herramienta de SONIX

![Pasted image 20231211193437.png](/img/user/Proyectos%20Electronica/Media/Pasted%20image%2020231211193437.png)

El VID es el primer campo del USB ID y el PID es el segundo campo del USB  ID, entonces tienen que escribirlo en ese campo y poner Load File

![Pasted image 20231211193830.png](/img/user/Proyectos%20Electronica/Media/Pasted%20image%2020231211193830.png)

Seleccionan este chip de la lista, es uno de los últimos, pulsan ok, les abre una pestaña entonces seleccionan el siguiente archivo

![[Proyectos Electronica/Media/Redragon_K552_RGB_Rev2_240B.bin]]

Una vez lo carguen, el teclado debería reiniciarse y su k552 quedaría totalmente reseteado de fabrica y ya lo pueden volver a armar
