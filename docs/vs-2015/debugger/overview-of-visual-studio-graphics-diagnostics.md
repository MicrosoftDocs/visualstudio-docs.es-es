---
title: Información general de diagnóstico de gráficos de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddd429d9-ac70-4ac4-9e69-299c6ea2df09
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4716ac398916a869fe122b54f829bbfda2f9911b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810447"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Información general de Diagnóstico de gráficos de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio *diagnóstico de gráficos* es un conjunto de herramientas para grabar y, a continuación, analizar los problemas de representación y rendimiento en aplicaciones de Direct3D. Diagnóstico de gráficos puede usarse con aplicaciones que se ejecutan localmente en su PC de Windows, en un emulador de dispositivos de Windows o en un dispositivo o equipo remoto.  
  
## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>Usar Diagnóstico de gráficos para depurar problemas de representación  
 La depuración de problemas de representación en una aplicación repleta de gráficos no es tan sencilla como iniciar un depurador y recorrer el código. En cada fotograma se producen cientos de miles de píxeles únicos, cada uno según un conjunto complejo de estado, datos, parámetros y código, de los cuales quizás solo algunos píxeles muestren el problema que intenta diagnosticar. Para complicar aún más las cosas, el código que genera cada píxel se ejecuta en hardware especializado que procesa cientos de píxeles en paralelo. Las herramientas y técnicas de depuración tradicionales, difíciles de utilizar incluso en código con pocos subprocesos, son ineficaces cuando hay que hacer frente a tantos datos.  
  
 Las herramientas de Diagnóstico de gráficos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] están diseñadas para ayudarle a encontrar problemas de representación a partir de los artefactos visuales que indican el problema y, a continuación, remontarse al origen del problema centrándose únicamente en el código del sombreador, las etapas de canalización, las llamadas de dibujo, los recursos y el estado del dispositivo pertinentes en el propio código fuente de la aplicación.  
  
## <a name="directx-version-compatibility"></a>Compatibilidad de versiones de DirectX  
 Diagnóstico de gráficos admite aplicaciones que usan Direct3D 12, Direct3D 11 y Direct3D 10, y proporciona compatibilidad limitada para las aplicaciones que usan Direct2D. No admite las aplicaciones que usan versiones anteriores de Direct3D, DirectDraw u otras API gráficas.  
  
### <a name="windows-10-and-direct3d-12"></a>Windows 10 y Direct3D 12  
 Windows 10 presenta la próxima versión de Direct3D, *Direct3D 12*, que es sustancialmente diferente de Direct3D 10 y Direct3D 11. Estas diferencias vuelven a colocar a DirectX a la altura del hardware gráfico moderno y liberan todo su potencial, pero también suponen grandes cambios en la API y aumentan la responsabilidad del programador para administrar la duración y la contención de los recursos. Para ayudar a los programadores de gráficos a realizar esta transición, es fundamental contar con buenas herramientas de depuración, por lo que Diagnóstico de gráficos en Visual Studio 2015 es compatible con Direct3D12 desde el primer momento. A pesar de las diferencias, Diagnóstico de gráficos con Direct3D 12 mantiene la paridad de características con Diagnóstico de gráficos con Direct3D 11.2, a excepción, actualmente, de la característica Análisis de fotogramas. Pronto se agregará compatibilidad para Análisis de fotogramas en Direct3D 12, a lo que seguirán nuevas herramientas de diagnóstico para ayudar a resolver los nuevos tipos de errores que pueden surgir en Direct3D 12.  
  
 Windows 10 también mantiene la compatibilidad con versiones anteriores de Direct3D y con los juegos y aplicaciones que dependen de ellas. Diagnóstico de gráficos en Visual Studio 2015 sigue siendo compatible con Direct3D 10 y Direct3D 11 en Windows 10, al igual que en Windows 8.1.  
  
### <a name="windows-81-and-direct3d-112"></a>Windows 8.1 y Direct3D 11.2  
 En [!INCLUDE[win81](../includes/win81-md.md)], DirectX 11.2 introduce nuevas características que incluyen compatibilidad para capturar información de gráficos durante el tiempo de ejecución. [!INCLUDE[win81](../includes/win81-md.md)] utiliza la nueva captura basada en tiempo de ejecución, conocido como *captura robusta*, exclusivamente para todas las versiones de DirectX que [!INCLUDE[win81](../includes/win81-md.md)] admite. La captura robusta también admite nuevas características de Direct3D 11.2.  
  
