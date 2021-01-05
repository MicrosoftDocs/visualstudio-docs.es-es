---
title: Animaciones para Visual Studio | Microsoft Docs
description: Obtenga información sobre las reglas que ayudan a garantizar estilos de animación coherentes y fáciles de conocer en el IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c86b033986511100415989e76f4f1e6ef7702f10
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715956"
---
# <a name="animations-for-visual-studio"></a>Animaciones para Visual Studio
## <a name="animation-fundamentals"></a>Aspectos básicos de la animación

### <a name="animation-best-practices-in-visual-studio"></a>Procedimientos recomendados de animación en Visual Studio
Siga estas reglas para garantizar que los estilos de animación sean coherentes y fáciles de ver en el IDE de Visual Studio.

- **Ser selectivo.** Limite las animaciones a las que sirven para fines específicos.

- La **temporización y la velocidad son importantes** para asegurarse de que las transiciones se sienten rápidas y naturales:

  - Completar transiciones animadas en un plazo de medio segundo (500 milisegundos).

  - Las animaciones que se producen con frecuencia deben ser lo suficientemente rápidas como para que no interrumpan el flujo de trabajo del usuario. Vea la animación en un bucle y ajuste el tiempo hasta que parezca adecuado.

  - Las animaciones no deben ser tan rápidas o discordante que resulte difícil de entender, pero no tan lenta que hace que sea un paciente para finalizar la transición.

  - Utilice el control de tiempo variable para enfatizar la importancia. Por ejemplo, al desplazarse por una secuencia de elementos de un diagrama de clases, la velocidad de las transiciones entre los elementos se ralentiza para centrarse en elementos importantes.

- **Use la aceleración no lineal gradual** de un estado a otro, lo que dará una idea del movimiento en calma y natural.

- Siempre que sea posible, **utilice una animación sutil de Hover** para indicar elementos interactivos bajo el mouse.

- Si confía en gran medida en las animaciones de sus características, **proporcione un medio para** desactivarlas localmente (para todas las características) como una opción en el cuadro de diálogo **herramientas > opciones** .

- **Solo se debe realizar una animación cada vez** y transmitir solo una parte de la información. Más de un objeto que se mueve o intenta transmitir varias cosas puede ser confuso.

- **El detalle es importante.** En la mayoría de los casos, la animación no tiene que solicitar la atención del usuario para atender su finalidad. Los cambios sutiles en el tiempo, la secuenciación y el comportamiento pueden afectar de forma significativa a la percepción y pueden hacer la diferencia entre una animación efectiva e ineficaz.

- Al usar animaciones para atraer la atención a algo, asegúrese de **que merece la pena interrumpir el** entrenamiento del usuario.

- **Al mostrar el progreso o el estado** a través de la animación:

  - Dejar de mostrar el movimiento de progreso cuando el proceso subyacente no avanza.

  - Distinga los procesos indeterminados de los procesos determinan.

  - Asegúrese de que una animación tenga Estados de finalización e identificación de errores.

  - Minimice el uso de animaciones de efectos que muestren el estado y asegúrese de que tienen un valor real proporcionando información adicional del uso real. Algunos ejemplos son los cambios de estado transitorios y las emergencias

#### <a name="animation-donts"></a>La animación no:

- No utilice movimientos pequeños (movimiento en una superficie pequeña). Prefiera atenuar y cambios sobre el movimiento de objetos.

- No use animaciones que tengan lugar en un área grande de espacio real de la pantalla. Independientemente del tamaño, este estilo de animación distrae al usuario.

- No use animaciones que no estén relacionadas con el objeto con el que el usuario se centra actualmente o con los que interactúa.

- No use animaciones que requieran la interacción del usuario para restablecer el estado, como obligar al usuario a responder a una notificación en parpadeo para que se detenga el parpadeo. Interactuar con ellos de cualquier manera debe ser suficiente para descartarlos.

