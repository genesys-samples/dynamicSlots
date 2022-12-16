---
title: "Creación del flujo de bot de Genesys"
chapter: false
weight: 20
---

## Creación del flujo de bot de Genesys - Genesys Bot Flow
Se necesita un flujo de bot (Genesys Bot Flow) para lograr nuestro caso de uso de disputar una transacción. La razón por la que necesitamos un flujo de bot es para poder comunicarnos con el cliente a través de un motor NLU sobre qué transacción cree que es fraudulenta. Siga estos pasos para crear su flujo de bot. También hay un video que puede ver sobre estos pasos al final de esta sección si lo prefiere.

### Creando un Bot Flow

1. Vaya a Genesys Cloud CX Architect y elija Bot Flows en el menú desplegable de flujos
![Bot Flow](/images/botFlow.jpg)
    - nota: si no ve esto, asegúrese de que Genesys Bot Flows esté habilitado en su organización y que tenga permisos para verlos y editarlos.
2. Haga clic para crear un nuevo flujo de bot. Asígnele un nombre descriptivo y, en Plantilla, elija Flujo de bot en blanco.
![Create Bot Flow](/images/createBotFlow.jpg)

### Llamar a la acción de datos
1. Lo primero que debemos hacer en el flujo de bot es arrastrar un bloque de acción de datos de llamada como inicio de nuestro flujo.
2. Para Categoría, elija la integración de Acciones de datos de servicios web que configuró anteriormente
3. En Acción de datos, elija la acción de datos que importamos anteriormente
4. Cree variables para las Salidas de éxito de transacciones.Almacenar y transacciones.Valor 

Ahora su flujo debería verse así:
![Data Action Config](/images/dataActionConfig.jpg)

### Configuración de la variable de ranura de la lista dinámica
1. Dentro del flujo del bot, en el lado izquierdo, navegue hasta Tipos de ranuras. Haga clic para agregar un nuevo tipo de ranura
2. Asígnele un nombre descriptivo, como Lista de transacciones, y luego elija Lista dinámica como el tipo de ranura.
![Dynamic List](/images/dynamicList.jpg)
3. Ahora navegue la Configuración de flujo de bot
![Bot Flow Settings](/images/botFlowSettings.jpg)
4. En la Configuración de flujo de bot, en Tipos de ranuras dinámicss, agregue la variable que creó para las tiendas en la columna de valores.
    - En teoría, también podría elegir el monto de la transacción como variable. En un escenario del mundo real, probablemente desee que cada transacción tenga una identificación única en caso de transacciones duplicadas.
     - No tendremos ningún sinónimo en nuestro ejemplo.
    ![Dynamic Slot Type](/images/dynamicSlotType.jpg)
5. Ahora navegue hasta el botón Ranuras (Slots button) en Comprensión del lenguaje natural. Haga clic para agregar una nueva ranura. Asígnele un nombre descriptivo y elija Existente como Tipo de ranura asociada. Elija el tipo de ranura de lista dinámica que acabamos de crear.
![Create Slot](/images/createSlot.jpg)

### Creación del resto del flujo de bot
Ahora tenemos que hacer que esta disputa de transacción sea conversacional. Ya tenemos los datos que necesitamos de nuestra acción de datos y nuestras ranuras están configuradas. Usemos eso para guiar nuestra conversación.
1. Primero, necesitamos leer las transacciones al cliente. Para hacer esto, arrastre un bloque Comunicar debajo de la ruta Éxito de la acción de datos. Una vez que haya agregado esto, haga clic para configurar la comunicación a la derecha.
![Configure Communication](/images/configureCommunication.jpg)
2. En el Generador de secuencias de comunicación, agregue un texto que diga:
```Lamentamos que sienta que ha habido actividad fraudulenta en su cuenta. Leeremos sus transacciones más recientes y podrá decirnos cuál es fraudulenta.```
![Add Text](/images/addText.jpg)
3. Ahora necesitamos recorrer la matriz de tiendas de transacciones y montos y leerlos. Para hacer esto, agregue un bloque de bucle debajo de ese bloque de comunicación. Asegúrese de asignarle al índice de bucle un nombre de variable y establezca Max Loop Count en una variable que cuente la cantidad de elementos en su matriz de variables Transactions.store. Esta expresión significará que el ciclo solo ocurrirá para la cantidad de tiendas que hemos retirado en esa matriz.
    - La función Count observará la cantidad de valores en nuestra matriz y devolverá la cantidad total agregada de elementos en la matriz. Por ejemplo, tendremos 3 transacciones en nuestra matriz; por lo tanto, la función Contar devolverá un valor de 3.
![Loop](/images/loop.jpg)
4. Ahora arrastre otro bloque de comunicación dentro del bucle y haga clic para configurar la comunicación.
![loop Communicate](/images/loopCommunicate.jpg)
5. Ahora necesitamos tener una expresión que use nuestro bucle para obtener las tiendas de transacciones y las cantidades en la matriz y leerlas en orden secuencial. En el Generador de secuencias de comunicación, cambie a Expresión y pegue esta expresión:
```
MakeCommunication(
  "$", 
  ToCommunication(GetAt(Flow.transactionValues, Flow.loopIndex)), 
  "at ", 
  ToCommunication(GetAt(Flow.transactionStores, Flow.loopIndex)))
```
  - La función GetAt encuentra un valor en una matriz en función de su posición numérica. En nuestro escenario, buscamos tanto los valores de transacción como los almacenes de transacciones y encontramos esos valores en función de la posición numérica que corresponde con el recuento de bucles. La siguiente tabla da una idea visual de nuestra función anterior. Estamos utilizando el conteo de bucles para encontrar la posición numérica y luego devolver el valor de transacción y el almacenamiento de transacciones en esa posición numérica.
   - He aquí un ejemplo de lo que se devolvería con esta expresión con base a la siguiente tabla: "$100 en Walmart". Luego, el segundo bucle diría "$ 150 en Menards" y así sucesivamente.
  - Tómese un segundo para revisar la expresión y asegurarse de que tenga sentido para usted.

  |Loop Count | Numeric Position | Transaction Value | Transaction store |
  | --- | --- | --- | --- |
  |0 | 0 | 100 | Walmart|
  |1 | 1 | 150 | Menards |
  |2 | 2| 200 | DSW |


  ![Expression](/images/expression.jpg)
6. Ahora podemos pedirle al cliente que nos diga con qué tienda le gustaría disputar la transacción. Para hacer esto, arrastre un bloque Ask for Slot debajo del bloque Communicate, pero fuera del bucle. A la derecha, seleccione la ranura que creamos anteriormente. Para la pregunta especificar:
``` ¿Con qué tienda quieres disputar la transacción?```
![Ask for Slot](/images/askForSlot.jpg)
7. Por último, habilitemos los botones de respuesta rápida automática para nuestro bot. Vaya a Entrada de usuario en Configuración en el lado izquierdo y luego asegúrese de que los Botones de respuesta rápida automática estén activados.
![Quick Replies](/images/quickReplies.jpg)
8. ¡Ahora simplemente haga clic en publicar y estará listo para pasar a la siguiente sección!

Es importante saber que este flujo de bot que construimos no es típico en el hecho de que nunca tuvimos un bloque Solicitar intención. En nuestro escenario, pretendemos que ya hemos identificado que cada persona que se pone en contacto con este bot necesita disputar una transacción.

Si desea ver un video de estos pasos anteriores, navegue aquí: https://youtu.be/AbOdknMqabY



