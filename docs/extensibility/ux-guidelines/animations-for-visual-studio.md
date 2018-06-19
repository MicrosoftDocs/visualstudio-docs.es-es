---
title: Las animaciones para Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f28e4d6f9ae1a0af060723047621b3e205d012c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148943"
---
# <a name="animations-for-visual-studio"></a>Animaciones para Visual Studio
## <a name="animation-fundamentals"></a>Aspectos básicos de animación  
  
### <a name="animation-best-practices-in-visual-studio"></a>Prácticas recomendadas de animación en Visual Studio  
Siga estas reglas para asegurarse de estilos de animación coherente y fácil de usar en el IDE de Visual Studio.  
  
-   **Sea selectivo.** Limitar las animaciones a los que se usan con fines específicos.  
  
-   **Control de tiempo y la velocidad están importantes** para asegurarse de que las transiciones sentirse rápido y natural:  
  
    -   Transiciones animadas completadas en un medio segundo (500 milisegundos).  
  
    -   Las animaciones que se producirían con frecuencia deben ser lo suficientemente rápido, por lo que no interrumpen el flujo de trabajo del usuario. Ver la animación en un bucle y ajustar el tiempo hasta que sienta al derecho. 
  
    -   Las animaciones no deben ser tan rápido o discordante que resulta difícil de entender, pero no tan lento que realice una impacienta para la transición al finalizar.  
  
    -   Usar control de tiempo variable para poner de relieve importancia. Por ejemplo, al navegar a través de una secuencia de elementos en un diagrama de clases, acelerar a través de las transiciones entre los elementos, a continuación, ralentizar para centrarse en los elementos importantes.  
  
-   **Usar aceleración no lineal gradual** desde un estado a otro, lo que proporciona una idea de movimiento calma y natural.  
  
-   Cuando sea posible, **usar una animación sutil al mantener el mouse** para indicar elementos interactivos en el mouse.  
  
-   Si dependen en gran medida las animaciones en sus características, a continuación, **proporcionan un medio para desactivarlos temporalmente** localmente (para todas las características) como una opción en el **Herramientas > opciones** cuadro de diálogo.  
  
-   **Solo una animación debe producirse en un momento** y mostrar solo una parte de la información. Más de un objeto de mover o intentar transmitir varias cosas puede resultar confuso. 
  
-   **Detalle es importante.** En la mayoría de los casos, la animación no tiene que requieren atención de usuario para cumplir su propósito. Sutiles cambios en el tiempo, la secuencia y el comportamiento pueden afectar significativamente a percepción y pueden marcar la diferencia entre una animación eficaz e ineficaces.  
  
-   Cuando se usa la animación para llamar la atención sobre algo, **Asegúrese de que merece la pena interrumpir al usuario**del hilo de ideas.  
  
-   **Cuando se muestran el progreso o estado** a través de la animación:  
  
    -   Detener la presentación de movimiento de progreso cuando no avanza el proceso subyacente. 
  
    -   Distinguir procesos indeterminados de procesos determinados.  
  
    -   Asegúrese de que una animación tiene la identificación de los Estados de finalización y de error.  
  
    -   Minimizar el uso de animaciones de efecto que indican el estado y asegúrese de que tienen un valor real al proporcionar información adicional de uso real. Algunos ejemplos son emergencias y cambios de estado transitorio  
  
#### <a name="animation-donts"></a>Acciones de animación:
  
-   No use pequeños movimientos (movimiento en una superficie pequeña). Preferir las fusiones y cambian con el movimiento de objetos.  
  
-   No use las animaciones que se realicen en una gran área de espacio en pantalla. Independientemente del tamaño, este estilo de animación es confuso al usuario.  
  
-   No use las animaciones no está relacionado con el objeto de en que usuario actualmente se centra o interactuar con.  
  
-   No use las animaciones que requieren interacción del usuario para restablecer el estado, como obligar al usuario a responder a una notificación para que sea deja de parpadear intermitente. Interactuar con ellos en ningún modo debería ser suficiente para descartar en ellos.  
  
