---
title: Animaciones para Visual Studio ( Visual Studio) Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc11eb7bab69728be5ceaa55143f56e93cd1fca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698602"
---
# <a name="animations-for-visual-studio"></a>Animaciones para Visual Studio
## <a name="animation-fundamentals"></a>Fundamentos de la animación

### <a name="animation-best-practices-in-visual-studio"></a>Prácticas recomendadas de animación en Visual Studio
Siga estas reglas para garantizar estilos de animación coherentes y fáciles de usar en el IDE de Visual Studio.

- **Sé selectivo.** Limite las animaciones a aquellas que sirvan a propósitos específicos.

- **El tiempo y la velocidad son importantes** para garantizar que las transiciones se sientan rápidas y naturales:

  - Completa transiciones animadas en medio segundo (500 milisegundos).

  - Las animaciones que se producirían con frecuencia deben ser lo suficientemente rápidas como para que no interrumpan el flujo de trabajo del usuario. Mira la animación en un bucle y ajusta el tiempo hasta que se sienta bien.

  - Las animaciones no deben ser tan rápidas o inquietantes que es difícil de entender, pero no tan lentas que hace que un impaciente para la transición termine.

  - Utilice el tiempo variable para enfatizar la importancia. Por ejemplo, al navegar por una secuencia de elementos en un diagrama de clases, acelere las transiciones entre elementos y, a continuación, reduzca la velocidad para centrarse en los elementos importantes.

- Utilice la **flexión no lineal gradual** de un estado a otro, dando una sensación de calma y movimiento natural.

- Cuando sea posible, **utilice una animación sutil al pasar el ratón** para indicar elementos interactivos debajo del ratón.

- Si depende en gran medida de las animaciones de las entidades, **proporcione un medio para desactivarlas** localmente (para todas las entidades) como una opción en el cuadro de diálogo Herramientas > **opciones.**

- **Solo debe producirse una animación** a la vez y transmitir solo una información. Más de un objeto que se mueve o intenta transmitir varias cosas puede ser confuso.

- **La sutileza es importante.** En la mayoría de los casos, la animación no tiene que exigir la atención del usuario para cumplir su propósito. Los cambios sutiles en el tiempo, la secuenciación y el comportamiento pueden afectar significativamente a la percepción y pueden marcar la diferencia entre una animación eficaz e ineficaz.

- Cuando utilice sanimación para llamar la atención sobre algo, asegúrese de que vale la pena interrumpir el tren de pensamiento del **usuario.**

- **Al mostrar el progreso o el estado** a través de la animación:

  - Deje de mostrar el movimiento de progreso cuando el proceso subyacente no avance.

  - Distinguir los procesos indeterminados de los procesos determinados.

  - Asegúrese de que una animación tiene estados identificables de finalización y error.

  - Minimice el uso de animaciones de efectos que muestren el estado y asegúrese de que tienen valor real proporcionando información adicional de uso real. Algunos ejemplos son los cambios de estado transitorios y las emergencias

#### <a name="animation-donts"></a>Animación no:

- No utilice movimientos pequeños (movimiento en una huella pequeña). Prefiere fundidos y cambios sobre objetos en movimiento.

- No utilice animaciones que tienen lugar en una gran área de bienes raíces de pantalla. Independientemente del tamaño, este estilo de animación distrae al usuario.

- No utilice animaciones no relacionadas con el objeto en el que el usuario está centrado o con el que interactúa.

- No utilice animaciones que requieran la interacción del usuario para restablecer el estado, como forzar al usuario a responder a una notificación parpadeante para que deje de parpadear. Interactuar con ellos de cualquier manera debería ser suficiente para descartarlos.

Para obtener más información sobre las aplicaciones para estas [prácticas recomendadas,](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)consulte Patrones de animación .

### <a name="animation-metrics"></a>Métricas de animación

- El sistema debe reaccionar visiblemente a los gestos del usuario en menos de 10 milisegundos.

- Las transiciones animadas no deben tardar más de 500 milisegundos en completarse.

- Una forma de compensar las transiciones que requieren tiempos más largos es separarlas en dos partes. Por ejemplo, la primera parte de una animación podría ser el contenedor de contenido vacío (hasta 500 milisegundos), seguido del contenido que se desvanece en el contenedor (hasta 500 milisegundos).

- Para los tiempos de carga que se pueden calcular, se prefiere un indicador de progreso determinante (indicador de progreso porcentual hecho).

