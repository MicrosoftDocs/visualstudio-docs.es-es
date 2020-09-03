---
title: Animaciones
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c07fb0887ae01ec917b39f5d7537d5a78fb5a4c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825354"
---
# <a name="animations-for-visual-studio"></a>Animaciones para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Aspectos básicos de la animación

### <a name="animation-best-practices-in-visual-studio"></a>Procedimientos recomendados de animación en Visual Studio
 Siga estas reglas para garantizar que los estilos de animación sean coherentes y fáciles de ver en el IDE de Visual Studio.

- **Ser selectivo.** Limite las animaciones a las que sirven para fines específicos.

- La **temporización y la velocidad son importantes** para asegurarse de que las transiciones se sienten rápidas y naturales:

  - Completar transiciones animadas en un plazo de medio segundo (500 milisegundos).

  - Las animaciones que se producen con frecuencia deben ser lo suficientemente rápidas como para que no interrumpan el flujo de trabajo del usuario.

  - Las animaciones no deben ser tan rápidas o discordante que resulte difícil de entender, pero no tan lenta que hace que sea un paciente para finalizar la transición.

  - Utilice el control de tiempo variable para enfatizar la importancia. Por ejemplo, al desplazarse por una secuencia de elementos de un diagrama de clases, la velocidad de las transiciones entre los elementos se ralentiza para centrarse en elementos importantes.

- **Usar aceleración no lineal gradual** de un estado a otro, lo que aporta una idea del movimiento en calma y natural

- Siempre que sea posible, **utilice una animación sutil de Hover** para indicar elementos interactivos bajo el mouse.

- Si confía en gran medida en las animaciones de sus características, **proporcione un medio para** desactivarlas localmente (para todas las características) como una opción en el cuadro de diálogo **herramientas > opciones** .

- **Solo se debe realizar una animación cada vez** y transmitir solo una parte de la información.

- **El detalle es importante.** En la mayoría de los casos, la animación no tiene que solicitar la atención del usuario para atender su finalidad. Los cambios sutiles en el tiempo, la secuenciación y el comportamiento pueden afectar de forma significativa a la percepción y pueden hacer la diferencia entre una animación efectiva e ineficaz.

- Al usar animaciones para atraer la atención a algo, asegúrese de **que merece la pena interrumpir el**entrenamiento del usuario.

- **Al mostrar el progreso o el estado** a través de la animación:

  - Dejar de mostrar el movimiento de progreso cuando el proceso subyacente no avanza.

  - Distinga los procesos indeterminados de los procesos determinan.

  - Asegúrese de que una animación tenga Estados de finalización e identificación de errores.

  - Minimice el uso de animaciones de efectos que muestren el estado y asegúrese de que tienen un valor real proporcionando información adicional del uso real. Algunos ejemplos son los cambios de estado transitorios y las emergencias

#### <a name="do-not"></a>No:

- Usar movimientos pequeños (movimiento en una superficie pequeña), preduciendo los fundidos y los cambios en el movimiento de objetos.

- Usar animaciones que tienen lugar en un área grande de espacio real de la pantalla. Independientemente del tamaño, este estilo de animación distrae al usuario.

- Use animaciones que no estén relacionadas con el objeto al que el usuario se centra actualmente o con el que interactúa.

