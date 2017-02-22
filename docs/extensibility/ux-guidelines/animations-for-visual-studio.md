---
title: "Animaciones para Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
---
# Animaciones para Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Aspectos básicos de animación  
  
### Prácticas recomendadas de animación en Visual Studio  
 Siga estas reglas para garantizar estilos de animación coherente y fácil de usar en el IDE de Visual Studio.  
  
-   **Sea selectivo.** Limitar las animaciones a los que se usan con fines específicos.  
  
-   **Tiempo y la velocidad están importantes** para asegurarse de que las transiciones se sienten natural y rápida:  
  
    -   Complete las transiciones animadas dentro de medio segundo \(500 milisegundos\).  
  
    -   Las animaciones que se produciría con frecuencia deben ser lo suficientemente rápido, por lo que no interrumpen el flujo de trabajo del usuario.  
  
    -   Animaciones no deben ser tan rápido o discordante que es difícil de entender, pero no tan lento que permite una impaciente la transición al finalizar.  
  
    -   Utilizar tiempo variable para destacar la importancia. Por ejemplo, al desplazarse a través de una secuencia de elementos en un diagrama de clases, acelerar a través de las transiciones entre los elementos y ralentizar centrarse en elementos importantes.  
  
-   **Utilizar la aceleración no lineal gradual** desde un estado a otro, lo que proporciona una sensación de movimiento con calma y natural  
  
-   Cuando sea posible, **usar una animación sutil al mantener el mouse** para indicar elementos interactivos en el mouse.  
  
-   Si depende en gran medida animaciones en sus características, a continuación, **proporcionan un medio para desactivarlos** localmente \(para todas las características\) como una opción en el **Herramientas \> opciones** cuadro de diálogo.  
  
-   **Solo animación debe producirse en un momento** y transmitir sólo una parte de la información.  
  
-   **Sutileza es importante.** En la mayoría de los casos la animación no tiene que requieren atención del usuario para cumplir su propósito. Cambios sutiles de temporización, secuenciación y comportamiento pueden afectar significativamente a la percepción y pueden marcar la diferencia entre una animación eficaz e ineficaz.  
  
-   Al usar animación para llamar la atención sobre algo, **Asegúrese de que merece la pena interrumpir al usuario**del tren de pensamiento.  
  
-   **Al mostrar el progreso o estado** animación:  
  
    -   Deja de mostrar el movimiento de progreso cuando el proceso subyacente no avanza.  
  
    -   Distinguir procesos indeterminados de procesos determinados.  
  
    -   Asegúrese de que una animación tiene los Estados de finalización y error de identificación.  
  
    -   Minimizar el uso de animaciones de efecto que mostrar el estado y asegúrese de que tienen un valor real al proporcionar información adicional de uso real. Algunos ejemplos son las emergencias y cambios de estado transitorio  
  
#### No:  
  
-   Utilice pequeños movimientos \(movimientos en un tamaño pequeño\), que prefieren fundido y cambia con el movimiento de objetos.  
  
-   Utilice las animaciones que tienen lugar a través de una gran área de visualización en pantalla. Independientemente del tamaño, este estilo de animación distrae al usuario.  
  
-   Usar animaciones no relacionados con el objeto de en que usuario se centra actualmente o interactuar con.  
  
