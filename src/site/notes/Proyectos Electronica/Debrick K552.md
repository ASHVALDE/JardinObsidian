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




1) Desconectar el teclado del computador xd 
2) Instalar Zadig

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

https://github.com/SonixQMK/Mechanical-Keyboard-Database/blob/main/stockFWs/Redragon/240B/Redragon_K552_RGB_Rev2_240B.bin

Una vez lo carguen, el teclado debería reiniciarse y su k552 quedaría totalmente reseteado de fabrica y ya lo pueden volver a armar
> [!question]- How are you? > I'm good
