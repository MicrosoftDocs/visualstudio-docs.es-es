---
title: Animaciones para Visual Studio | Microsoft Docs
description: Obtenga información sobre las reglas que ayudan a garantizar estilos de animación coherentes y fáciles de usar en Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f1e8e61e5decea326fcb7f670ed2ab58f0137530
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902792"
---
# <a name="animations-for-visual-studio"></a>Animaciones para Visual Studio
## <a name="animation-fundamentals"></a>Aspectos básicos de la animación

### <a name="animation-best-practices-in-visual-studio"></a>Procedimientos recomendados de animación en Visual Studio
Siga estas reglas para garantizar estilos de animación coherentes y fáciles de usar en Visual Studio IDE.

- **Ser selectivo.** Limite las animaciones a las que sirven para fines específicos.

- **El tiempo y la velocidad son importantes** para garantizar que las transiciones sean rápidas y naturales:

  - Complete las transiciones animadas en un segundo medio (500 milisegundos).

  - Las animaciones que se producirían con frecuencia deben ser lo suficientemente rápidas como para no interrumpir el flujo de trabajo del usuario. Vea la animación en un bucle y ajuste el tiempo hasta que se sienta bien.

  - Las animaciones no deben ser tan rápidas ni tan rápidas que sea difícil de entender, pero no tan lentas que impacienten la realización de la transición.

  - Use el control de tiempo variable para resaltar la importancia. Por ejemplo, cuando se navega por una secuencia de elementos en un diagrama de clases, se aceleran las transiciones entre los elementos y, a continuación, se ralentizan para centrarse en elementos importantes.

- **Use la aceleración no lineal gradual** de un estado a otro, lo que da una sensación de movimiento natural y natural.

- Cuando sea posible, **use una animación sutil al mantener el mouse** para indicar elementos interactivos debajo del mouse.

- Si depende en gran medida de animaciones en las características, proporcione un medio para desactivarlas **localmente** (para todas las características) como opción en el cuadro de diálogo Herramientas > **opciones.**

- **Solo debe producirse una animación a la vez** y transmitir solo un fragmento de información. Más de un objeto que se mueve o intenta transmitir varias cosas puede resultar confuso.

- **La sutilidad es importante.** En la mayoría de los casos, la animación no tiene que exigir atención al usuario para cumplir su propósito. Los cambios sutiles en el tiempo, la secuenciación y el comportamiento pueden afectar significativamente a la percepción y pueden marcar la diferencia entre una animación eficaz e ineficaz.

- Al usar animación para llamar la atención sobre **algo,** asegúrese de que merece la pena interrumpir el entrenamiento de reflexión del usuario.

- **Al mostrar el progreso o el estado a través** de la animación:

  - Deje de mostrar el movimiento de progreso cuando el proceso subyacente no avanza.

  - Distinguir procesos indeterminados de procesos determinados.

  - Asegúrese de que una animación tiene estados de error y finalización identificables.

  - Minimice el uso de animaciones de efecto que muestren el estado y asegúrese de que tienen un valor real proporcionando información adicional de uso real. Algunos ejemplos son los cambios de estado transitorios y las emergencias.

#### <a name="animation-donts"></a>La animación no hace lo siguiente:

- No use movimientos pequeños (movimiento en una superficie pequeña). Prefiere atenuaciones y cambios en lugar de mover objetos.

- No use animaciones que se llevan a cabo en un área grande del patrimonio de pantalla. Independientemente del tamaño, este estilo de animación distrae al usuario.

- No use animaciones no relacionadas con el objeto en el que el usuario está centrado actualmente o con el que interactúa.

- No use animaciones que requieran la interacción del usuario para restablecer el estado, como forzar al usuario a responder a una notificación intermitente para que deje de parpadear. Interactuar con ellos de cualquier manera debe ser suficiente para descartarlos.

Para obtener más información sobre las aplicaciones para estos procedimientos [recomendados,](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)vea Patrones de animación .

### <a name="animation-metrics"></a>Métricas de animación

- El sistema debe reaccionar visiblemente a los gestos del usuario en menos de 10 milisegundos.

- Las transiciones animadas no deben tardar más de 500 milisegundos en completarse.

- Una manera de compensar las transiciones que requieren tiempos más largos es separarla en dos partes. Por ejemplo, la primera parte de una animación podría ser el contenedor de contenido vacío (hasta 500 milisegundos), seguido del contenido que se desvanecia en el contenedor (hasta 500 milisegundos).

