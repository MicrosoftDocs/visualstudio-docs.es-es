---
title: Las animaciones para Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b79ed46a6b81969658e5413d8a2d8f392893fb7b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582209"
---
# <a name="animations-for-visual-studio"></a>Animaciones para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [animaciones para Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/ux-guidelines/animations-for-visual-studio).  
  
## <a name="animation-fundamentals"></a>Aspectos básicos de animación  
  
### <a name="animation-best-practices-in-visual-studio"></a>Procedimientos recomendados de animación en Visual Studio  
 Siga estas reglas para garantizar los estilos de animación coherente y fácil de usar en el IDE de Visual Studio.  
  
-   **Sea selectivo.** Limitar las animaciones a los que sirven para propósitos específicos.  
  
-   **Control de tiempo y la velocidad son importantes** para asegurarse de que las transiciones sentirse rápido y natural:  
  
    -   Completar transiciones animadas dentro de un medio segundo (500 milisegundos).  
  
    -   Las animaciones que se producirían con frecuencia deben ser lo suficientemente rápido, por lo que no interrumpen el flujo de trabajo del usuario.  
  
    -   Las animaciones no deben ser tan rápido o discordante que resulta difícil de entender, pero no tan lento que realice una impacienta para la transición al finalizar.  
  
    -   Utilice el control de tiempo variable para enfatizar la importancia. Por ejemplo, al navegar a través de una secuencia de elementos en un diagrama de clases, la velocidad a través de las transiciones entre los elementos, a continuación, ralentizar centrarse en los elementos importantes.  
  
-   **Usar aceleración no lineal gradual** desde un estado a otro, lo que ofrece una sensación de movimiento de calma y natural  
  
-   Cuando sea posible, **usar una animación sutil al mantener el mouse** para indicar los elementos interactivos situado bajo el mouse.  
  
-   Si depende en gran medida las animaciones en sus características, a continuación, **proporcionan un medio para desactivarlos** localmente (para todas las características) como una opción en el **Herramientas > opciones** cuadro de diálogo.  
  
-   **Solo una animación debe producirse en un momento** y transmitir solo un fragmento de información.  
  
-   **Matiz es importante.** En la mayoría de los casos la animación no tiene que requieren atención del usuario para atender su propósito. Cambios sutiles en tiempo, la secuenciación y el comportamiento pueden afectar significativamente a la percepción y pueden marcar la diferencia entre una animación eficaz e ineficaz.  
  
-   Al usar animación para llamar la atención sobre algo, **Asegúrese de que merece la pena interrumpir al usuario**del tren de pensamiento.  
  
-   **Al mostrar el progreso o estado** a través de animación:  
  
    -   Detener la presentación de movimiento de progreso cuando el proceso subyacente no está promoviendo.  
  
    -   Distinguir procesos indeterminados de procesos determinados.  
  
    -   Asegúrese de que una animación tiene identificación Estados de error y de finalización.  
  
    -   Minimizar el uso de animaciones de efecto que mostrar el estado y asegúrese de que tienen un valor real al proporcionar información adicional del uso real. Algunos ejemplos incluyen de emergencia y cambios de estado transitorio  
  
#### <a name="do-not"></a>No:  
  
-   Usar movimientos pequeño (movimiento en una superficie pequeña), que prefieren difumina y cambia con el movimiento de objetos.  
  
-   Utilice las animaciones que tienen lugar a través de una gran área de espacio en pantalla. Independientemente del tamaño, este estilo de animación distrae al usuario.  
  
-   Utilice las animaciones que no hacen referencia al objeto en que del usuario actualmente se centra o interactuar con.  
  