- Para los tiempos de carga que no se pueden calcular, un indicador ocupado como un cursor o una animación de giro incrustada (indicador de carga o de trabajo) es adecuado.

### <a name="animation-as-communicator"></a>Animación como comunicador
En la interfaz de usuario de Visual Studio, la animación solo funciona como una herramienta de comunicación.  Se usa para comunicar una variedad de información, como cambios estructurales en la interfaz de usuario (por ejemplo, cuando se abre o se cierra un menú). La animación puede ayudar a visualizar el comportamiento dependiente del tiempo de sistemas complejos, como la visualización del progreso de la instalación. Las animaciones también se pueden utilizar para atraer la atención con alertas y notificaciones.

 Las animaciones de la interfaz de usuario suelen funcionar de cuatro maneras: visualizar, atraer la atención, simular y los indicadores de tiempos de respuesta/progreso.

#### <a name="visualize"></a>Visualizar
La animación puede enfatizar la naturaleza tridimensional de los objetos y facilitar a los usuarios la visualización de su estructura espacial. Para lograr esto, la animación puede necesitar girar el objeto en un círculo completo, girarlo lentamente hacia adelante y hacia atrás, o acercar el objeto y aumentar ligeramente su tamaño para enfatizar el rollover o el enfoque.

Aunque los objetos tridimensionales se pueden mover con el control de usuario, el diseñador debe determinar de antemano (mediante programación o manualmente) cómo animar mejor un movimiento que proporciona una comprensión óptima del objeto. Esta animación programada puede ser activada por el usuario colocando el cursor sobre el objeto, mientras que los movimientos controlados por el usuario requieren que el usuario entienda cómo manipular el objeto. Limitar el movimiento a un solo eje u orientación a la vez; escala, gira o traduce, pero no hagas más de uno simultáneamente.

La categoría Visualizar incluye los aspectos de los datos, las relaciones, el estado, la estructura, la secuencia y el tiempo.

##### <a name="data"></a>data
Ilustrar información compleja y variable:

- Moverse a través de visualizaciones de información como gráficos y gráficos

- Paso a través de una secuencia, visita guiada y paginación

- Llamar a los detalles, señalar y resaltar información específica

- Superposición de detalles e información adicional sobre un elemento enfocado

- Morphing de una representación estructural o organizativa a otra

- Representación de los cambios a lo largo del tiempo mediante controles deslizantes de tiempo, ruedas jog-and-shuttle y controles de transporte (reproducir, detener y pausar)

##### <a name="relationships"></a>Relaciones

- Ilustrar cómo se relacionan entre sí los elementos o qué elementos se relacionan con un elemento determinado

- Mostrar jerarquías y relaciones padre-hijo o hermano

- Un elemento genera otro

- Un elemento se minimiza a otro elemento

- Un elemento atado a otro

##### <a name="state"></a>State

- Actualizaciones de contenido

- Enfoque y selección del usuario

- Progreso

- Errors

##### <a name="structure"></a>Estructura

- Pivotar la estructura en un nodo

- Reorientar

- Minimizar y maximizar, o expandir y contraer

##### <a name="sequence"></a>Secuencia

- Secuencia de presentación de diapositivas

- Voltear a través de las imágenes

##### <a name="time"></a>Time

- Mostrar cambio con el tiempo, lapso de tiempo y screencast

- Muévete a la basura, rehacer y rehacer

- Restaurar estado histórico

#### <a name="attract-attention"></a>Atraer la atención
Si el objetivo es atraer la atención del usuario a un solo elemento de varios o alertar al usuario de información actualizada, entonces una animación podría ser adecuada. Por ejemplo, la página de inicio de la aplicación podría emplear un botón de introducción que se desliza en su lugar después de que se cargue la página.

Como regla general, el último elemento en movimiento en la pantalla atrae la atención del usuario.  En una serie de elementos animados, la atención del usuario seguirá el último objeto en movimiento.

##### <a name="alert"></a>Alerta

- Alertar al usuario, llamar la atención, mostrar el progreso

- Mostrar que algo se está haciendo correctamente o incorrectamente o mostrar cambios de progreso o progreso

- Preguntar a los usuarios durante una tarea, como encontrar más información en línea o aprender sobre la tarea actual

##### <a name="notifications"></a>Notificaciones

- Alertar al usuario sobre una condición de error

- Interrumpir al usuario para ver si le gustaría atender a otra cosa

- Informar suavemente al usuario de que un proceso se ha completado o cambiado, como cuando se completa una descarga.

#### <a name="simulate"></a>Simular
Esta categoría abarca la física y la dimensionalidad.

