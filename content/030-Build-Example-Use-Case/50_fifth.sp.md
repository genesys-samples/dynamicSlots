---
title: "Pruebas"
chapter: false
weight: 50
---

## Probando lo que hemos construido
Ahora que hemos creado todo, podemos probar para asegurarnos de que no haya nada que deba arreglarse. Siga para probar: 

1. Vaya a la página de herramientas de mensajería web de Genesys Cloud Developer Center  https://developer.genesys.cloud/devapps/web-chat-messenger
2. Asegúrese de iniciar sesión en su cuenta en la parte superior derecha
3. Elija su implementación de mensajería web (web messenger) en el menú desplegable y luego presione Iniciar chat
4. Haga clic en el icono de mensajería web (web messenger) que aparece en el cuadro
![Messenger Icon](/images/messengerIcon.jpg)
5. Al hacer clic en el ícono y decir 'Hola', el bot de disputa entrará en acción y leerá las transacciones y luego le dará la opción de con qué tienda disputar la transacción.
![Testing](/images/testing.jpg)
6. Después de seleccionar una opción, nuestro flujo se configura para enrutar a una cola. En un escenario del mundo real, el bot podría procesar todo detrás de escena sin necesidad de intervención humana.
7. Si desea ver el tramo del agente de la transacción, asegúrese de que su usuario sea miembro de la cola a la que se dirige el flujo de mensajes entrantes. Luego, ponga a su usuario en cola para aceptar la interacción. Para obtener más información sobre la configuración de colas y el manejo de interacciones de mensajes entrantes, consulte nuestro taller de configuración de canales de Genesys Cloud CX™️: https://workshop.genesys.com/workshops/gride-demo/. 

¡Felicitaciones! Si esto funcionó para usted, ha completado con éxito el taller.