-   Utilice las animaciones que requieren la interacción del usuario para restablecer el estado, como forzar al usuario que responda a una notificación para que sea deja de parpadear parpadeante. Interactuar con ellos en ningún modo debe ser suficiente para descartarlas.  
  
 Para obtener más información acerca de las aplicaciones para estos procedimientos recomendados, consulte [patrones de animación](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### <a name="animation-metrics"></a>Métricas de animación  
  
-   El sistema visiblemente debe reaccionar ante los gestos del usuario en menos de 10 milisegundos.  
  
-   Las transiciones animadas no deberían tardar más de 500 milisegundos en completarse.  
  
-   Es una forma para compensar las transiciones que requieren tiempos más largos separarlo en dos partes; Por ejemplo, la primera parte de una animación podría ser el contenedor de contenido vacío (hasta 500 milisegundos) seguido por la atenuación de contenido en el contenedor (hasta 500 milisegundos).  
  
-   Para los tiempos de carga que se pueden calcular, se prefiere un indicador de progreso determinante (indicador de progreso: terminado por ciento).  
  
-   Para los tiempos de carga que no se puede calcular, un indicador de ocupado, como un cursor o una animación de giro incrustado (carga o indicador del trabajo) es adecuado.  
  
### <a name="animation-as-communicator"></a>Animación como communicator  
 En la interfaz de usuario de Visual Studio, animación funciona solo como una herramienta de comunicación.  Se utiliza para comunicar una variedad de información, como los cambios estructurales en la interfaz de usuario; Por ejemplo, cuando un menú se abre o cierra. Animación puede ayudar a visualizar el comportamiento depende del tiempo de sistemas complejos, como la visualización del progreso de instalación o utilizarse para atraer la atención con alertas y notificaciones.  
  
 Las animaciones de la interfaz de usuario funcionan normalmente de cuatro maneras: visualizar, atraer la atención, simular e indica respuesta veces o de progreso.  
  
#### <a name="visualize"></a>Visualizar  
 Animación puede resaltar la naturaleza tridimensional de objetos y que sea más fácil para que los usuarios visualizar su estructura espacial. Para lograr esto, la animación es posible que necesita para girar el objeto en un círculo completo, lentamente activarlo y hacia atrás, o traer el objeto más cercano y ligeramente aumentar su tamaño para destacar la sustitución o tiene el foco.  
  
 Aunque pueden mover objetos tridimensionales con control de usuario, el diseñador debe determinar de antemano (mediante programación o manualmente) cómo sacarle animar un movimiento que se proporciona una descripción óptima del objeto. Esto programarse la animación puede, a continuación, activarse por el usuario colocando el cursor sobre el objeto, mientras que los movimientos controlado por el usuario requieren que el usuario entender cómo manipular el objeto. Limitar el movimiento a un único eje o la orientación a la vez; escalar, girar, o trasladar, pero no hace más de uno al mismo tiempo.  
  
 La categoría de visualizar incluye los aspectos de los datos, relaciones, state, estructura, la secuencia y el tiempo.  
  
##### <a name="data"></a>Datos  
 Muestran información complejas y de variable:  
  
-   Mover a través de visualizaciones de información como las gráficos  
  
-   Ejecución paso a paso a través de una secuencia, visita guiada y paginación  
  
-   Realizar llamadas a los detalles, señalar y resaltar la información específica  
  
-   Superposición de detalles e información adicional sobre un elemento con foco  
  
-   Transformación de una representación estructural o de la organización a otra  
  
-   Que representa los cambios con el tiempo mediante controles deslizantes de hora, llantas de salir a correr y lanzadera y controles de transporte (reproducción, detención y pausa).  
  
##### <a name="relationships"></a>Relaciones  
  
-   Ilustrar cómo se relacionan entre sí los elementos o qué elementos están relacionados con un elemento determinado.  
  
-   Visualización de relaciones de jerarquías y elementos primarios y secundarios o del mismo nivel  
  
-   Genera un elemento de otro  
  
-   Minimiza un elemento a otro elemento  
  
-   Un elemento bloqueado a otro  
  
##### <a name="state"></a>Estado  
  
-   Actualizaciones de contenido.  
  
-   Selección y el foco del usuario  
  
-   Progreso  
  
-   Errores  
  
##### <a name="structure"></a>Estructura  
  
-   Dinamizar la estructura en un nodo  
  
-   Reorientar  
  
-   Minimizar y maximizar, o expandir y contraer  
  
##### <a name="sequence"></a>Secuencia  
  
-   Secuencia de presentación con diapositivas  
  
-   Voltear a través de imágenes  
  
##### <a name="time"></a>Tiempo  
  
-   Cambio de mostrar a lo largo de tiempo, el lapso de tiempo y la presentación en pantalla  
  
-   Mover a la Papelera, deshacer y rehacer  
  
-   Restaurar estado histórico  
  
#### <a name="attract-attention"></a>Atraer la atención  
 Si el objetivo es para atraer la atención del usuario a un solo elemento fuera de algunos o para alertar al usuario a la información actualizada, una animación puede ser adecuada. Por ejemplo, la página de inicio de aplicaciones puede emplear un botón de introducción a la que se desliza en su lugar una vez cargada la página.  
  
 Como regla general, el último elemento móvil en la pantalla atraiga la atención del usuario.  En una serie de elementos animados, la atención del usuario seguirá el último objeto.  
  
##### <a name="alert"></a>Alerta  
  
-   Alertar al usuario, obtener atención y mostrar el progreso  
  
-   Mostrar que algo se realiza correcta o incorrectamente o mostrar el progreso o los cambios de progreso  
  
-   Pedir a los usuarios durante una tarea, como buscar más información en línea o aprendiendo sobre la tarea actual  
  
##### <a name="notifications"></a>Notificaciones  
  
-   Alertar al usuario sobre una condición de error  
  
-   Interrumpan al usuario para ver si desea ocuparse de otro  
  
-   Suavemente informar al usuario que ha finalizado o se cambia, como cuando una descarga se completa un proceso.  
  
#### <a name="simulate"></a>Simular  
 Esta categoría cubre physicality y dimensionalidad.  
  
-   Ilustrar dónde proceden los objetos o donde vaya a  
  
-   Expandir y contraer o abrir y cerrar  
  
-   Movimiento panorámico, desplazamiento y la página activa  
  
-   Apilamiento y orden z  
  
-   Carrusel y accordion  
  
-   Voltear y rotar la interfaz de usuario  
  
#### <a name="response-and-progress-indicators"></a>Indicadores de progreso y de respuesta  
 Indicadores de progreso tienen dos ventajas importantes:  
  
-   Ambos indicadores de progreso indeterminada y determinada tranquilizar al usuario que el sistema no se ha bloqueado y está trabajando en el problema.  
  
-   Indicadores determinados ofrecen que una idea de hasta qué punto a lo largo de la acción se lleva a cabo, así como una sensación de acercándose a la finalización.  
  
##  <a name="BKMK_AnimationPatterns"></a> Patrones de animación  
  
### <a name="overview"></a>Información general  
 Las animaciones en Visual Studio están diseñadas para dar servicio a una función específica y no mermar la productividad de usuario. Características de animación general cumplir para que incluya:  
  
-   Pequeños y discretos  
  
-   Naturales y realistas  
  
-   Sutiles y tenue  
  
-   Rápido y eficiente  
  
-   Más flexible, no da  
  
 La siguiente ilustración muestra los estilos de animación que se recomienda para su uso en Visual Studio. Ninguna animación y animaciones sutiles, como fundido de entrada / fundido de salida se usan con más frecuencia. Hay limitada para las aplicaciones de movimiento de las animaciones, como expandir y contraer, cambio y la rotación de posiciones X e Y.  
  
 ![Recomienda estilos de animación para Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202 a_VSAnimStyles")  
  
 **Estilos de animación recomendados para Visual Studio**  
  
#### <a name="appear-and-disappear"></a>Aparecen y desaparecen  
 Con este patrón, un elemento cambia de visible de la vista y volver sin una animación de transición:  
  
 ![Aparecen&#47;desaparecen de la animación en Visual Studio](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202 b_AppearAndDisappear")  
  
##### <a name="correct-usage"></a>Uso correcto  
 Elementos de interfaz de usuario nuevos que se deba al instante aparezcan o desaparezcan para que el usuario no se distraen ni se puede ver obstruido. Además, las animaciones de movimiento lento pueden considerarse como un arrastre de rendimiento, lo que no ocurre con el estilo que aparecen y desaparecen.  
  
##### <a name="incorrect-usage"></a>Uso incorrecto  
 Casos en que la interfaz de usuario aparece repentinamente que el usuario no tiene idea de qué ha ocurrido y agregar una animación ayudaría con comprensión del contexto.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
 El tiempo de retardo suele ser cero segundos.  
  
##### <a name="examples"></a>Ejemplos  
  
-   Ventanas de ocultación automática  
  
-   Interfaz de usuario, como IntelliSense y la Ayuda de parámetro de editor activados en el teclado  
  
-   Regiones de código de expandir y contraer  
  
#### <a name="fade-in-and-fade-out"></a>Fundido de entrada y el fundido de salida  
 Con este patrón, se pasa un elemento de interfaz de usuario de no es visible (opacidad de 0%) a visible (100% de opacidad) o viceversa:  
  
 ![Atenuar&#45;en&#47;atenuar&#45;animación en Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202 c_FadeInFadeOut")  
  
##### <a name="correct-usage"></a>Uso correcto  
 Con más frecuencia esto se recomienda la animación de la interfaz de usuario. Es un efecto sutil que agrega interés sin interrumpir el flujo. En algunos casos, el usuario puede no incluso tenga en cuenta que hay una animación y simplemente percibe un sistema de la interfaz de usuario sin problemas, el flujo.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
  
-   A partir de opacidad: 0% de fundido de entrada, 100% de fundido de salida  
  
-   Finalizando la opacidad: 100% de fundido de entrada, de 0% de fundido de salida  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación  
  
-   Estilo de aceleración: InOut seno  
  
##### <a name="examples"></a>Ejemplos  
  
-   Ventanas de ocultación automática  
  
-   Menú Abrir y cerrar  
  
-   Transiciones de pestaña en segundo plano y de primer plano  
  
#### <a name="color-blend-from-a-to-b"></a>Mezcla de colores de la A B  
 Con este patrón, un elemento de interfaz de usuario cambia de color A color B:  
  
 ![Color de blend animación en Visual Studio](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202 d_ColorBlend")  
  
##### <a name="correct-usage"></a>Uso correcto  
 Como una transición animada cuando un elemento de interfaz de usuario cambia el color de un contexto o estado a otro.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
  
-   Color inicial: interfaz de usuario  
  
-   Color final: interfaz de usuario  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación  
  
-   Estilo de aceleración: InOut seno  
  
##### <a name="examples"></a>Ejemplos  
  
-   Transiciones de estado de la ventana de documento (activo, última activas e inactivas)  
  
-   Transiciones de estado de la ventana de herramientas (centrado y sin foco)  
  
#### <a name="expand-and-contract"></a>Expandir y contraer  
 Con este patrón, se expande un elemento de interfaz de usuario en la X, Y o ambas direcciones:  
  
 ![Expanda&#47;de contrato de animación en Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202 e_ExpandContract")  
  
##### <a name="correct-usage"></a>Uso correcto  
 Como una transición animada cuando un elemento de interfaz de usuario cambia el tamaño de un contexto a otro.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
  
-   X escala: % o una dimensión específica (en píxeles)  
  
-   Escala Y: % o una dimensión específica (en píxeles)  
  
-   Posición de anclaje: por lo general superior izquierda (para idiomas de izquierda a derecha) o superior derecha (para idiomas de derecha a izquierda)  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación  
  
##### <a name="examples"></a>Ejemplos  
  
-   Panel del explorador de arquitectura expandir y contraer  
  
-   Elemento de la página de inicio expandir y contraer  
  
#### <a name="x-y-position-change"></a>Cambio de posición de X-Y  
 Con este patrón, un elemento de interfaz de usuario cambia su posición X o Y o ambos:  
  
 ![X&#47;cambiar de posición Y animación en Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202 f_XYPositionChange")  
  
##### <a name="correct-usage"></a>Uso correcto  
 Como una transición animada cuando un elemento de interfaz de usuario cambia de posición de un contexto a otro.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
  
-   Posición a partir de X e Y: interfaz de usuario  
  
-   Posición final X e Y: interfaz de usuario  
  
-   Guía de movimiento: ninguno  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se usa como parte de una secuencia de animación de combinación  
  
-   Estilo de aceleración: InOut seno  
  
##### <a name="example"></a>Ejemplo  
 Reordenación de pestaña  
  
#### <a name="rotate"></a>Girar  
 Con este patrón, gira el elemento de interfaz de usuario:  
  
 ![Animación de giro en Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202 g_Rotate")  
  
##### <a name="correct-usage"></a>Uso correcto  
 Solo para el indicador de progreso indeterminada de giro.  
  
##### <a name="animation-properties"></a>Propiedades de animación  
  
-   Grado de giro: 360  
  
-   Centro de rotación: central del objeto  
  
-   Duración: continua  
  
##### <a name="example"></a>Ejemplo  
 Indicador de progreso indeterminada (girar)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>Acciones de interfaz de usuario de shell comunes y animaciones recomendadas  
  
#### <a name="tab-open"></a>Pestaña abierta  
  
-   Estilo: aparecen  
  
-   Duración: Cero segundos  
  
 ![Pestaña animación de apertura en Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202 h_TabOpen")  
  
#### <a name="tab-close"></a>Cerrar pestaña  
  
-   Estilo: Cambiar de posición X  
  
-   Duración: 200 milisegundos  
  
 ![Pestaña animación de cierre en Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202 i_TabClose")  
  
#### <a name="tab-reorder"></a>Reordenación de pestaña  
  
-   Estilo: Cambiar de posición X  
  
-   Duración: 200 milisegundos  
  
 ![Pestaña animación de reorganización en Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202 j_TabReorder")  
  
#### <a name="close-floating-document"></a>Cerrar documento flotante  
  
-   Estilo: aparecen  
  
-   Duración: 200 milisegundos  
  
 ![Cierre flotante animación del documento en Visual Studio](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202 k_CloseFloatingDocument")  
  
#### <a name="window-state-transition"></a>Transición de estado de ventana  
  
-   Style: Para que sea coherente con otras ventanas, dejar que el sistema operativo actual definen la animación de cierre de documento.  
  
-   Duración: 200 milisegundos  
  
 ![Animación de transición de estado de ventana en Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202 l_WindowStateTransition")  
  
#### <a name="menu-open"></a>Menú Abrir  
  
-   Estilo: fundido de entrada  
  
-   Duración: 200 milisegundos  
  
 ![Animación de apertura de menú en Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202 m_MenuOpen")  
  
#### <a name="menu-close"></a>Cerrar menú  
  
-   Estilo: fundido de salida  
  
-   Duración: 200 milisegundos  
  
 ![Animación de cierre de menú en Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202 n_MenuClose")  
  
#### <a name="auto-hide-tool-window-reveal"></a>Mostrar ventana de ocultación automática herramienta  
  
-   Estilo: aparecen  
  
-   Duración: Cero segundos  
  
 ![Auto&#45;ocultar las animaciones de ventana de herramientas en Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")