- Ilustrar de dónde vienen los objetos o a dónde van

- Expandir y contraer o abrir y cerrar

- Panorámica, desplazamiento y vueltas de página

- Apilamiento y ordenamiento en z

- Carrusel y acordeón

- Voltear y rotar la interfaz de usuario

#### <a name="response-and-progress-indicators"></a>Indicadores de respuesta y progreso
Los indicadores de progreso tienen un par de ventajas notables:

- Los indicadores de progreso determinados e indeterminados aseguran al usuario que el sistema no se ha bloqueado y está trabajando en el problema.

- Los indicadores determinados dan al usuario una idea de lo lejos que avanza la acción, así como una sensación de acercarse al final.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a>Patrones de animación

### <a name="overview"></a>Información general
Las animaciones en Visual Studio están diseñadas para servir a una función específica sin obstaculizar la productividad del usuario. Por lo general, las animaciones en Visual Studio deben ser:

- Pequeño y discreto

- Natural y realista

- Sutil y tenue

- Rápido y eficiente

- Relajado, no apresurado

En esta ilustración se muestran los estilos de animación que se recomiendan para Visual Studio. Ninguna animación o animaciones sutiles como fade in/fade out son las más utilizadas. Hay una aplicación limitada de animaciones de movimiento como expandir y contraer, cambio de posición X e Y, y rotación.