-   Usar animaciones que requieren la interacción del usuario para restablecer el estado, como obligar al usuario a responder a una notificación para que sea deja de parpadear parpadeante. Interactuar con ellos en ningún modo debe ser suficiente para descartar ellos.  
  
 Para obtener más información acerca de aplicaciones para estas prácticas recomendadas, consulte [Patrones de animación](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### Métricas de animación  
  
-   El sistema visiblemente debe reaccionar a los gestos del usuario en menos de 10 milisegundos.  
  
-   Transiciones animadas no deberían tardar más de 500 milisegundos en completarse.  
  
-   Una manera para compensar las transiciones que requieren tiempos más largos es separar en dos partes; Por ejemplo, la primera parte de una animación podría ser el contenedor de contenido vacío \(hasta 500 milisegundos\) seguido por el fundido de contenido en el contenedor \(hasta 500 milisegundos\).  
  
-   Para los tiempos de carga que se pueden calcular, se prefiere un indicador de progreso determinante \(indicador de progreso hecho por ciento\).  
  
-   Para los tiempos de carga que no se puede calcular, un indicador de ocupado, como un cursor o animación de giro incrustado \(carga o indicador del trabajo\) es adecuado.  
  
### Animación de communicator  
 En la interfaz de usuario de Visual Studio, animación funciona únicamente como una herramienta de comunicación.  Se utiliza para comunicar una variedad de información, como los cambios estructurales en la interfaz de usuario; Por ejemplo, cuando un menú se abre o se cierra. Animación puede ayudar a visualizar el comportamiento depende del tiempo de sistemas complejos, como la visualización del progreso de instalación o utilizarse para atraer la atención con alertas y notificaciones.  
  
 Animaciones de interfaz de usuario funcionan normalmente de cuatro maneras: visualizar, atraer la atención, simular e indicar respuesta veces o de progreso.  
  
#### Visualizar  
 Animación puede resaltar la naturaleza de los objetos tridimensional y facilitan a los usuarios visualizar su estructura espacial. Para lograr esto, la animación puede necesita para girar el objeto en un círculo completo, lentamente activar y hacia atrás, o traer el objeto más cercano y aumentar ligeramente su tamaño para destacar la sustitución o el foco.  
  
 Aunque pueden mover objetos tridimensionales con control de usuario, el diseñador debe determinar de antemano \(mediante programación o manualmente\) cómo óptimamente animar un movimiento que proporciona una descripción óptima del objeto. Esto programarse la animación puede entonces activado por el usuario colocando el cursor sobre el objeto, mientras que los movimientos controlada por el usuario requieren que el usuario a entender cómo manipular el objeto. Limitar el movimiento a un único eje o la orientación a la vez; escalar, girar, o traducir, pero no hace más de una vez.  
  
 La categoría de visualizar incluye los aspectos de los datos, las relaciones, estado, estructura, la secuencia y el tiempo.  
  
##### Datos  
 Mostrar información de variables y compleja:  
  
-   Mover a través de visualizaciones de información como gráficos y diagramas  
  
-   Ejecución paso a paso a través de una secuencia, visita guiada y paginación  
  
-   Llamar a detalles, señalar y resaltar información específica  
  
-   Superponer los detalles e información adicional sobre un elemento con foco  
  
-   Transformación de una representación estructural o de la organización a otro  
  
-   Que representan cambios en el tiempo con controles deslizantes de hora, ruedas correr y control y los controles de transporte \(reproducción, detención y pausa\).  
  
##### Relaciones  
  
-   Ilustrar cómo se relacionan entre sí elementos o qué elementos están relacionados con un elemento determinado.  
  
-   Mostrar las jerarquías y elementos primarios y secundarios o del mismo nivel relaciones  
  
-   Genera un elemento de otro  
  
-   Un elemento se minimiza a otro elemento  
  
-   Un elemento bloqueado a otro  
  
##### Estado  
  
-   Actualizaciones de contenido.  
  
-   Selección y el foco de usuario  
  
-   Progreso  
  
-   Errores  
  
##### Estructura  
  
-   La estructura en un nodo de tablas dinámicas  
  
-   Reorientar  
  
-   Minimizar y maximizar, o expandir y contraer  
  
##### Secuencia  
  
-   Secuencia de presentación  
  
-   Hojear imágenes  
  
##### Tiempo  
  
-   Mostrar cambios con el tiempo, el lapso de tiempo y la presentación en pantalla  
  
-   Mover, eliminar, deshacer y rehacer  
  
-   Restaurar estado histórico  
  
#### Atraer la atención  
 Si el objetivo es llamar la atención del usuario a un único elemento de varios o para alertar al usuario a la información actualizada, una animación resulte adecuada. Por ejemplo, la página de inicio de aplicaciones puede emplear un botón de introducción que se introduce en su lugar, después de cargarse la página.  
  
 Como regla general, el último elemento móvil en la pantalla atraiga la atención del usuario.  En una serie de elementos animados, la atención del usuario seguirá el último objeto.  
  
##### Alerta  
  
-   Alertar al usuario, llamar la atención, mostrar el progreso  
  
-   Mostrar que algo se hace correcta o incorrectamente o mostrar el progreso o los cambios de progreso  
  
-   Pedir a los usuarios durante una tarea, como buscar más información en línea o de aprendizaje acerca de la tarea actual  
  
##### Notificaciones  
  
-   Alertar al usuario acerca de una condición de error  
  
-   Interrumpir el usuario para ver si les gustaría asistir a otra cosa  
  
-   Suavemente informar al usuario que un proceso ha finalizado o se cambia, como cuando se completa la descarga.  
  
#### Simular  
 Esta categoría cubre physicality y dimensionalidad.  
  
-   Ilustrar procedencia de los objetos o donde vaya a  
  
-   Expandir y contraer o abrir y cerrar  
  
-   Activa la panorámica, desplazamiento y página  
  
-   Apilamiento y orden z  
  
-   Carrusel y acordeón  
  
-   Voltear y rotar la interfaz de usuario  
  
#### Indicadores de progreso y de respuesta  
 Indicadores de progreso tienen dos ventajas importantes:  
  
-   Ambos indicadores de progreso indeterminada y determinada garantizar al usuario que el sistema no se ha bloqueado y está trabajando en el problema.  
  
-   Indicadores determinados dar al usuario que una idea de la distancia a lo largo de la acción en curso, así como la sensación de que se aproxima a la finalización.  
  
##  <a name="BKMK_AnimationPatterns"></a> Patrones de animación  
  
### Información general  
 Animaciones en Visual Studio están diseñados para servir una función específica y no mermar la productividad de usuario. Características de animación general cumplir para incluir:  
  
-   Pequeños y discretos  
  
-   Naturales y realistas  
  
-   Sutiles y tenue  
  
-   Rápida y eficaz  
  
-   Más flexible, no da  
  
 La ilustración siguiente muestra los estilos de animación recomendados para su uso en Visual Studio. Ninguna animación y animaciones sutiles como intensifiquen \/ difuminar se usan con más frecuencia. Hay limitada para las aplicaciones de movimiento de animaciones como expandir y contraer, cambio y rotación de posiciones X e Y.  
  
 ![Recommended animation styles for Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202\-a\_VSAnimStyles")  
  
 **Estilos de animación recomendados para Visual Studio**  
  
#### Aparecen y desaparecen  
 Con este modelo, un elemento cambia de visible de la vista y volver sin una animación de transición:  
  
 ![Appear&#47;Disappear animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202\-b\_AppearAndDisappear")  
  
##### Uso correcto  
 Elementos de interfaz de usuario nuevos que necesita al instante aparezcan o desaparezcan de modo que el usuario no se distraen ni obstruido. Además, las animaciones de movimiento lento pueden considerarse un arrastre de rendimiento, lo que no ocurre con el estilo aparecen y desaparecen.  
  
##### Uso incorrecto  
 Casos en que aparece su interfaz de usuario repentinamente que el usuario no tiene idea ¿qué ha ocurrido y agregar una animación ayudaría a comprender el contexto.  
  
##### Propiedades de animación  
 El tiempo de retardo suele ser cero segundos.  
  
##### Ejemplos  
  
-   Ventanas de herramientas Ocultar automáticamente  
  
-   Activado en el teclado editor de interfaz de usuario, como IntelliSense y la Ayuda de parámetro  
  
-   Regiones de código de expandir y contraer  
  
#### Fundido de entrada y difuminado  
 Con este modelo, un elemento de interfaz de usuario pasa de no visibles \(0% de opacidad\) visible \(100% de opacidad\) o viceversa:  
  
 ![Fade&#45;in&#47;Fade&#45;out animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202\-c\_FadeInFadeOut")  
  
##### Uso correcto  
 Esto se recomienda la más animación de la interfaz de usuario. Es un efecto sutil que agrega interés sin interrumpir el flujo. En algunos casos, el usuario puede incluso comprenden que hay una animación y simplemente percibe un sistema de interfaz de usuario suave y flujo.  
  
##### Propiedades de animación  
  
-   A partir de opacidad: 0% de fundido de entrada, 100% de difuminado  
  
-   Finalizando la opacidad: 100% de fundido de entrada, 0% de difuminado  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se utiliza como parte de una secuencia de animación de combinación  
  
-   Estilo de aceleración: InOut seno  
  
##### Ejemplos  
  
-   Ventanas de herramientas Ocultar automáticamente  
  
-   Menú Abrir y cerrar  
  
-   Transiciones de ficha de fondo y primer plano  
  
#### Mezcla de colores de la A B  
 Con este modelo, un elemento de interfaz de usuario cambia de color A color B:  
  
 ![Color blend animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202\-d\_ColorBlend")  
  
##### Uso correcto  
 Como una transición animada cuando un elemento de interfaz de usuario cambia el color de un contexto o estado a otro.  
  
##### Propiedades de animación  
  
-   Color inicial: interfaz de usuario  
  
-   Color final: interfaz de usuario  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se utiliza como parte de una secuencia de animación de combinación  
  
-   Estilo de aceleración: InOut seno  
  
##### Ejemplos  
  
-   Transiciones de estado de la ventana de documento \(activo, última activas e inactivas\)  
  
-   Las transiciones de estado de ventana de herramientas \(centrado y no enfocado\)  
  
#### Expandir y contraer  
 Con este modelo, un elemento de interfaz de usuario se expande en la X, Y o ambas direcciones:  
  
 ![Expand&#47;Contract animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202\-e\_ExpandContract")  
  
##### Uso correcto  
 Como una transición animada cuando un elemento de interfaz de usuario cambia el tamaño de un contexto a otro.  
  
##### Propiedades de animación  
  
-   Escala x:: % o una dimensión específica \(en píxeles\)  
  
-   Escala: % o una dimensión específica \(en píxeles\)  
  
-   Fijar posición: generalmente superior izquierda \(para idiomas de derecha a izquierda\) o superior derecha \(para idiomas de derecha a izquierda\)  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se utiliza como parte de una secuencia de animación de combinación  
  
##### Ejemplos  
  
-   Panel del explorador de arquitectura de expandir y contraer  
  
-   Elemento de la página de inicio de expandir y contraer  
  
#### Cambio de posición de X\-Y  
 Con este modelo, un elemento de interfaz de usuario cambia su posición X e Y o ambas:  
  
 ![X&#47;Y position change animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202\-f\_XYPositionChange")  
  
##### Uso correcto  
 Como una transición animada cuando un elemento de interfaz de usuario cambia la posición de un contexto a otro.  
  
##### Propiedades de animación  
  
-   Posición a partir de X e Y: interfaz de usuario  
  
-   Posición final X e Y: interfaz de usuario  
  
-   Guía de movimiento: ninguno  
  
-   Duración: 200 milisegundos independiente, 100 milisegundos cuando se utiliza como parte de una secuencia de animación de combinación  
  
-   Estilo de aceleración: InOut seno  
  
##### Ejemplo  
 Reordenación de pestaña  
  
#### Girar  
 Con este modelo, se gira el elemento de interfaz de usuario:  
  
 ![Rotate animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202\-g\_Rotate")  
  
##### Uso correcto  
 Sólo para el indicador de progreso indeterminada de giro.  
  
##### Propiedades de animación  
  
-   Grado de rotación: 360  
  
-   Centro de rotación: central del objeto  
  
-   Duración: continua  
  
##### Ejemplo  
 Indicador de progreso indeterminada \(giro\)  
  
### Acciones de interfaz de usuario de shell comunes y animaciones recomendadas  
  
#### Pestaña abierta  
  
-   Estilo: aparecen  
  
-   Duración: Cero segundos  
  
 ![Tab open animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202\-h\_TabOpen")  
  
#### Cerrar pestaña  
  
-   Estilo: Cambiar de posición X  
  
-   Duración: 200 milisegundos  
  
 ![Tab close animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202\-i\_TabClose")  
  
#### Ficha pedido  
  
-   Estilo: Cambiar de posición X  
  
-   Duración: 200 milisegundos  
  
 ![Tab reorder animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202\-j\_TabReorder")  
  
#### Cerrar documento flotante  
  
-   Estilo: aparecen  
  
-   Duración: 200 milisegundos  
  
 ![Close floating document animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202\-k\_CloseFloatingDocument")  
  
#### Transición de estado de ventana  
  
-   Estilo: Para ser coherentes con otras ventanas, dejar que el sistema operativo actual definen la animación de cierre de documento.  
  
-   Duración: 200 milisegundos  
  
 ![Window state transition animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202\-l\_WindowStateTransition")  
  
#### Menú Abrir  
  
-   Estilo: fundido de entrada  
  
-   Duración: 200 milisegundos  
  
 ![Menu open animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202\-m\_MenuOpen")  
  
#### Cerrar el menú  
  
-   Estilo: difuminado  
  
-   Duración: 200 milisegundos  
  
 ![Menu close animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202\-n\_MenuClose")  
  
#### Mostrar ventana de herramienta de ocultación automática  
  
-   Estilo: aparecen  
  
-   Duración: Cero segundos  
  
 ![Auto&#45;hide tool window animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202\-o\_AutoHideToolWindowReveal")