---
{"dg-publish":true,"permalink":"/proyectos-electronica/debrick-k552/"}
---

# Debrick K552

Hola, probablemente estén aquí por una de dos, o tienen curiosidad y estaban viendo mi pagina, o porque como yo les gusta joder con electrónica, y mientras estaban intentando flashear un firmware a sus teclados lo terminaron brickeando, en cualquiera de los casos les quiero explicar un poco que hice y porque:
### ¿ Teclados Mecánicos ?

https://www.youtube.com/watch?v=hrme6nUSUCc
### ¿ Debrick ?

Cuando se trata de dispositivos electrónicos con cierto grado de complejidad, es común recurrir a un microcontrolador para gestionar la lógica interna del dispositivo. En el caso específico de este teclado mecánico, el vs11k09a de Evision desempeña el papel crucial de controlar las luces y registrar las pulsaciones de las teclas. La base lógica que guía las operaciones de este microcontrolador se conoce como firmware.

Según la definición de firmware, es un programa informático que establece la lógica de nivel más bajo que controla los circuitos electrónicos de cualquier dispositivo. Como indica la Wikipedia: "**El firmware o soporte lógico inalterable es un programa informático que establece la lógica de más bajo nivel que controla los circuitos electrónicos de un dispositivo de cualquier tipo**."

A pesar de su supuesta inalterabilidad, siempre hay personas que buscan más. Modificar este firmware "inalterable" puede ofrecer beneficios sustanciales, como obtener un control total sobre las luces del teclado o implementar funciones personalizadas, como cambiar el comportamiento de una tecla específica para ajustar el brillo de la computadora al pulsarla.

El término "Brickear" tiene su origen en el inglés y significa literalmente "convertir en ladrillo". La palabra "Brick" en inglés tiene esa connotación de ladrillo. En términos sencillos, "brickeamos" nuestro dispositivo cuando cometemos un error, ya sea al realizar una modificación incorrecta en el firmware, ser víctimas de un virus u otras causas. En otras palabras, nosotros mismos somos responsables de dejar el dispositivo en estado "brickeado".

### Procedimiento para recuperar un K552 Brickeado

Antes de comenzar el proceso de flasheo del firmware en tu PC, es crucial contar con los programas necesarios ya instalados. En caso de que tu teclado esté en estado "brickeado", es probable que ya dispongas de estos programas. No obstante, si no los tienes instalados, será necesario obtenerlos.

- [Zadig](https://zadig.akeo.ie) para ver el USB ID
- El firmware del teclado
	- [Firmware K552](https://github.com/SonixQMK/Mechanical-Keyboard-Database/blob/main/stockFWs/Redragon/240B/Redragon_K552_RGB_Rev2_240B.bin)
	- [Firmwares de varios teclados](https://github.com/SonixQMK/Mechanical-Keyboard-Database/blob/main/stockFWs/)
- Para el programa para flashear tienen dos opciones:
	- [Pagina de Sonix](https://www.sonix.com.tw/article-en-4336-30356) y buscan el SONiX_USB_MCU_ISP_Tool_V2.3.3.1.zip
	- [Link Directo](https://www.sonix.com.tw/files/1/F1932A4438F3645AE050007F01006657)

Primero tienes que desconectar el teclado del PC, Remover todas las teclas con la pieza plástica que viene en la caja ( o con mucha paciencia si lo botaron como yo ), Buscar los tornillos que hay en la placa y quitarlos, quita los dos tornillos de la parte de atrás del teclado y empuja la placa desde atrás.

Busca el contacto metálico que se encuentra a la izquierda arriba del microcontrolador (Señalado en la imagen), posiblemente tengas que raspar un poco porque viene con un esmalte protector y con un cable tienes que conectar este punto con pin de el conector que esta abajo del cable negro del USB.

![Pasted image 20231211192631.png](/img/user/Proyectos%20Electronica/Media/Pasted%20image%2020231211192631.png)

Abre Zadig y en options selecciona "**List all devices** ", con los dos contactos unidos conecta el teclado al computador, una vez reconocido puedes dejar de conectar los dos puntos. En Zadig busca el nuevo USB Device que aparece cuando conectamos el teclado.

![Pasted image 20231211193007.png](/img/user/Proyectos%20Electronica/Media/Pasted%20image%2020231211193007.png)

anota el USB ID y ve a la herramienta de SONIX

![Pasted image 20231211193437.png](/img/user/Proyectos%20Electronica/Media/Pasted%20image%2020231211193437.png)

En el VID debes poner el primer campo del USB ID y en el PID debes poner el segundo campo del USB  ID y poner Load File

![Pasted image 20231211193830.png](/img/user/Proyectos%20Electronica/Media/Pasted%20image%2020231211193830.png)

Seleccionan este chip de la lista ( El SN32F24xB ), es uno de los últimos; pulsan ok y les va a abrir una pestaña para seleccionar un archivo entonces seleccionan el firmware del teclado (Redragon_K552_RGB_Rev2_240B.bin)

Una vez lo carguen, el teclado debería reiniciarse y su k552 quedaría totalmente reseteado de fabrica y ya lo pueden volver a armar

> [!question]- V > I'm good
a me escriben a mi Discord > AshValde