- Use animaciones que requieran la interacción del usuario para restablecer el estado, como obligar al usuario a responder a una notificación en parpadeo para que se detenga el parpadeo. Interactuar con ellos de cualquier manera debe ser suficiente para descartarlos.

  Para obtener más información sobre las aplicaciones de estas prácticas recomendadas, consulte [patrones de animación](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Métricas de animación

- El sistema debe reaccionar de manera visible a los gestos del usuario en menos de 10 milisegundos.

- Las transiciones animadas no deben tardar más de 500 milisegundos en completarse.

- Una manera de compensar las transiciones que requieren más tiempo es separarlas en dos partes: por ejemplo, la primera parte de una animación podría ser el contenedor de contenido vacío (hasta 500 milisegundos) seguido del contenido fundido en el contenedor (hasta 500 milisegundos).

- En el caso de los tiempos de carga que se pueden calcular, se prefiere un indicador de progreso determinante (indicador de progreso por porcentaje completado).

- En el caso de los tiempos de carga que no se pueden calcular, es adecuado un indicador de ocupado como un cursor o una animación giratoria incrustada (carga o indicador de trabajo).

### <a name="animation-as-communicator"></a>Animación como Communicator
 En la interfaz de usuario de Visual Studio, la animación funciona solo como una herramienta de comunicación.  Se usa para comunicar una gran variedad de información, como cambios estructurales en la interfaz de usuario; por ejemplo, cuando se abre o se cierra un menú. La animación puede ayudarle a visualizar el comportamiento dependiente del tiempo de sistemas complejos, como la visualización del progreso de la instalación o el uso para atraer la atención con alertas y notificaciones.

 Las animaciones de interfaz de usuario funcionan normalmente de cuatro maneras: visualizar, atraer la atención, simular e indicar los tiempos de respuesta y el progreso.

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

- Representación de los cambios con el tiempo mediante controles deslizantes de tiempo, ruedas de quiebro y lanzadera y controles de transporte (reproducir, detener y pausar).

##### <a name="relationships"></a>Relaciones

- Muestra cómo se relacionan los elementos entre sí o qué elementos se relacionan con un elemento determinado.

- Mostrar jerarquías y relaciones primario-secundario o del mismo nivel

- Un elemento genera otro

- Un elemento se minimiza en otro elemento

- Un elemento anclado a otro

##### <a name="state"></a>State

- Actualizaciones de contenido.

- Selección y foco del usuario

- Progreso

- Errores

##### <a name="structure"></a>Estructura

- Dinamizar la estructura en un nodo

- Reorientar

- Minimizar y maximizar, o expandir y contraer

##### <a name="sequence"></a>Secuencia

- Secuencia de presentación

- Voltear imágenes

##### <a name="time"></a>Time

- Mostrar cambio con el tiempo, lapso de tiempo y screencast

- Moverse a la papelera, deshacer y rehacer

- Restaurar estado histórico

#### <a name="attract-attention"></a>Atraer la atención
 Si el objetivo es atraer la atención del usuario a un solo elemento de varias o para avisar al usuario de la información actualizada, es posible que una animación sea adecuada. Por ejemplo, la página de inicio de las aplicaciones puede emplear un botón Introducción que se desliza en el lugar después de que se cargue la página.

 Como regla, el último elemento que se mueve en la pantalla atrae la atención del usuario.  En una serie de elementos animados, la atención del usuario seguirá el último objeto que se mueve.

##### <a name="alert"></a>Alerta

- Avisar al usuario, prestar atención, mostrar el progreso

- Mostrar que algo se realiza correctamente o de forma incorrecta, o que muestra cambios de progreso o progreso

- Preguntar a los usuarios durante una tarea, como buscar más información en línea o aprender sobre la tarea actual

##### <a name="notifications"></a>Notificaciones

- Alertar al usuario sobre una condición de error

- Interrumpir al usuario para ver si desea asistir a otra cosa

- Informe suavemente al usuario de que un proceso se ha completado o cambiado, por ejemplo, cuando se completa una descarga.

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
 Las animaciones en Visual Studio están diseñadas para servir una función específica y no obstaculizar la productividad de los usuarios. Las características de animación generales que se deben cumplir incluyen:

- Pequeño y discreto

- Natural y realista

- Sutil y subdued

- Rápida y eficaz

- Relajado, no hurried

  En la ilustración siguiente se muestran los estilos de animación recomendados para su uso en Visual Studio. No se usa con más frecuencia ninguna animación ni animaciones sutiles, como atenuar o atenuar. Hay una aplicación limitada de animaciones de movimiento, como la expansión y el contrato, el cambio de posición X e y y la rotación.

  ![Estilos de animación recomendados para Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202-a_VSAnimStyles")

  **Estilos de animación recomendados para Visual Studio**

#### <a name="appear-and-disappear"></a>Aparecen y desaparecen
 Con este patrón, un elemento cambia de visible a no vista y atrás sin una animación de transición:

 ![Aparecen&#47;animación desaparecer en Visual Studio](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202-b_AppearAndDisappear")

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
 Con este patrón, un elemento de la interfaz de usuario realiza una transición de no visible (0% de opacidad) a visible (opacidad del 100%) o viceversa:

 ![Atenuar&#45;en&#47;atenuación de la animación de la&#45;en Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202-c_FadeInFadeOut")

##### <a name="correct-usage"></a>Uso correcto
 Esta es la animación de IU recomendada más comúnmente. Es un efecto sutil que agrega interés sin interrumpir el flujo. En algunos casos, es posible que el usuario no tenga en cuentan que hay una animación y simplemente percibe un sistema de interfaz de usuario fluido.

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
 Con este patrón, un elemento de la interfaz de usuario cambia de color a al color B:

 ![Animación de mezcla de colores en Visual Studio](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202-d_ColorBlend")

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
 Con este patrón, un elemento de la interfaz de usuario se expande en la X, Y, o en ambas direcciones:

 ![Expandir&#47;animación de contrato en Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202-e_ExpandContract")

##### <a name="correct-usage"></a>Uso correcto
 Como una transición animada cuando un elemento de la interfaz de usuario cambia el tamaño de un contexto a otro.

##### <a name="animation-properties"></a>Propiedades de animación

- X Scale:% o dimensión específica (en píxeles)

- Escala Y:% o dimensión específica (en píxeles)

- Posición del delimitador: generalmente superior izquierda (para los idiomas de izquierda a derecha) o superior derecha (para los idiomas de derecha a izquierda)

- Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación

##### <a name="examples"></a>Ejemplos

- Expandir y contraer panel del explorador de arquitectura

- Expandir y contraer elementos de la Página principal

#### <a name="x-y-position-change"></a>Cambio de posición de X-Y
 Con este patrón, un elemento de la interfaz de usuario cambia su posición X o Y o ambas:

 ![Animación de cambio de posición X&#47;Y en Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202-f_XYPositionChange")

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
 Con este patrón, el elemento de la interfaz de usuario gira:

 ![Animación de giro en Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202-g_Rotate")

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

- Estilo: aparece

- Duración: cero segundos

  ![Animación de apertura de pestaña en Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202-h_TabOpen")

#### <a name="tab-close"></a>Cierre de pestaña

- Estilo: cambio de posición X

- Duración: 200 milisegundos

  ![Animación de cierre de pestaña en Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202-i_TabClose")

#### <a name="tab-reorder"></a>Reordenación de pestañas

- Estilo: cambio de posición X

- Duración: 200 milisegundos

  ![Animación de reorganización de pestañas en Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202-j_TabReorder")

#### <a name="close-floating-document"></a>Cerrar documento flotante

- Estilo: aparece

- Duración: 200 milisegundos

  ![Animación de cierre de documento flotante en Visual Studio](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202-k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Transición de estado de ventana

- Estilo: para que sea coherente con otras ventanas, permita que el sistema operativo actual defina la animación de cierre del documento.

- Duración: 200 milisegundos

  ![Animación de transición de estado de ventana en Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202-l_WindowStateTransition")

#### <a name="menu-open"></a>Menú abierto

- Estilo: fundido de aparición

- Duración: 200 milisegundos

  ![Animación de apertura de menú en Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202-m_MenuOpen")

#### <a name="menu-close"></a>Cerrar menú

- Estilo: fundido de salida

- Duración: 200 milisegundos

  ![Animación de cierre de menú en Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202-n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Mostrar ventana de herramientas de ocultación automática

- Estilo: aparece

- Duración: cero segundos

  ![&#45;automática ocultar la animación de la ventana de herramientas en Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")