Para obtener más información sobre las aplicaciones de estas prácticas recomendadas, consulte [patrones de animación](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Métricas de animación

- El sistema debe reaccionar de manera visible a los gestos del usuario en menos de 10 milisegundos.

- Las transiciones animadas no deben tardar más de 500 milisegundos en completarse.

- Una manera de compensar las transiciones que requieren más tiempo es separarlas en dos partes. Por ejemplo, la primera parte de una animación podría ser el contenedor de contenido vacío (hasta 500 milisegundos), seguido del contenido fundido en el contenedor (hasta 500 milisegundos).

- En el caso de los tiempos de carga que se pueden calcular, se prefiere un indicador de progreso determinante (indicador de progreso por porcentaje completado).

- En el caso de los tiempos de carga que no se pueden calcular, es adecuado un indicador de ocupado como un cursor o una animación giratoria incrustada (carga o indicador de trabajo).

### <a name="animation-as-communicator"></a>Animación como Communicator
En la interfaz de usuario de Visual Studio, la animación funciona solo como una herramienta de comunicación.  Se usa para comunicar una gran variedad de información, como cambios estructurales en la interfaz de usuario (por ejemplo, cuando se abre o se cierra un menú). La animación puede ayudar a visualizar el comportamiento dependiente del tiempo de sistemas complejos, como la visualización del progreso de la instalación. También se pueden usar animaciones para atraer la atención con alertas y notificaciones.

 Las animaciones de interfaz de usuario funcionan normalmente de cuatro maneras: visualizar, atraer la atención, simular y tiempos de respuesta/indicadores de progreso.

#### <a name="visualize"></a>Visualización
La animación puede enfatizar la naturaleza tridimensional de los objetos y facilitar a los usuarios la visualización de su estructura espacial. Para lograr esto, es posible que la animación tenga que girar el objeto en un círculo completo, reactivarlo lentamente y retrocederlo, o colocar el objeto más cerca y aumentar ligeramente su tamaño para enfatizar la sustitución o el foco.

Aunque los objetos tridimensionales pueden moverse con el control de usuario, el diseñador debe determinar de antemano (mediante programación o manualmente) cómo animar mejor un movimiento que proporciona una comprensión óptima del objeto. Esta animación programada puede activarla el usuario colocando el cursor sobre el objeto, mientras que los movimientos controlados por el usuario requieren que el usuario comprenda cómo manipular el objeto. Limitar el movimiento a un solo eje o orientación a la vez; Escale, rote o traduzca, pero no haga más de uno simultáneamente.

La categoría visualizar incluye los aspectos de los datos, las relaciones, el estado, la estructura, la secuencia y la hora.

##### <a name="data"></a>data
Mostrar información compleja y variable:

- Desplazarse a través de visualizaciones de información como gráficos y gráficos

- Recorrer una secuencia, un paseo guiado y una paginación

- Llamar a detalles, señalar y resaltar información específica

- Superposición de detalles e información adicional sobre un elemento con foco

- Transformación de una representación estructural o organizativa a otra

- Representar cambios con el tiempo mediante controles deslizantes de tiempo, ruedas de quiebro y lanzadera y controles de transporte (reproducir, detener y pausar)

##### <a name="relationships"></a>Relaciones

- Muestra cómo se relacionan entre sí los elementos o qué elementos se relacionan con un elemento determinado.

- Mostrar jerarquías y relaciones primario-secundario o del mismo nivel

- Un elemento genera otro

- Un elemento se minimiza en otro elemento

- Un elemento anclado a otro

##### <a name="state"></a>State

- Actualizaciones de contenido

- Selección y foco del usuario

- Progreso

- Errors

##### <a name="structure"></a>Estructura

- Dinamizar la estructura en un nodo

- Reorientar

- Minimizar y maximizar, o expandir y contraer

##### <a name="sequence"></a>Secuencia

- Secuencia de presentación

- Voltear imágenes

##### <a name="time"></a>Hora

- Mostrar cambio con el tiempo, lapso de tiempo y screencast

- Moverse a la papelera, deshacer y rehacer

- Restaurar estado histórico

#### <a name="attract-attention"></a>Atraer la atención
Si el objetivo es atraer la atención del usuario a un solo elemento de varias o para avisar al usuario de la información actualizada, es posible que una animación sea adecuada. Por ejemplo, la página de inicio de la aplicación puede emplear un botón Introducción que se desliza en el lugar después de que se cargue la página.

Como regla, el último elemento que se mueve en la pantalla atrae la atención del usuario.  En una serie de elementos animados, la atención del usuario seguirá el último objeto que se mueve.

##### <a name="alert"></a>Alerta

- Avisar al usuario, prestar atención, mostrar el progreso

- Mostrar que algo se realiza correctamente o de forma incorrecta, o que muestra cambios de progreso o progreso

- Preguntar a los usuarios durante una tarea, como buscar más información en línea o aprender sobre la tarea actual

##### <a name="notifications"></a>Notificaciones

- Alertar al usuario sobre una condición de error

- Interrumpir al usuario para ver si desea asistir a otra cosa

- Informe suavemente al usuario de que se ha completado o cambiado un proceso, como cuando se completa una descarga.

#### <a name="simulate"></a>Simular
Esta categoría cubre la física y la dimensionalidad.

- Muestra de dónde proceden los objetos o adónde van a

- Expandir y contraer o abrir y cerrar

- Movimiento panorámico, desplazamiento y reactivación de páginas

- Apilamiento y ordenación z

- Carrusel y Accordion

- Voltear y girar la interfaz de usuario

#### <a name="response-and-progress-indicators"></a>Indicadores de progreso y respuesta
Los indicadores de progreso tienen un par de ventajas destacadas:

- Los indicadores de progreso determinante e indeterminados garantizan al usuario que el sistema no se ha bloqueado y está trabajando en el problema.

- Los indicadores de determinan proporcionan al usuario una idea del progreso de la acción, así como una sensación de llegar más cerca al final.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Patrones de animación

### <a name="overview"></a>Información general
Las animaciones de Visual Studio están diseñadas para servir una función específica sin obstaculizar la productividad del usuario. Por lo general, las animaciones en Visual Studio deben ser:

- Pequeño y discreto

- Natural y realista

- Sutil y subdued

- Rápida y eficaz

- Relajado, no hurried

En esta ilustración se muestran los estilos de animación recomendados para Visual Studio. No se usa con más frecuencia ninguna animación ni animaciones sutiles, como fundidos o fundidos. Hay una aplicación limitada de animaciones de movimiento como expandir y contraer, cambio de posición X e y y rotación.

![Estilos de animación recomendados para Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Estilos de animación recomendados para Visual Studio

#### <a name="appear-and-disappear"></a>Aparecen y desaparecen
Con este patrón, un elemento cambia de visible a no vista y atrás sin una animación de transición.

![Animación de aparecer y desaparecer](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Animación de aparecer y desaparecer

##### <a name="correct-usage"></a>Uso correcto
Nuevos elementos de la interfaz de usuario que deben aparecer o desaparecer al instante para que no se distraigan ni se obstruyan. Además, las animaciones de movimiento lento se pueden percibir como un arrastre de rendimiento, que no se producirá con el estilo de mostrar y desaparecer.

##### <a name="incorrect-usage"></a>Uso incorrecto
Casos en los que la interfaz de usuario aparece de manera repentina, el usuario no tiene ninguna idea de lo que ha sucedido y agregar una animación ayudaría a comprender el contexto.

##### <a name="animation-properties"></a>Propiedades de animación
El tiempo de retardo suele ser de cero segundos.

##### <a name="examples"></a>Ejemplos
- Ocultar automáticamente las ventanas de herramientas

- Interfaz de usuario del editor activada mediante teclado, como IntelliSense y la ayuda de parámetros

- Expandir y contraer regiones de código

#### <a name="fade-in-and-fade-out"></a>Fundido de salida y fundido de salida
Con este patrón, un elemento de la interfaz de usuario realiza una transición de no visible (0% de opacidad) a visible (opacidad del 100%) o viceversa.

![Animación de fundido de salida y de fundido](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animación de fundido de salida y de fundido

##### <a name="correct-usage"></a>Uso correcto
Esta es la animación de IU recomendada más comúnmente. Es un efecto sutil que agrega interés sin interrumpir el flujo. En algunos casos, es posible que el usuario no se dé tener en cuentan que hay una animación, que percibe un sistema de interfaz de usuario suave y de flujo.

##### <a name="animation-properties"></a>Propiedades de animación

- Opacidad inicial: 0% para el fundido de salida, 100% para el fundido de salida

- Opacidad final: 100% para el fundido de salida, 0% para el fundido de salida

- Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación

- Estilo de aceleración: seno-InOut

##### <a name="examples"></a>Ejemplos

- Ocultar automáticamente las ventanas de herramientas

- Abrir y cerrar menú

- Transiciones de tabulación de fondo y de primer plano

#### <a name="color-blend-from-a-to-b"></a>Combinación de colores de a a B
Con este patrón, un elemento de la interfaz de usuario cambia de color a al color B.

![Animación de Blend de color](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animación de Blend de color

##### <a name="correct-usage"></a>Uso correcto
Como una transición animada cuando un elemento de la interfaz de usuario cambia de color de un contexto o de un estado a otro.

##### <a name="animation-properties"></a>Propiedades de animación

- Color inicial: específico de la interfaz de usuario

- Color final: específico de la interfaz de usuario

- Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación

- Estilo de aceleración: seno-InOut

##### <a name="examples"></a>Ejemplos

- Transiciones de estado de la ventana de documento (activo, último activo e inactivo)

- Transiciones de estado de la ventana de herramientas (con foco y sin foco)

#### <a name="expand-and-contract"></a>Expandir y contraer
Con este patrón, un elemento de la interfaz de usuario se expande en la X, Y, o en ambas direcciones.

![Expandir y animar animación](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Expandir y animar animación

##### <a name="correct-usage"></a>Uso correcto
Como una transición animada cuando un elemento de la interfaz de usuario cambia el tamaño de un contexto a otro.

##### <a name="animation-properties"></a>Propiedades de animación

- X Scale:% o dimensión específica (en píxeles)

- Escala Y:% o dimensión específica (en píxeles)

- Posición del delimitador: generalmente superior izquierda (para los idiomas de izquierda a derecha) o superior derecha (para los idiomas de derecha a izquierda)

- Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación

##### <a name="examples"></a>Ejemplos

- Expandir y contraer panel del explorador de arquitectura

- Expandir y contraer el elemento de página principal de Visual Studio 2017

#### <a name="x-y-position-change"></a>Cambio de posición de X-Y
Con este patrón, un elemento de la interfaz de usuario cambia su posición X o Y, o ambos.

![Animación de cambio de posición de X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animación de cambio de posición de X-Y

##### <a name="correct-usage"></a>Uso correcto
Como una transición animada cuando un elemento de la interfaz de usuario cambia la posición de un contexto a otro.

##### <a name="animation-properties"></a>Propiedades de animación

- Posición X e y inicial: específica de la interfaz de usuario

- Posición X e y final: específico de la interfaz de usuario

- Guía de movimiento: ninguno

- Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación

- Estilo de aceleración: seno-InOut

##### <a name="example"></a>Ejemplo
Reordenación de pestañas

#### <a name="rotate"></a>Girar
Con este patrón, el elemento de la interfaz de usuario gira.

![Animación de rotación de elementos de IU](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animación de rotación de elementos de IU

##### <a name="correct-usage"></a>Uso correcto
Solo para el indicador de progreso de giro indeterminado.

##### <a name="animation-properties"></a>Propiedades de animación

- Grado de rotación: 360

- Centro de rotación: centro del objeto

- Duración: continua

##### <a name="example"></a>Ejemplo
Indicador de progreso indeterminado (giro)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Acciones de interfaz de usuario de Shell comunes y animaciones recomendadas

#### <a name="tab-open"></a>Pestaña abierta
![Animación abierta de pestañas](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animación abierta de pestañas

- Estilo: aparece

- Duración: cero segundos

#### <a name="tab-close"></a>Cierre de pestaña
![Animación de cierre de pestaña](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animación de cierre de pestaña

- Estilo: cambio de posición X

- Duración: 200 milisegundos

#### <a name="tab-reorder"></a>Reordenación de pestañas
![Animación de reorganización de pestañas en Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animación de reordenación de pestañas

- Estilo: cambio de posición X

- Duración: 200 milisegundos

#### <a name="close-floating-document"></a>Cerrar documento flotante
![Cerrar animación de documento flotante](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Cerrar animación de documento flotante

- Estilo: aparece

- Duración: 200 milisegundos

#### <a name="window-state-transition"></a>Transición de estado de ventana
![Animación de transición de estado de ventana](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animación de transición de estado de ventana

- Estilo: para que sea coherente con otras ventanas, permita que el sistema operativo actual defina la animación de cierre del documento.

- Duración: 200 milisegundos

#### <a name="menu-open"></a>Menú abierto
![Animación de apertura de menú](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animación de apertura de menú

- Estilo: fundido de aparición

- Duración: 200 milisegundos

#### <a name="menu-close"></a>Cerrar menú
![Animación de cierre de menú](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animación de cierre de menú

- Estilo: fundido de salida

- Duración: 200 milisegundos

#### <a name="auto-hide-tool-window-reveal"></a>Mostrar ventana de herramientas de ocultación automática
![Ventana de herramientas de ocultación automática mostrar animación](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Ventana de herramientas de ocultación automática mostrar animación

- Estilo: aparece

- Duración: cero segundos
