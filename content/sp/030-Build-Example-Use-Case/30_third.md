---
title: "Creación del flujo de mensajes entrantes"
chapter: false
weight: 30
---

## Creación del flujo de mensajes entrantes - Inbound Message Flow

Con nuestro flujo de bot construido, necesitaremos configurar un flujo de mensajes entrantes que dirija a los clientes a este flujo de bot.

Dentro de architect, cambie el tipo de flujo a "Mensaje entrante"

![image](/images/messageflowselect.PNG)

Seleccione Agregar y proporcione un nombre y una descripción a su flujo. También puede proporcionar una cola de transferencia de eventos de error (Error Event Transfer queue) que permitirá procesar correctamente los eventos de error y permitir que las interacciones continúen fluyendo a una cola en caso de una falla lógica.

![Create Message Flow](/images/messageflowcreate.PNG)

Dentro de este flujo de mensajes, puede procesar la lógica previa al bot, como las búsquedas de acciones de datos. A los efectos de este taller, simplemente agregaremos un bloque lógico de flujo de bot de llamada.

Dentro de la caja de herramientas, expanda "Bot" y arrastre un cuadro "Llamar flujo de bot" sobre el bloque de desconexión predeterminado dentro del constructor de flujo.

![Call Bot Flow](/images/messageflowbot.PNG)

Dentro de las opciones de Call Bot Flow que se abren en el lado derecho, podemos seleccionar nuestro flujo de bot de ranura dinámica (Dynamic Slot bot flow) que acabamos de construir. También podemos definir ranuras de entrada y salida.

  * Las entradas nos permiten enviar información que ya hemos recopilado a un flujo de bot, por ejemplo, si ejecutamos una acción de datos en el flujo de mensajes y encontramos un caso abierto, podríamos enviar este caso al bot como una ranura ya ocupada. No necesitamos insumos para este taller.

  * Los resultados nos permiten almacenar datos que el bot ha recopilado del cliente para tomar más decisiones sobre el enrutamiento o la secuencia de comandos del agente. Ejemplo; el cliente usa el bot para seleccionar sobre qué nos está contactando, podemos usar esta información para enrutar a diferentes colas o proporcionar diferentes guiones a los agentes. Tampoco necesitaremos salidas para este ejemplo.

![Call Bot Flow Options](/images/messageflowbotoptions.PNG)

El último elemento que agregaremos es una transferencia al bloque ACD. Esto no será un requisito para este taller; sin embargo, permitirá probar futuras mejoras.

Dentro de la caja de herramientas, busque "Transferir a ACD" y luego arrástrelo debajo del bloque "Call Bot Flow" y seleccione su cola. Ahora puede publicar este flujo de mensajes entrantes.

Si tiene experiencia con Architect, siéntase libre de agregar cualquier otra lógica que desee.

![Transfer to ACD](/images/messageflowacd.PNG)