### <a name="limited-direct2d-support"></a>Compatibilidad limitada con Direct2D  
 Como Direct2D es una API de modo de usuario basada en Direct3D, puede utilizar Diagnóstico de gráficos para ayudar a depurar problemas de representación en aplicaciones que usan Direct2D. Sin embargo, puesto que, en lugar de los eventos de alto nivel de Direct2D, solo se registran los eventos subyacentes de Direct3D, los eventos de Direct2D no aparecerán en la lista de eventos de gráficos. Además, como la relación entre los eventos de Direct2D y los eventos resultantes de Direct3D no siempre está clara, el uso de Diagnóstico de gráficos para depurar problemas de representación en aplicaciones que utilizan Direct2D no es sencillo. No obstante, puede utilizar Diagnóstico de gráficos para obtener información sobres problemas de representación de bajo nivel en aplicaciones que utilizan Direct2D.  
  
## <a name="graphics-diagnostics-features-in-visual-studio"></a>Características de Diagnóstico de gráficos en Visual Studio  
 Diagnóstico de gráficos tiene una interfaz dedicada, la ventana del Analizador de gráficos, para diagnosticar problemas de representación, pero también agrega algunas herramientas a la interfaz de Visual Studio.  
  
### <a name="the-graphics-toolbar-visual-studio"></a>La barra de herramientas Gráficos (Visual Studio)  
 La barra de herramientas Gráficos proporciona acceso directo a los comandos de Diagnóstico de gráficos.  
  
 El **Iniciar diagnóstico** botón ejecuta la aplicación en diagnóstico de gráficos. Cuando se ejecuta una aplicación en diagnóstico de gráficos, el **capturar el siguiente fotograma presentado** botón está habilitado.  
  
### <a name="diagnostics-capture-interface"></a>Interfaz de captura de diagnóstico  
 Cuando se ejecuta una aplicación en Diagnóstico de gráficos, Visual Studio muestra una interfaz de sesión de diagnóstico que se puede utilizar para capturar fotogramas y que también muestra la carga actual de CPU y GPU. Se muestra la carga de CPU y GPU para ayudarle a identificar los fotogramas que desee capturar debido a sus características de rendimiento, y no a sus errores de representación.  
  
 Pero esta no es la única forma de capturar fotogramas. Puede usar también la interfaz de captura mediante programación o el programa de línea de comandos de captura, dxcap.exe.  
  
 Consulte [capturar información de gráficos](../debugger/capturing-graphics-information.md) para obtener más información.  
  
### <a name="gpu-usage"></a>Uso de GPU  
 Diagnóstico de gráficos también puede generar un perfil de rendimiento de la aplicación Direct3D. Para evitar que los datos del perfil resulten sesgados a causa de la grabación de detalles de eventos gráficos, esta función está separada de la captura de fotogramas que se usará con el Analizador de gráficos.  
  
 Consulte [uso de GPU](../debugger/gpu-usage.md) para obtener más información.  
  
### <a name="directx-control-panel"></a>Panel de control de DirectX  
 El panel de control de DirectX es un componente de DirectX que puede utilizar para cambiar la forma en que DirectX se comporta; por ejemplo, puede habilitar la versión de depuración de los componentes de tiempo de ejecución de DirectX, seleccionar la clase de mensajes de depuración que se notifican e impedir el uso de ciertas funciones del hardware gráfico para emular el hardware menos eficaz. Este nivel de control sobre DirectX puede ayudarle a depurar y probar la aplicación DirectX. Puede acceder al panel de control de DirectX desde Visual Studio.  
  
##### <a name="to-open-the-directx-control-panel"></a>Para abrir el panel de control de DirectX  
  
-   En la barra de menús, elija **depurar**, **gráficos**, **Panel de Control de DirectX**.  
  