Para obtener más información sobre las aplicaciones para estas prácticas recomendadas, consulte [patrones de animación](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### <a name="animation-metrics"></a>Métricas de animación  
  
-   El sistema visiblemente debe reaccionar ante los gestos del usuario en menos de 10 milisegundos.  
  
-   Transiciones animadas no deberían tardar más de 500 milisegundos para completar.  
  
-   Es una manera para compensar las transiciones que requieren tiempos más largos dividir en dos partes. Por ejemplo, la primera parte de una animación podría ser el contenedor de contenido vacío (hasta 500 milisegundos), seguido por la atenuación de contenido en el contenedor (hasta 500 milisegundos).  
  
-   Para los tiempos de carga que se pueden calcular, se prefiere un indicador de progreso determinante (indicador de progreso realiza por ciento).  
  
-   Para los tiempos de carga que no se puede calcular, un indicador de disponibilidad como un cursor o animación de giro incrustado (carga o indicador del trabajo) es adecuado.  
  
### <a name="animation-as-communicator"></a>Animación como communicator  
En la interfaz de usuario de Visual Studio, animación funciona únicamente como una herramienta de comunicación.  Se usa para comunicar una variedad de información, como los cambios estructurales en la interfaz de usuario (por ejemplo, cuando un menú abre o cierra). Animación puede ayudar a visualizar el comportamiento depende del tiempo de sistemas complejos, como la visualización del progreso de instalación. Las animaciones también pueden utilizarse para llamar la atención con alertas y notificaciones.  
  
 Las animaciones de la interfaz de usuario funcionan normalmente de cuatro maneras: visualizar, llamar la atención, simular, y tiempos de respuesta o indicadores de progreso.  
  
#### <a name="visualize"></a>Visualizar  
Animación puede resaltar la naturaleza tridimensional de objetos y que sea más fácil para que los usuarios visualizar su estructura espacial. Para lograr esto, la animación puede necesita para rotar el objeto en un círculo completo, lentamente, activarlo o traer el objeto más cercano y ligeramente aumentar su tamaño para dar énfasis a sustitución o el foco.  
  
Aunque pueden mover objetos tridimensionales con control de usuario, el diseñador debe determinar de antemano (mediante programación o manualmente) cómo sacarle animar un movimiento que proporciona una descripción óptima del objeto. Esto programarse can animación a continuación activado por el usuario colocando el cursor sobre el objeto, mientras que los movimientos controlado por el usuario requieren que el usuario entender cómo manipular el objeto. Limitar el movimiento a un único eje o la orientación a la vez; escalar, girar, o traducir, pero no hace más de una al mismo tiempo.  
  
La categoría de visualizar incluye los aspectos de los datos, las relaciones, estado, estructura, la secuencia y la hora.  
  
##### <a name="data"></a>Datos  
Muestran información complejas y de variable:  
  
-   Mover a través de visualizaciones de información como diagramas y gráficos  
  
-   Ejecución paso a paso a través de una secuencia, visita guiada y paginación  
  
-   Detalles de llamada, señalar y resaltar información específica  
  
-   Superponer detalles e información adicional sobre un elemento con foco
  
-   Transformar de una representación estructural o de la organización a otro  
  
-   Que representa los cambios con el tiempo mediante los controles deslizantes de hora, ruedas de progreso y control y los controles de transporte (reproducir, detener y pausar) 
  
##### <a name="relationships"></a>Relaciones  
  
-   Ilustrar cómo se relacionan entre sí los elementos o qué elementos están relacionados con un elemento determinado
  
-   Visualización de relaciones de jerarquías y elementos primarios y secundarios o del mismo nivel
  
-   Genera un elemento de otro
  
-   Un elemento se minimiza a otro elemento
  
-   Un elemento Windows anclado a red a otro
  
##### <a name="state"></a>Estado  
  
-   Actualizaciones de contenido
  
-   Selección y el foco de usuario  
  
-   Progreso  
  
-   Errores  
  
##### <a name="structure"></a>Estructura  
  
-   Dinamizar la estructura en un nodo  
  
-   Reorienta  
  
-   Minimizar y maximizar, o expandir y contraer  
  
##### <a name="sequence"></a>Secuencia  
  
-   Secuencia de presentación de imágenes  
  
-   Voltear a través de imágenes  
  
##### <a name="time"></a>Tiempo  
  
-   Cambio de mostrar con el tiempo, el lapso de tiempo y la presentación en pantalla  
  
-   Mover a la Papelera, deshacer y rehacer  
  
-   Restaurar estado histórico  
  
#### <a name="attract-attention"></a>Llamar la atención  
Si el objetivo es llamar la atención del usuario a un único elemento fuera de varios o para alertar al usuario la información actualizada, a continuación, una animación podría ser adecuada. Por ejemplo, la página de inicio de la aplicación podría emplear un botón de introducción que se introduce en su lugar después de la página se cargue.  
  
Como norma, el último elemento móvil en la pantalla atrae la atención del usuario.  En una serie de elementos animados, la atención del usuario seguirá el último objeto móvil.  
  
##### <a name="alert"></a>Alerta  
  
-   Avisar al usuario, llamar la atención, mostrar el progreso  
  
-   Mostrar que algo se realiza correcta o incorrectamente o mostrar el progreso o cambios de progreso  
  
-   Pedir a los usuarios durante una tarea, como buscar más información en línea ni tener que aprender acerca de la tarea actual  
  
##### <a name="notifications"></a>Notificaciones  
  
-   Avisar al usuario acerca de una condición de error  
  
-   Interrumpir el usuario para ver si les gustaría asistir a otra cosa  
  
-   Tire suavemente informar al usuario que ha completado un proceso o cambiado, al igual que una vez completada una descarga.  
  
#### <a name="simulate"></a>Simular  
Esta categoría cubre physicality y dimensionalidad.  
  
-   Ilustrar procedencia de los objetos o donde vaya a  
  
-   Expandir y contraer o abrir y cerrar  
  
-   Activa el modo panorámico, el desplazamiento y la página  
  
-   Apilamiento y orden z  
  
-   Carrusel y accordion  
  
-   Voltear y rotar la interfaz de usuario  
  
#### <a name="response-and-progress-indicators"></a>Indicadores de respuesta y el progreso  
Indicadores de progreso tienen dos ventajas importantes:  
  
-   Los indicadores de progreso determinada e indeterminado asegurar al usuario que el sistema no se ha bloqueado y está trabajando en el problema.  
  
-   Indicadores determinados dar al usuario que una idea de hasta qué punto a lo largo de la acción está progresando, así como una sensación de vaya acercando a la finalización.  
  
##  <a name="BKMK_AnimationPatterns"></a> Patrones de animación  
  
### <a name="overview"></a>Información general  
Las animaciones en Visual Studio están diseñadas para atender una función específica sin reducir la productividad del usuario. Por lo general, deberían ser animaciones en Visual Studio:  
  
-   Pequeñas y discreto  
  
-   Naturales y realistas  
  
-   Sutiles y tenue  
  
-   Rápidos y eficaces  
  
-   Menos estricta, no da  
  
Esta ilustración muestra los estilos de animación que se recomienda para Visual Studio. Ninguna animación o sutiles animaciones como fundido de entrada / fundido de salida se utilizan con más frecuencia. Hay limitada para las aplicaciones de animaciones de movimiento como expandir y contraer, X e Y colocar el cambio y la rotación. 
  
![Los estilos de animación recomendados para Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "a_VSAnimStyles 1202")<br />Estilos de animación recomendados para Visual Studio
  
#### <a name="appear-and-disappear"></a>Aparecen y desaparecen  
Con este modelo, un elemento cambia del visible fuera de la vista y volver sin una animación de transición.  
  
![Aparecen y desaparecen animación](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "b_AppearAndDisappear 1202")<br />Aparecen y desaparecen animación  
  
##### <a name="correct-usage"></a>Uso correcto  
Elementos de interfaz de usuario nuevos que tienen que aparezcan o desaparezcan para que el usuario no se le distraiga ni se puede ver obstruido con forma instantánea. Además, animaciones de movimiento lento podrían considerarse un arrastre de rendimiento, lo que no ocurre con el estilo aparecen y desaparecen.  
  
##### <a name="incorrect-usage"></a>Uso incorrecto  
Casos en los que aparece repentinamente que el usuario no tiene ni idea interfaz de usuario ¿qué ha ocurrido y agregar una animación sería útil con la comprensión del contexto.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
El tiempo de retardo suele ser cero segundos.  
  
##### <a name="examples"></a>Ejemplos    
-   Ventanas de herramientas de ocultación automática  
  
-   Activar teclado editor de interfaz de usuario, como IntelliSense y la Ayuda de parámetro  
  
-   Regiones de código de expandir y contraer  
  
#### <a name="fade-in-and-fade-out"></a>Fundido de entrada y fundido de salida  
Con este modelo, un elemento de interfaz de usuario realiza la transición de no es visible (0% de opacidad) a visible (100% de opacidad) o viceversa.  
  
![Animación de fundido de entrada y fundido de salida](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "c_FadeInFadeOut 1202")<br />Animación de fundido de entrada y fundido de salida  
  
##### <a name="correct-usage"></a>Uso correcto  
Esto se recomienda más comúnmente animación de la interfaz de usuario. Es un efecto sutil que agrega interés sin interrumpir el flujo. En algunos casos, el usuario sea consciente de que hay una animación, percibir un suave y hacer fluir de sistema de interfaz de usuario.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
  
-   A partir de opacidad: 0% de fundido de entrada, 100% para fundido de salida  
  
-   Finalizar la opacidad: 100% de fundido de entrada, 0% de fundido de salida  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación  
  
-   Aceleración estilo: InOut seno  
  
##### <a name="examples"></a>Ejemplos  
  
-   Ventanas de herramientas de ocultación automática  
  
-   Menú Abrir y cerrar  
  
-   Primer plano y fondo transiciones de pestaña  
  
#### <a name="color-blend-from-a-to-b"></a>Mezcla de colores de la A B  
Con este modelo, un elemento de interfaz de usuario cambia de color A color B.  
  
![Animación de mezcla de colores](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "d_ColorBlend 1202")<br />Animación de mezcla de color  
  
##### <a name="correct-usage"></a>Uso correcto  
Como una transición animada cuando un elemento de interfaz de usuario cambia el color de un contexto o estado a otro.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
  
-   Color inicial: específica de la interfaz de usuario  
  
-   Color final: específica de la interfaz de usuario  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación  
  
-   Aceleración estilo: InOut seno  
  
##### <a name="examples"></a>Ejemplos  
  
-   Transiciones de estado de la ventana de documento (activo, última activas e inactivas)  
  
-   Las transiciones de estado de ventana de herramientas (tiene el foco y sin foco)  
  
#### <a name="expand-and-contract"></a>Expandir y contraer  
Con este modelo, un elemento de interfaz de usuario se expande en la X, Y o ambas direcciones.  
  
![Expandir y contraer de animación](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "e_ExpandContract 1202")<br />Expandir y contraer de animación  
  
##### <a name="correct-usage"></a>Uso correcto  
Como una transición animada cuando un elemento de interfaz de usuario cambia el tamaño de un contexto a otro.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
  
-   X escala: % o dimensión específica (en píxeles)  
  
-   Escala Y: % o dimensión específica (en píxeles)  
  
-   Fijar posición: generalmente superior izquierda (para los idiomas de izquierda a derecha) o superior derecha (para los idiomas de derecha a izquierda)  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación  
  
##### <a name="examples"></a>Ejemplos  
  
-   Panel del explorador de arquitectura de expandir y contraer  
  
-   Elemento de la página de inicio de expandir y contraer  
  
#### <a name="x-y-position-change"></a>Cambio de posición de X-Y  
Con este modelo, un elemento de interfaz de usuario cambia su posición X o Y o ambos.  
  
![Animación de cambio de posición de X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "f_XYPositionChange 1202")<br />Animación de cambio de posición de X-Y  
  
##### <a name="correct-usage"></a>Uso correcto  
Como una transición animada cuando un elemento de interfaz de usuario cambia de posición de un contexto a otro.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
  
-   Posición a partir de X e Y: específica de la interfaz de usuario  
  
-   Posición final X e Y: específica de la interfaz de usuario  
  
-   Ruta de acceso de movimiento: ninguno  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación  
  
-   Aceleración estilo: InOut seno  
  
##### <a name="example"></a>Ejemplo  
Reordenación de pestaña  
  
#### <a name="rotate"></a>Girar  
Con este modelo, se gira el elemento de interfaz de usuario.  
  
![Animación de giro del elemento de interfaz de usuario](../../extensibility/ux-guidelines/media/1202-g_rotate.png "g_Rotate 1202")<br />Animación de giro del elemento de interfaz de usuario  
  
##### <a name="correct-usage"></a>Uso correcto  
Solo para el indicador de progreso de giro indeterminado.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
  
-   Grado de giro: 360  
  
-   Centro de rotación: intermedio del objeto  
  
-   Duración: continua  
  
##### <a name="example"></a>Ejemplo  
Indicador de progreso indeterminada (giro)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>Acciones de interfaz de usuario comunes de shell y las animaciones recomendadas  
  
#### <a name="tab-open"></a>Pestaña abierta  
![Ficha animación de apertura](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "h_TabOpen 1202")<br />Animación de apertura de pestaña  
    
-   Estilo: aparecen  
  
-   Duración: cero segundos  

#### <a name="tab-close"></a>Cerrar pestaña  
![Ficha animación de cierre](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "i_TabClose 1202")<br />Animación de cierre de pestaña  
  
-   Estilo: Cambiar de posición X  
  
-   Duración: 200 milisegundos  
  
#### <a name="tab-reorder"></a>Pestaña volver a ordenar  
![Ficha animación de reorganización en Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "j_TabReorder 1202")<br />Animación de reorganización de pestaña

-   Estilo: Cambiar de posición X  
  
-   Duración: 200 milisegundos  
    
#### <a name="close-floating-document"></a>Cerrar documento flotante  
![Cierre flotante animación de documento](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "k_CloseFloatingDocument 1202")<br />Animación de cierre de documento flotante  
   
-   Estilo: aparecen  
  
-   Duración: 200 milisegundos   
 
#### <a name="window-state-transition"></a>Transición de estado de ventana  
![Animación de transición de estado de ventana](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "l_WindowStateTransition 1202")<br />Animación de transición de estado de ventana  
    
-   Estilo: para mantener la coherencia con otras ventanas, dejar que el sistema operativo actual definen la animación de cierre de documento.  
  
-   Duración: 200 milisegundos  
  
#### <a name="menu-open"></a>Menú Abrir  
![Animación de apertura de menú](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "m_MenuOpen 1202")<br />Animación de apertura de menú  
    
-   Estilo: fundido de entrada  
  
-   Duración: 200 milisegundos  
  
#### <a name="menu-close"></a>Cierre de menú  
![Animación de cierre de menú](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "n_MenuClose 1202")<br />Animación de cierre de menú  
    
-   Estilo: fundido de salida  
  
-   Duración: 200 milisegundos  
  
#### <a name="auto-hide-tool-window-reveal"></a>Mostrar ventana de herramienta de ocultación automática  
![Animación de mostrar ventana de herramienta de ocultación automática](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "o_AutoHideToolWindowReveal 1202")<br />Animación de mostrar ventana de herramienta de ocultación automática  

-   Estilo: aparecen  
  
-   Duración: cero segundos