- Para los tiempos de carga que se pueden calcular, se prefiere un indicador de progreso determinante (indicador de progreso de porcentaje realizado).

- Para los tiempos de carga que no se pueden calcular, es adecuado un indicador ocupado como un cursor o una animación de giro incrustada (indicador de carga o de trabajo).

### <a name="animation-as-communicator"></a>Animación como animación
En Visual Studio interfaz de usuario, la animación solo funciona como una herramienta de comunicación.  Se usa para comunicar una variedad de información, como cambios estructurales en la interfaz de usuario (por ejemplo, cuando se abre o se cierra un menú). La animación puede ayudar a visualizar el comportamiento dependiente del tiempo de sistemas complejos, como la visualización del progreso de la instalación. Las animaciones también se pueden usar para atraer la atención con alertas y notificaciones.

 Las animaciones de la interfaz de usuario suelen funcionar de cuatro maneras: visualizar, atraer la atención, simular y tiempos de respuesta/indicadores de progreso.

#### <a name="visualize"></a>Visualización
La animación puede resaltar la naturaleza tridimensional de los objetos y facilitar a los usuarios la visualización de su estructura espacial. Para ello, es posible que la animación tenga que girar el objeto en un círculo completo, girarlo lentamente hacia atrás y hacia delante, o acercar el objeto y aumentar ligeramente su tamaño para resaltar la suversión o el foco.

Aunque los objetos tridimensionales se pueden mover con el control de usuario, el diseñador debe determinar de antemano (mediante programación o manualmente) cómo animar mejor un movimiento que proporciona una comprensión óptima del objeto. A continuación, el usuario puede activar esta animación programada colocando el cursor sobre el objeto, mientras que los movimientos controlados por el usuario requieren que el usuario entienda cómo manipular el objeto. Limite el movimiento a un solo eje u orientación a la vez; escala, gira o traduce, pero no hace más de una simultáneamente.

La categoría Visualizar incluye los aspectos de los datos, las relaciones, el estado, la estructura, la secuencia y el tiempo.

##### <a name="data"></a>Datos
Ilustra información compleja y variable:

- Desplazarse por visualizaciones de información, como gráficos y gráficos

- Recorrer paso a paso una secuencia, un paseo guiado y paginación

- Llamar a detalles, señalar y resaltar información específica

- Superposición de detalles e información adicional sobre un elemento centrado

- Transformación de una representación estructural u organizativa a otra

- Representación de los cambios a lo largo del tiempo mediante controles deslizantes de tiempo, ruedas de desplazamiento y desplazamiento, y controles de transporte (reproducir, detener y pausar)

##### <a name="relationships"></a>Relaciones

- Ilustra cómo se relacionan los elementos entre sí o qué elementos se relacionan con un elemento determinado.

- Mostrar jerarquías y relaciones de elementos primarios y secundarios o del mismo nivel

- Un elemento genera otro.

- Un elemento se minimiza en otro elemento

- Un elemento tethered a otro

##### <a name="state"></a>State

- Actualizaciones de contenido

- Selección y enfoque del usuario

- Progreso

- Errors

##### <a name="structure"></a>Estructura

- Pivoting the structure on one node (Dinamr la estructura en un nodo)

- Reorientar

- Minimizar y maximizar, o expandir y contraer

##### <a name="sequence"></a>Secuencia

- Secuencia de presentación

- Voltear imágenes

##### <a name="time"></a>Time

- Mostrar el cambio a lo largo del tiempo, el período de tiempo y la difusión en pantalla

- Pasar a la papelera, deshacer y rehacer

- Restauración del estado histórico

#### <a name="attract-attention"></a>Atraer la atención
Si el objetivo es atraer la atención del usuario a un único elemento de varios o para alertar al usuario de la información actualizada, es posible que sea adecuada una animación. Por ejemplo, la página de inicio de la aplicación podría emplear un Tareas iniciales que se desliza en su lugar después de que se cargue la página.

Por regla general, el último elemento en movimiento de la pantalla llama la atención del usuario.  En una serie de elementos animados, la atención del usuario seguirá el último objeto en movimiento.

##### <a name="alert"></a>Alerta

- Alertar al usuario, llamar la atención y mostrar el progreso

- Mostrar que algo se está haciendo correcta o incorrectamente, o mostrar los cambios de progreso o progreso

- Preguntar a los usuarios durante una tarea, como buscar más información en línea o aprender sobre la tarea actual

##### <a name="notifications"></a>Notificaciones

- Alertar al usuario sobre una condición de error