## <a name="graphics-analyzer"></a>Analizador de gráficos  
 El Analizador de gráficos de Visual Studio es una interfaz dedicada para examinar los problemas de representación y de rendimiento en fotogramas que ya se ha capturado. Dentro del Analizador de gráficos encontrará varias herramientas que le ayudarán a explorar y comprender el comportamiento de representación de la aplicación. Cada herramienta expone un tipo diferente de información acerca del fotograma que se va a inspeccionar, y todas están diseñadas para utilizarse conjuntamente y delimitar intuitivamente el origen de un problema de representación a partir de la su aparición en el búfer de fotogramas.  
  
 Esta ilustración muestra un diseño típico de herramientas en el Analizador de gráficos.  
  
 ![Todos los gráficos ventanas del depurador](../debugger/media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")  
  
### <a name="the-graphics-toolbar-graphics-analyzer"></a>Barra de herramientas Gráficos (Analizador de gráficos)  
 La barra de herramientas Gráficos proporciona acceso directo a las ventanas del Analizador de gráficos.  
  
 ![La barra de herramientas de gráficos en modo de diagnóstico de gráficos](../debugger/media/vsg-toolbar.png "vsg_toolbar")  
  
### <a name="graphics-log-document"></a>Documento de registro de gráficos  
 En el Analizador de gráficos, el documento de registro de gráficos es la ventana de herramientas más destacada. Esta ventana representa todos los fotogramas capturados mediante la ejecución de la aplicación en Diagnóstico de gráficos. Desde aquí, puede seleccionar el fotograma que desea examinar o seleccionar un píxel concreto para examinarlo con la herramienta Historial de píxeles. La imagen del búfer de fotogramas que muestra este documento cambia para reflejar el evento seleccionado, de forma que pueda ver cómo cambia el búfer de fotogramas con el tiempo.  
  
 El [documento de registro de gráficos](../debugger/graphics-log-document.md) es también el punto de entrada a la herramienta de análisis de fotogramas, que le ayudará a comprender el rendimiento de un marco cambiando la manera en que se configuran ciertos aspectos de la representación y proporciona los resultados de pruebas comparativas para comparar con el original.  
  
### <a name="event-list"></a>Lista de eventos  
 Los eventos gráficos recogen todas las llamadas a la API de Direct3D y los eventos definidos por el usuario.  
  
 El [lista de eventos](../debugger/graphics-event-list.md) muestra todos los eventos de gráficos que se registraron durante el fotograma que está examinando. Para ayudarle a encontrar lo más relevante, la lista de eventos puede verse de forma jerárquica, con los cambios de estado recientes debajo la subsiguiente llamada a draw, o como una escala de tiempo. Además, los eventos están codificados con colores según la cola a la que pertenecen y puede filtrar la lista para incluir sólo los eventos que le interesan.  
  
 Al seleccionar un evento en la lista, el resto de las herramientas de Análisis de gráficos reflejan el estado del fotograma en el momento de ese evento. De esta manera, puede ver el efecto de cualquier evento en la GPU. Por ejemplo, verá el efecto inmediato de cualquier llamada a draw en el búfer de fotogramas, incluso si queda oculta por llamadas a draw subsiguientes. Algunos eventos tienen también hipervínculos que puede seguir para ver más detalles sobre sus parámetros u objetos de recurso relacionados.  
  
### <a name="pipeline-stages"></a>Etapas de canalización  
 Cada llamada a draw de su aplicación pasa por la canalización de gráficos que proporciona Direct3D. En cada fase de la canalización, el resultado de la fase anterior es transformado por un pequeño programa, denominado sombreador, y, a continuación, pasa a la fase siguiente hasta que finalmente se representa en la pantalla. Se producen muchos errores de representación en el límite entre fases de canalización cuando el formato de salida es distinto del que espera la etapa siguiente o simplemente cuando una de las fases produce resultados incorrectos. Normalmente, solo se obtiene el resultado final tal y como se verá en la pantalla y no es fácil distinguir en qué punto de la canalización se produjo el error.  
  
 El [etapas de canalización](../debugger/graphics-pipeline-stages.md) ventana muestra el resultado de cada fase de forma independiente, por lo que se puede determinar en qué fase más fácilmente un problema de representación aparece por primera vez en. Una vez determinada la fase, puede comenzar a depurar a su sombreador directamente desde la ventana Etapas de canalización.  
  
### <a name="graphics-state"></a>Estado de gráficos  
 Las operaciones de representación dependen mucho de un estado que suele estar repartido entre varios objetos. Muchos tipos de problemas de representación están provocados por el una configuración de estado errónea.  
  
 El [estado](../debugger/graphics-state.md) ventana recopila la información de estado pertinente para cada llamada a draw en un solo lugar, por lo que es más fácil de encontrar, y también la información destacada de los cambios de estado que se han producido desde la anterior llamada a draw.  
  
### <a name="pixel-history"></a>Historial de píxeles  
 En casos complejos, no es raro que el sombreado se aplique varias veces a un píxel en un solo fotograma. A veces, el color anterior se sobrescribe, pero otras veces se combinan los colores para lograr efectos como la transparencia. Cuando el resultado de combinarlos no tiene el aspecto correcto, no es fácil saber si se debe a que uno de los colores es incorrecto o si hay un problema con la forma en se combinan. En otras ocasiones, puede parecer que falta un objeto porque se rechazó su contribución al píxel por algún motivo.  
  
 El [historial de píxeles](../debugger/graphics-pixel-history.md) ventana visualiza el historial completo de sombreador de cada píxel del fotograma, incluidas las contribuciones rechazadas. Para las contribuciones que no se han rechazado, muestra los resultados del sombreado sin procesar y cómo se combina cada color nuevo con el anterior. Con esta información, es mucho más fácil encontrar el origen de errores en píxeles mezclan resultados del sombreador y saber si falta objeto representado falta porque su contribución al píxel se rechazó indebidamente.  
  
### <a name="event-call-stack"></a>Pila de llamadas de eventos  
 El código del sombreador no es la única fuente de problemas de representación en una aplicación de Direct3D; a veces, el código fuente de la aplicación pasa el parámetro incorrecto o no configura Direct3D correctamente. Un tipo de error que puede detectar con más facilidad gracias a la función Historial de píxeles es cuando falta un objeto representado porque se han rechazado todas sus píxeles. Este tipo de error ocurre normalmente cuando se configura incorrectamente un valor, como el valor que controla cómo se realiza la prueba de profundidad, y suele encontrarse en alguna parte de la pila de llamadas a draw del objeto falta.  
  
 El [pila de llamadas de eventos](../debugger/graphics-event-call-stack.md) ventana muestra la pila de llamadas completa de cada evento de gráficos en la lista de eventos y código fuente de incluso permite saltar a la aplicación si está disponible la información de depuración. Se trata de una herramienta eficaz para hacer el seguimiento de un error desde el lugar en que aparece por primera vez, en la GPU, hasta donde se origina en el código fuente de la aplicación.  
  
### <a name="object-table"></a>Tabla de objetos  
 Cada fotograma que representa su aplicación está probablemente respaldado por cientos o incluso miles de objetos de recursos. Puede tratarse de búferes de reserva y destinos de representación, texturas, búferes de vértices, búferes de índice, búferes generales..., casi todo lo que Direct3D recuerda como un objeto.  
  
 El [tabla de objetos](../debugger/graphics-object-table.md) muestra todos los objetos que existen en el momento del evento de gráficos seleccionado en la lista de eventos. Puesto que la mayoría de los objetos en una aplicación típica son texturas, la lista de eventos está optimizada para mostrar de un vistazo los detalles pertinentes para las imágenes. La columna Tipo indica el tipo de objeto que se encuentra en cada fila, y la columna Formato muestra el subtipo o la versión del objeto. También se muestran otros detalles. Algunos objetos cuentan también con hipervínculos que puede seguir para usar un visor más especializado al visualizar objetos como texturas (puede ver la textura como una imagen) o búferes (puede elegir la forma en que el visor de búfer analiza y muestra los bytes del búfer sin formato definiendo el formato del búfer).  
  
### <a name="frame-analysis"></a>Análisis de fotogramas  
 Los gráficos de su aplicación no solo deben ser correctos; además, deben ser rápidos. Incluso en dispositivos menos potentes, como equipos portátiles con gráficos integrados o teléfonos móviles. Y también deben tener una apariencia inmejorable.  
  
 El [análisis de fotogramas](../debugger/graphics-frame-analysis.md) herramienta explora las posibles optimizaciones del rendimiento cambiando automáticamente la forma en la aplicación usa Direct3D y proporciona los resultados de pruebas comparativas para la comparación. Por ejemplo, Análisis de fotogramas puede habilitar la asignación de MIP en todas las texturas, lo que podría revelar qué texturas podrían beneficiarse de la asignación de MIP pero actualmente no tienen habilitado. Si el hardware lo admite, Análisis de fotogramas presenta también la información recopilada de los contadores de rendimiento de la GPU. Este nivel de información puede identificar problemas de rendimiento relacionados con el hardware, como un número alto de detenciones al obtener texturas o de líneas no ejecutadas de caché.  
  
 Pero Análisis de fotogramas no consiste solo en ganar rapidez; consiste también en obtener el máximo rendimiento que pueda mientras renuncia a la menor cantidad de calidad visual. En ocasiones, un efecto costoso que se ve genial en una pantalla grande no tiene el mismo efecto cuando se ve en la pantalla pequeña de un teléfono, donde un efecto más sencillo podría ser igual de vistoso sin agotar la batería. Los cambios automáticos y las pruebas comparativas que proporciona Análisis de gráficos pueden ayudarle a encontrar el equilibrio adecuado para su aplicación en diversos dispositivos.  
  
## <a name="see-also"></a>Vea también  
 [Herramienta de captura de línea de comandos](../debugger/command-line-capture-tool.md)   
 [Depurador de HLSL](../debugger/hlsl-shader-debugger.md)



