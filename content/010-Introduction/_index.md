---
title: "Introducción"
chapter: true
weight: 10
---

### Actualización de terminología de flujos de bots de Genesys Dialog Engine

Antes de definir los tipos de ranuras de listas dinámicas (Dynamic List Slot Types), repasemos la terminología de Genesys Dialog Engine Bot Flows. Entonces podremos vincular cómo las ranuras dinámicas encajan en la imagen.

Estos son algunos de los términos clave que debe conocer con Genesys Dialog Engine Bot Flows:

- Intenciones: las intenciones describen un objetivo o una tarea que los usuarios quieren lograr. Por ejemplo, "Reservar una habitación" o "Consultar el saldo de la cuenta"
- Expresiones: las expresiones son frases que los usuarios utilizan para describir lo que quieren hacer. Las expresiones se asignan a las intenciones, de modo que cuando se pronuncia una expresión, activa el elemento correspondiente. Por ejemplo, si la intención es "Reservar una habitación", un enunciado podría ser "Me gustaría reservar una habitación para esta noche".
- Ranuras: las ranuras son piezas de información que se pueden usar para ayudar a cumplir la intención. En el ejemplo de "Me gustaría reservar una habitación para esta noche", la palabra "esta noche" está cumpliendo con un dato clave; la fecha de la estancia. La fecha de la estancia es una franja horaria. Podríamos seguir pidiendo otra ranura; recogiendo el tipo de habitación que necesitan para su estancia.
- Tipos de ranura: un tipo de ranura define cómo el bot procesa la información disponible en la ranura identificada. Cada ranura debe asignarse a un tipo de ranura. En el ejemplo anterior para recopilar la fecha de la estadía, un tipo de ranura puede ayudar a definir que solo estamos aceptando valores del cliente que son una fecha. Entonces, si el bot le pregunta al cliente en qué fecha quiere quedarse, el cliente no puede decir "pizza" porque el tipo de ranura no aceptará nada más que una fecha.

Las ranuras y los tipos de ranuras son, en última instancia, el enfoque del taller de hoy, así que profundicemos un poco más:

### Ranuras y tipos de ranuras - Slot & Slot Types
Hay tres tipos diferentes de tipos de ranuras (Slot types) que puede crear:

- Expresión regular: la expresión regular se utiliza para identificar patrones dentro de expresiones que coinciden con una secuencia específica de caracteres. Comúnmente conocido como REGEX, este es un método ampliamente utilizado. Para dar un ejemplo del uso de un tipo de ranura REGEX, piense en los números de cuenta. Si solo desea aceptar una secuencia de números de 10 a 12 dígitos, por ejemplo, puede tener una expresión REGEX que solo permita esa secuencia de caracteres.
- Lista - Este es el más fácil de entender porque es exactamente como suena. Piense en nuestro ejemplo anterior sobre el tipo de habitación que alguien podría reservar en un hotel. El hotel probablemente solo ofrece alrededor de 4 a 8 tipos de habitaciones, por lo que este es un ejemplo perfecto del uso de un tipo de ranura de lista. También puede incluir sinónimos de las palabras en su lista.
- Lista dinámica: si bien son similares a las listas, las listas dinámicas son útiles si su bot contiene muchos valores para un tipo de ranura y no desea agregarlos y actualizarlos manualmente a medida que cambia su lista. También son útiles cuando los valores de la lista no se conocen en el momento de diseñar el bot o si la lista es específica para cada cliente individual.

Para brindarle algunos casos de uso de lo que acabamos de describir para las ranuras de listas dinámicas, pase a la siguiente sección.