![Estilos de animación recomendados para Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Estilos de animación recomendados para Visual Studio

#### <a name="appear-and-disappear"></a>Aparecen y desaparecen
Con este patrón, un elemento cambia de visible a fuera de vista y hacia atrás sin una animación de transición.

![Aparece y desaparece la animación](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Aparece y desaparece la animación

##### <a name="correct-usage"></a>Uso correcto
Elementos de interfaz de usuario frescos que necesitan aparecer o desaparecer al instante para que el usuario no esté distraído ni obstruido. Además, las animaciones de movimiento lento pueden percibirse como un arrastre de rendimiento, lo que no se producirá con el estilo de aparecer y desaparecer.

##### <a name="incorrect-usage"></a>Uso incorrecto
Casos en los que la interfaz de usuario aparece tan abruptamente el usuario no tiene idea de lo que sucedió, y agregar una animación ayudaría con la comprensión contextual.

##### <a name="animation-properties"></a>Propiedades de animación
El retardo de tiempo es generalmente cero segundos.

##### <a name="examples"></a>Ejemplos
- Ocultar automáticamente las ventanas de herramientas

- Interfaz de usuario del editor activado por teclado, como IntelliSense y la Ayuda de parámetros

- Expandir y contraer regiones de código

#### <a name="fade-in-and-fade-out"></a>Fade-in y fade-out
Con este patrón, un elemento de interfaz de usuario pasa de no visible (0% de opacidad) a visible (100% de opacidad) o viceversa.

![Animación fade-in y fade-out](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animación fade-in y fade-out

##### <a name="correct-usage"></a>Uso correcto
Esta es la animación de interfaz de usuario más comúnmente recomendada. Es un efecto sutil que añade interés sin interrumpir el flujo. En algunos casos, es posible que el usuario ni siquiera se dé cuenta de que hay una animación, al percibir un sistema de interfaz de usuario fluido y fluido.

##### <a name="animation-properties"></a>Propiedades de animación

- Opacidad inicial: 0% para fade-in, 100% para fade-out

- Opacidad final: 100% para fade-in, 0% para fade-out

- Duración: 200 milisegundos independientes, 100 milisegundos cuando se utiliza como parte de una secuencia de animación de combinación

- Estilo de adelanto: Sine InOut

##### <a name="examples"></a>Ejemplos

- Ocultar automáticamente las ventanas de herramientas

- Menú abierto y cerrado

- Transiciones de pestañas en primer plano y en segundo plano

#### <a name="color-blend-from-a-to-b"></a>Mezcla de colores de A a B
Con este patrón, un elemento de interfaz de usuario cambia de color A a color B.

![Animación de mezcla de colores](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animación de mezcla de colores

##### <a name="correct-usage"></a>Uso correcto
Como transición animada cuando un elemento de interfaz de usuario cambia de color de un contexto o estado a otro.

##### <a name="animation-properties"></a>Propiedades de animación

- Color inicial: específico de la interfaz de usuario

- Color final: específico de la interfaz de usuario

- Duración: 200 milisegundos independientes, 100 milisegundos cuando se utiliza como parte de una secuencia de animación de combinación

- Estilo de adelanto: Sine InOut

##### <a name="examples"></a>Ejemplos

- Transiciones de estado de la ventana de documento (activa, última activa e inactiva)

- Transiciones de estado de la ventana de herramientas (enfocadas y desenfocadas)

#### <a name="expand-and-contract"></a>Expandir y contratar
Con este patrón, un elemento de interfaz de usuario se expande en las direcciones X, Y o ambas direcciones.

![Expandir y contraer animación](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Expandir y contraer animación

##### <a name="correct-usage"></a>Uso correcto
Como transición animada cuando un elemento de interfaz de usuario cambia de tamaño de un contexto a otro.

##### <a name="animation-properties"></a>Propiedades de animación

- Escala X: % o dimensión específica (en píxeles)

- Escala Y: % o dimensión específica (en píxeles)

- Posición de anclaje: generalmente superior izquierda (para idiomas de izquierda a derecha) o superior derecha (para idiomas de derecha a izquierda)

- Duración: 200 milisegundos independientes, 100 milisegundos cuando se utiliza como parte de una secuencia de animación de combinación

##### <a name="examples"></a>Ejemplos

- El panel Explorador de arquitectura se expande y contrae

- Visual Studio 2017 Elemento de página de inicio expandir y contraer

#### <a name="x-y-position-change"></a>Cambio de posición X-Y
Con este patrón, un elemento de interfaz de usuario cambia su posición X o Y o ambas.

![Animación de cambio de posición X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animación de cambio de posición X-Y

##### <a name="correct-usage"></a>Uso correcto
Como transición animada cuando un elemento de interfaz de usuario cambia de posición de un contexto a otro.

##### <a name="animation-properties"></a>Propiedades de animación

- Inicio de la posición X e Y: específico de la interfaz de usuario

- Posición De terminación X e Y: específica de la interfaz de usuario

- Ruta de movimiento: ninguno

- Duración: 200 milisegundos independientes, 100 milisegundos cuando se utiliza como parte de una secuencia de animación de combinación

- Estilo de adelanto: Sine InOut

##### <a name="example"></a>Ejemplo
Reordenación de pestañas

#### <a name="rotate"></a>Girar
Con este patrón, el elemento de interfaz de usuario gira.

![Animación de rotación de elementos de interfaz de usuario](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animación de rotación de elementos de interfaz de usuario

##### <a name="correct-usage"></a>Uso correcto
Sólo para el indicador de progreso de giro indeterminado.

##### <a name="animation-properties"></a>Propiedades de animación

- Grado de rotación: 360

- Centro de rotación: centro del objeto

- Duración: continua

##### <a name="example"></a>Ejemplo
Indicador de progreso indeterminado (giro)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Acciones comunes de la interfaz de usuario del shell y animaciones recomendadas

#### <a name="tab-open"></a>Pestaña abierta
![Animación abierta de pestañas](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animación abierta de pestañas

- Estilo: aparece

- Duración: cero segundos

#### <a name="tab-close"></a>Cierre de pestañas
![Animación de cierre de pestaña](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animación de cierre de pestaña

- Estilo: Cambio de posición X

- Duración: 200 milisegundos

#### <a name="tab-reorder"></a>Reorden de pestañas
![Animación de reorganización de pestañas en Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animación de reordenación de pestañas

- Estilo: Cambio de posición X

- Duración: 200 milisegundos

#### <a name="close-floating-document"></a>Cerrar documento flotante
![Cerrar animación de documento flotante](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Cerrar animación de documento flotante

- Estilo: aparece

- Duración: 200 milisegundos

#### <a name="window-state-transition"></a>Transición del estado de la ventana
![Animación de transición de estado de ventana](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animación de transición de estado de ventana

- Estilo: para ser coherente con otras ventanas, deje que el sistema operativo actual defina la animación de cierre del documento.

- Duración: 200 milisegundos

#### <a name="menu-open"></a>Menú abierto
![Menú de animación abierta](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Menú de animación abierta

- Estilo: fade-in

- Duración: 200 milisegundos

#### <a name="menu-close"></a>Menú cerrado
![Menú cerrar animación](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Menú cerrar animación

- Estilo: fade-out

- Duración: 200 milisegundos

#### <a name="auto-hide-tool-window-reveal"></a>La ventana de herramientas de ocultación automática revela
![La ventana de herramientas de ocultación automática revela la animación](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />La ventana de herramientas de ocultación automática revela la animación

- Estilo: aparece

- Duración: cero segundos