- Interrumpir al usuario para ver si desea atender a otra cosa

- Informe al usuario de que un proceso se ha completado o cambiado, como cuando se completa una descarga.

#### <a name="simulate"></a>Simular
Esta categoría abarca la física y dimensionalidad.

- Ilustra dónde proceden los objetos o a dónde van.

- Expandir y contraer o abrir y cerrar

- Desplazamiento panorámico, desplazamiento y turnos de página

- Apilamiento y ordenación z

- Carrusel y acordeón

- Volteo y rotación de la interfaz de usuario

#### <a name="response-and-progress-indicators"></a>Indicadores de respuesta y progreso
Los indicadores de progreso tienen un par de ventajas importantes:

- Tanto los indicadores de progreso determinados como los indeterminados aseguran al usuario que el sistema no se ha bloqueado y está trabajando en el problema.

- Los indicadores determinados dan al usuario una idea de hasta qué punto avanza la acción, así como la sensación de estar más cerca del final.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Patrones de animación

### <a name="overview"></a>Información general
Las animaciones Visual Studio están diseñadas para servir a una función específica sin que ello impida la productividad del usuario. Por lo general, las animaciones Visual Studio deben ser:

- Pequeño y discreto

- Natural y realista

- Sutil y subdesclado

- Rápido y eficaz

- Relajada, no apurada

En esta ilustración se muestran los estilos de animación que se recomiendan para Visual Studio. Ninguna animación o animaciones sutiles, como la atenuación o la atenuación, son las que se usan con más frecuencia. Hay una aplicación limitada de animaciones de movimiento como expansión y contrato, cambio de posición X e Y y rotación.

