---
title: "Casos de uso para ranuras de listas dinámicas - Dynamic List Slots"
chapter: true
weight: 10
---

## Casos de uso

Las ranuras dinámicas (Dynamic slots) realmente abren las puertas a la automatización completa dentro de un bot. Históricamente, un administrador tendría que modificar qué ranuras captura un bot cuando cambian las ofertas o los servicios de su organización. Las ranuras dinámicas permiten que el bot construya su lista de ranuras por interacción a partir de una fuente de datos interna o externa. Esto significa que un cliente siempre puede estar interactuando con los datos más actualizados y los administradores no los están construyendo manualmente. Aquí hay algunos ejemplos de casos de uso:

**Case de uso 1:** Una compañía de seguros amplía sus ofertas para incluir tipos y paquetes de seguros adicionales. En lugar de que un administrador agregue estos elementos adicionales a la lista de espacios, la API que extrae los servicios actuales verá automáticamente las nuevas ofertas y las capturará como ranuras aceptadas dentro del flujo del bot.

**Caso de uso 2:** Un cliente está utilizando un menú de autoservicio para ordenar una pizza, sin embargo, la compañía de pizzas se quedó sin un ingrediente específico. Por lo general, esto resultaría en una devolución de llamada al cliente para informarle que no está disponible, sin embargo, los slots (ranuras) dinámicos permitirían que el bot ya no lo reconozca como un slot aceptado y podría recomendar algo más en su lugar.

**Caso de uso 3:** Un cliente se comunica con un banco para discutir un cargo en su cuenta. Las ranuras dinámicas le permiten al bot extraer todas las transacciones recientes y reconocerlas como ranuras referenciables. El bot puede leer las diversas transacciones al cliente y permitirle decir qué transacción cree que es un fraude. Para crear esto sin ranuras dinámicas, un administrador tendría que crear un flujo complejo para iterar a través de las transacciones del cliente y permitir que el cliente actúe a partir de ellas.

Para este taller, desarrollaremos el Caso de uso 3 en su propio entorno.