![Estilos de animación recomendados para Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Estilos de animación recomendados para Visual Studio

#### <a name="appear-and-disappear"></a>Aparecen y desaparecen
Con este patrón, un elemento cambia de visible a fuera de vista y atrás sin una animación de transición.

![Animación de aparición y desvanecer](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Animación de aparición y desvanecer

##### <a name="correct-usage"></a>Uso correcto
Elementos de interfaz de usuario nuevos que deben aparecer o desaparecer al instante para que el usuario no se distraiga ni se obstruya. Además, las animaciones de movimiento lento se pueden percibir como un arrastre de rendimiento, lo que no se producirá con el estilo de aparecer y desaparecer.

##### <a name="incorrect-usage"></a>Uso incorrecto
Los casos en los que la interfaz de usuario aparece de forma repentina el usuario no tiene idea de lo que ha ocurrido y agregar una animación ayudaría a comprender el contexto.

##### <a name="animation-properties"></a>Propiedades de animación
El retraso de tiempo suele ser de cero segundos.

##### <a name="examples"></a>Ejemplos
- Ocultar automáticamente las ventanas de herramientas

- Interfaz de usuario del editor activada con teclado, como IntelliSense y La Ayuda de parámetros

- Expandir y contraer regiones de código

#### <a name="fade-in-and-fade-out"></a>Atenuación y atenuación
Con este patrón, un elemento de la interfaz de usuario pasa de no visible (0 % de opacidad) a visible (opacidad del 100 %) o viceversa.

![Animación de atenuación y atenuación](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animación de atenuación y atenuación

##### <a name="correct-usage"></a>Uso correcto
Esta es la animación de interfaz de usuario más recomendada. Es un efecto sutil que agrega interés sin interrumpir el flujo. En algunos casos, es posible que el usuario ni siquiera se dé cuenta de que hay una animación, lo que da lugar a un sistema de interfaz de usuario fluida y fluida.

##### <a name="animation-properties"></a>Propiedades de animación

- Opacidad inicial: 0 % para atenuación, 100 % para atenuación

- Opacidad final: 100 % para atenuación, 0 % para atenuación

- Duración: 200 milisegundos independientes, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación

- Estilo de aceleración: Sine InOut

##### <a name="examples"></a>Ejemplos

- Ocultar automáticamente las ventanas de herramientas

- Menú abrir y cerrar

- Transiciones de pestañas en segundo plano y en primer plano

#### <a name="color-blend-from-a-to-b"></a>Combinación de colores de A a B
Con este patrón, un elemento de la interfaz de usuario cambia del color A al color B.

![Animación de combinación de colores](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animación de combinación de colores

##### <a name="correct-usage"></a>Uso correcto
Como transición animada cuando un elemento de la interfaz de usuario cambia de un contexto o estado a otro.

##### <a name="animation-properties"></a>Propiedades de animación

- Color inicial: específico de la interfaz de usuario

- Color final: específico de la interfaz de usuario

- Duración: 200 milisegundos independientes, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación

- Estilo de aceleración: Sine InOut

##### <a name="examples"></a>Ejemplos

- Transiciones de estado de ventana de documento (activa, última activa e inactiva)

- Transiciones de estado de la ventana de herramientas (centradas y sin foco)

#### <a name="expand-and-contract"></a>Expansión y contrato
Con este patrón, un elemento de interfaz de usuario se expande en las direcciones X, Y o ambas.

![Animación de expansión y contrato](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Animación de expansión y contrato

##### <a name="correct-usage"></a>Uso correcto
Como transición animada cuando un elemento de la interfaz de usuario cambia de tamaño de un contexto a otro.

##### <a name="animation-properties"></a>Propiedades de animación

- Escala X: % o dimensión específica (en píxeles)

- Escala Y: % o dimensión específica (en píxeles)

- Posición del delimitador: generalmente superior izquierda (para idiomas de izquierda a derecha) o superior derecha (para idiomas de derecha a izquierda)

- Duración: 200 milisegundos independientes, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación

##### <a name="examples"></a>Ejemplos

- Expansión y contraer del panel Explorador de arquitectura

- Visual Studio elemento de la página de inicio de 2017 se expande y contrae

#### <a name="x-y-position-change"></a>Cambio de posición X-Y
Con este patrón, un elemento de la interfaz de usuario cambia su posición X o Y o ambas.

![Animación de cambio de posición X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animación de cambio de posición X-Y

##### <a name="correct-usage"></a>Uso correcto
Como transición animada cuando un elemento de la interfaz de usuario cambia de posición de un contexto a otro.

##### <a name="animation-properties"></a>Propiedades de animación

- Posición inicial de X e Y: específica de la interfaz de usuario

- Posición X e Y final: específica de la interfaz de usuario

- Ruta de movimiento: ninguna

- Duración: 200 milisegundos independientes, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación

- Estilo de aceleración: Sine InOut

##### <a name="example"></a>Ejemplo
Reordenación de pestañas

#### <a name="rotate"></a>Girar
Con este patrón, el elemento de la interfaz de usuario gira.

![Animación de rotación de elementos de la interfaz de usuario](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animación de rotación de elementos de la interfaz de usuario

##### <a name="correct-usage"></a>Uso correcto
Solo para el indicador de progreso de giro indeterminado.

##### <a name="animation-properties"></a>Propiedades de animación

- Grado de rotación: 360

- Centro de rotación: centro del objeto

- Duración: continua

##### <a name="example"></a>Ejemplo
Indicador de progreso indeterminado (giro)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Acciones comunes de la interfaz de usuario de shell y animaciones recomendadas

#### <a name="tab-open"></a>Pestaña abierta
![Animación abierta con tabulación](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animación abierta con tabulación

- Estilo: aparecen

- Duración: cero segundos

#### <a name="tab-close"></a>Cierre de tabulación
![Animación de cierre de tabulación](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animación de cierre de tabulación

- Estilo: cambio de posición X

- Duración: 200 milisegundos

#### <a name="tab-reorder"></a>Reordenación de tabulación
![Animación de reorganización de pestañas en Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animación de reordenación de tabulación

- Estilo: cambio de posición X

- Duración: 200 milisegundos

#### <a name="close-floating-document"></a>Cerrar documento flotante
![Cerrar animación de documentos flotantes](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Cerrar animación de documentos flotantes

- Estilo: aparecen

- Duración: 200 milisegundos

#### <a name="window-state-transition"></a>Transición de estado de ventana
![Animación de transición de estado de ventana](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animación de transición de estado de ventana

- Estilo: para ser coherente con otras ventanas, permita que el sistema operativo actual defina la animación de cierre del documento.

- Duración: 200 milisegundos

#### <a name="menu-open"></a>Menú abierto
![Animación de apertura de menú](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animación de apertura de menú

- Estilo: atenuación

- Duración: 200 milisegundos

#### <a name="menu-close"></a>Menú cerrar
![Animación de cierre de menú](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animación de cierre de menú

- Estilo: atenuación

- Duración: 200 milisegundos

#### <a name="auto-hide-tool-window-reveal"></a>Mostrar ventana de herramientas ocultar automáticamente
![Ocultar automáticamente la ventana de herramientas mostrar animación](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Ocultar automáticamente la ventana de herramientas mostrar animación

- Estilo: aparecen

- Duración: cero segundos
