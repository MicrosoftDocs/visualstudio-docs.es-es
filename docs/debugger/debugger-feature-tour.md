---
title: 'Guía de características: el depurador Visual Studio | Documentos de Microsoft'
description: Dé un paseo por el depurador de Visual Studio
ms.custom: mvc
ms.date: 03/27/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb84fbfa4b8916b963f3f3cc35e044593c5a47e1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="quickstart-first-look-at-the-visual-studio-debugger"></a>Inicio rápido: Busque primero en el depurador de Visual Studio

En este tema se presenta las características del depurador de Visual Studio. Si desea seguir el tutorial abriendo su propia aplicación en Visual Studio, puede hacerlo o bien puede seguir junto con una aplicación de ejemplo con el [guía para principiantes](../debugger/getting-started-with-the-debugger.md).

Las características descritas aquí son aplicables a C#, C++, Visual Basic, JavaScript y otros lenguajes compatibles con Visual Studio (excepto donde se indicó).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Establecer un punto de interrupción e iniciar el depurador

Para depurar, debe iniciar la aplicación con el depurador asociado al proceso de aplicación. F5 (**Depurar > Iniciar depuración**) es la manera más común de hacerlo. Sin embargo, en estos momentos no hayan podido establecer puntos de interrupción para examinar la aplicación de código, por lo que se realice primero y, a continuación, iniciar la depuración.

Si tiene un archivo abierto en el editor de código, puede establecer un punto de interrupción, haga clic en el margen situado a la izquierda de una línea de código.

![Establecer un punto de interrupción](../debugger/media/dbg-tour-set-a-breakpoint.gif "establecer un punto de interrupción")

Presione F5 (**Depurar > Iniciar depuración**) y el depurador ejecuta hasta el primer punto de interrupción que encuentre. Si la aplicación no se está ejecutando, F5 inicia al depurador y se detiene en el primer punto de interrupción.

Los puntos de interrupción son una característica útil si conoce la línea de código o la sección de código que se va a examinar en detalle.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegar por el código en el depurador mediante comandos de paso

Se proporcionan métodos abreviados de teclado para casi todos los comandos porque simplifican la exploración del código de la aplicación más rápido. (Equivalente comandos como comandos de menú se muestran entre paréntesis).

Para iniciar la aplicación con el depurador adjunto, presiona F11 (**Depurar > Depurar paso a paso**). F11 es el **paso a paso** comando y hace avanzar la una instrucción ejecución de aplicación a la vez. Cuando se inicia la aplicación con F11, el depurador se interrumpe en la primera instrucción que se ejecuta.

![F11 Paso a paso](../debugger/media/dbg-tour-f11.png "F11 paso a paso")

La flecha amarilla representa la instrucción en el que el depurador está en pausa, que también suspende la ejecución de la aplicación en el mismo punto (esta instrucción no se ha ejecutado).

F11 es una buena manera de examinar el flujo de ejecución en el nivel más detallado. (Para mover contenidos más rápido a través del código, le mostramos algunas otras opciones.) De forma predeterminada, el depurador omite los código de no usuario (si desea obtener más información, consulte [solo mi código](../debugger/just-my-code.md)).

>[!NOTE]
> En código administrado, verá un cuadro de diálogo que le pregunta si desea recibir una notificación cuando automáticamente saltar propiedades y operadores (comportamiento predeterminado). Si desea cambiar la configuración más adelante, deshabilitar **saltar propiedades y operadores** en el **Herramientas > opciones** menú situado bajo **depuración**.

## <a name="step-over-code-to-skip-functions"></a>Recorrer el código que se omiten las funciones

Cuando se encuentra en una línea de código que es una llamada de función o un método, puede presionar F10 (**Depurar > paso a paso por**) en lugar de F11.

F10 hace avanzar al depurador sin entrar en funciones o métodos en el código de la aplicación (todavía se ejecuta el código). Presionando F10, puede saltarse código que no le interesa. De esta manera, puede obtener rápidamente al código que más le interesen.

## <a name="step-into-a-property"></a>Ir a una propiedad

Como se mencionó anteriormente, de forma predeterminada, el depurador omite las propiedades administradas y los campos, pero la **ir a específico** comando le permite invalidar este comportamiento.

Haga doble clic en una propiedad o campo y elija **ir a específico**, a continuación, elija una de las opciones disponibles.

![Ir a específico](../debugger/media/dbg-tour-step-into-specific.png "paso a paso específico")

En este ejemplo, **ir a específico** nos obtiene al código de `Path.set`.

![Ir a específico](../debugger/media/dbg-tour-step-into-specific-2.png "paso a paso específico")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Ejecutar hasta un punto en el código rápidamente mediante el mouse

En el depurador, mantenga el mouse sobre una línea de código hasta que el **ejecutar, haga clic en** botón (ejecución aquí) ![ejecutar, haga clic en](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece a la izquierda.

![Ejecutar, haga clic en](../debugger/media/dbg-tour-run-to-click-2.png "ejecutar, haga clic en")

>  [!NOTE] 
> El **ejecutar, haga clic en** botón (ejecución aquí) es una novedad en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Haga clic en el **ejecutar, haga clic en** botón (ejecución aquí). El depurador avanza a la línea de código donde ha hecho clic.

Mediante este botón es similar a establecer un punto de interrupción temporal. Este comando también es útil para desplazarse rápidamente dentro de un área visible del código de la aplicación. Puede usar **ejecutar, haga clic en** en cualquier archivo abierto.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Avanzar al depurador hasta salir de la función actual

A veces, desea continuar la sesión de depuración pero avanza al depurador completamente a través de la función actual.

Presione MAYÚS + F11 (o **Depurar > Salir**).

Este comando reanuda la ejecución de la aplicación (y hace avanzar el depurador) hasta que regresa la función actual.

## <a name="run-to-cursor"></a>Ejecutar hasta el cursor

Detenga el depurador presionando el **Detener depuración** botón rojo ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Detener depuración") o MAYÚS + F5.

Haga clic en una línea de código de la aplicación y elija **ejecutar hasta el Cursor**. Este comando inicia la depuración y establece un punto de interrupción temporal en la línea de código actual.

![Ejecutar hasta el Cursor](../debugger/media/dbg-tour-run-to-cursor.png "ejecutar hasta el Cursor")

Si ha configurado los puntos de interrupción, el depurador se detiene en el primer punto de interrupción que se produce.

Presione F5 para llegar a la línea de código si seleccionas **ejecutar hasta el Cursor**.

Este comando es útil cuando se edita código y desea establecer un punto de interrupción temporal rápidamente e iniciar al depurador.


> [!NOTE]
> Puede usar **ejecutar hasta el Cursor** en el **pila de llamadas** ventana mientras está depurando.

## <a name="restart-your-app-quickly"></a>Reinicie la aplicación rápidamente

Haga clic en el **reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "Reiniciar aplicación") botón en la barra de herramientas Depurar (**Ctrl + Mayús + F5**).

Cuando se presiona **reiniciar**, le permite ahorrar tiempo frente a la aplicación de detener y reiniciar el depurador. El depurador se detiene en el primer punto de interrupción se visita mediante la ejecución de código.

Si desea detener el depurador y recibir de nuevo en el editor de código, puede presionar la detención en rojo ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Detener depuración") botón en lugar de **reiniciar**.

## <a name="inspect-variables-with-data-tips"></a>Inspeccionar las variables con sugerencias de datos

Ahora que sabe cómo usar un poco, tener una buena oportunidad para iniciar inspeccionar el estado de la aplicación (variables) con el depurador. Características que permiten inspeccionar las variables son algunas de las características más útiles del depurador, y hay diferentes maneras de hacerlo. A menudo, cuando se intenta depurar un problema, está intentando averigüe si las variables almacena los valores que se esperan que tengan en un estado de aplicación determinada.

Mientras está en pausa en el depurador, mantenga el mouse sobre un objeto con el mouse y verá que su valor de propiedad predeterminado (en este ejemplo, el nombre de archivo `market 031.jpg` es el valor de propiedad predeterminado).

![Ver información sobre datos](../debugger/media/dbg-tour-data-tips.gif "ver una sugerencia de datos")

Expanda el objeto para ver todas sus propiedades (como el `FullPath` propiedad en este ejemplo).

A menudo, durante la depuración, desee una forma rápida de comprobar los valores de propiedad en objetos y las sugerencias de datos son una buena manera de hacerlo.

> [!TIP]
> En los lenguajes más compatibles, puede editar código en el medio de una sesión de depuración. Para obtener más información, consulte [editar y continuar](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspeccionar las variables con las ventanas automático y variables locales

Durante la depuración, mire el **automático** ventana en la parte inferior del editor de código.

![Automático ventana](../debugger/media/dbg-tour-autos-window.png "ventana automático")

En el **automático** , ver variables junto con su valor actual y su tipo. El **automático** ventana muestra todas las variables utilizadas en la línea actual o en la línea anterior (en C++, la ventana muestra las variables en las tres líneas de código anteriores. Compruebe la documentación para el comportamiento específico del idioma).

> [!NOTE]
> En JavaScript, el **locales** ventana es compatible pero no la **automático** ventana.

A continuación, examine la **locales** ventana. El **locales** ventana muestra las variables que están actualmente en el ámbito.

![Ventana variables locales](../debugger/media/dbg-tour-locals-window.png "ventana variables locales")

En este ejemplo, el `this` objeto y el objeto `f` están en el ámbito. Para obtener más información, consulte [inspeccionar las Variables en las ventanas de variables locales y automático](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Establece una inspección

Puede usar un **inspección** ventana para especificar una variable (o una expresión) que desea que esté atento en.

Durante la depuración, haga clic en un objeto y elija **Agregar inspección**.

![Ventana Inspección](../debugger/media/dbg-tour-watch-window.png "ventana Inspección")

En este ejemplo, tiene una inspección activada la `File` objeto y se puede ver su valor cambia conforme se desplaza por el depurador. A diferencia de las otras ventanas de variables, la **inspección** windows Mostrar siempre las variables que está viendo (están atenuadas cuando sale del ámbito).

Para obtener más información, consulte [establece una inspección mediante la inspección y las ventanas de inspección rápida](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Examinar la pila de llamadas

Haga clic en el **pila de llamadas** ventana mientras está depurando, que está abierto en el panel inferior derecho de forma predeterminada.

![Examinar la pila de llamadas](../debugger/media/dbg-tour-call-stack.png "examinar la pila de llamadas")

El **pila de llamadas** ventana muestra el orden en el que se esté llamando métodos y funciones. La primera línea muestra la función actual (la `Update` método en este ejemplo). La segunda línea muestra que `Update` se ha llamado desde el `Path.set` propiedad y así sucesivamente. La pila de llamadas es una buena forma de examinar y comprender el flujo de ejecución de una aplicación.

> [!NOTE]
> El **pila de llamadas** ventana es similar a la perspectiva de la depuración de algunos IDE como Eclipse.

Haga doble clic en una línea de código que se vaya a ver ese código de origen y que también cambia el ámbito actual va a inspeccionar el depurador. Esto no hace avanzar al depurador.

También puede utilizar los menús contextuales de la **pila de llamadas** ventana para realizar otras actividades. Por ejemplo, puede insertar los puntos de interrupción en funciones específicas, reinicie la aplicación con **ejecutar hasta el Cursor**y para ir a examinar el código fuente. Vea [Cómo: examinar la pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a>Examinar una excepción

Cuando la aplicación produce una excepción, el depurador le lleva a la línea de código que produjo la excepción.
     
![Aplicación auxiliar de excepciones](../debugger/media/dbg-tour-exception-helper.png "aplicación auxiliar de excepciones")

En este ejemplo, el **aplicación auxiliar de excepciones** muestra un `System.Argument` excepción y un mensaje de error que indica que la ruta de acceso no es un formato válido. Por lo tanto, sabemos que se produjo el error en un argumento de método o función.

En este ejemplo, el `DirectoryInfo` llamada dio el error en la cadena vacía que se almacenan en la `value` variable.

La aplicación auxiliar de excepciones es una característica excelente que puede ayudarle a depurar los errores. También puede hacer cosas como vista de detalles del error y agregue una inspección de la aplicación auxiliar de excepciones. O bien, si es necesario, puede cambiar las condiciones para producir la excepción concreta.

>  [!NOTE] 
> Reemplaza el Asistente de excepciones en la aplicación auxiliar de excepciones [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Expanda el **configuración de excepciones** nodo para ver más opciones controlar este tipo de excepción, pero no es necesario cambiar ninguna acción para este paseo le!

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Depurar aplicaciones ASP.NET en vivo en el servicio de aplicación de Azure

el **depurador instantánea** toma una instantánea de las aplicaciones de producción cuando se ejecuta código que le interesa. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

![Iniciar el depurador de instantánea](../debugger/media/snapshot-launch.png "iniciar el depurador de instantánea")

Recopilación de instantáneas está disponible para aplicaciones de ASP.NET que se ejecutan en el servicio de aplicación de Azure. Las aplicaciones ASP.NET deben ejecutarse en .NET Framework 4.6.1 o versiones posteriores, y las aplicaciones de ASP.NET Core deben estar ejecutándose en .NET Core 2.0 o posterior en Windows.

Para obtener más información, consulte [depurar aplicaciones ASP.NET en directo con el depurador de instantánea](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Ver las instantáneas con devolución de paso de IntelliTrace (Visual Studio Enterprise)

**Devolución de IntelliTrace paso** automáticamente toma una instantánea de la aplicación en cada punto de interrupción y el depurador de evento de paso. Las instantáneas registradas le permiten volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior. La característica step-back de IntelliTrace puede permitirle ahorrar tiempo cuando desea ver el estado anterior de la aplicación, pero no desea reiniciar la depuración ni volver a crear el estado de aplicación que se desea.

Para poder navegar y ver las instantáneas, use los botones **Retroceder paso a paso** y **Avanzar paso a paso** en la barra de herramientas de depuración. Estos botones permiten navegar por los eventos que aparecen en la pestaña **Eventos** en la ventana **Herramientas de diagnóstico**.

![Paso hacia atrás y hacia delante botones](../debugger/media/intellitrace-step-back-icons-description.png  "botones paso hacia atrás y hacia delante")  

Para más información, consulte la página [Visualización de instantáneas mediante step-back de IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md).

## <a name="more-features-to-look-at"></a>Más características para buscar en

-   [Sugerencias y trucos del depurador](../debugger/debugger-tips-and-tricks.md) obtener información sobre cómo aumentar su productividad con el depurador.

-   [Editar y continuar](../debugger/edit-and-continue.md) para un subconjunto de idiomas (C#, C++, Visual Basic), la característica Editar y continuar permite editar código en el medio de una sesión de depuración.

-   [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md) describe cómo depurar aplicaciones multiproceso. 

-   [Depuración remota](../debugger/remote-debugging.md) describe cómo depurar aplicaciones que se ejecutan en otros equipos o dispositivos. 
  
-   [IntelliTrace](../debugger/intellitrace.md) describe la característica de IntelliTrace en Visual Studio Enterprise. Puede usarlo para el registro y seguimiento de historial de ejecución de su código.

-   [Uso de red](../profiling/network-usage.md) describe una herramienta de generación de perfiles que se puede utilizar para depurar servicios web y otros recursos de red en las aplicaciones universales de Windows (UWP). Utilice la herramienta para examinar cargas.

-   [Debug Interface Access SDK](../debugger/debug-interface-access/debug-interface-access-sdk.md) describe el Kit de desarrollo de Software de Microsoft Debug Interface Access (SDK de DIA). El SDK de DIA proporciona acceso a información de depuración almacenada en archivos de base de datos de programa (.pdb) generados por herramientas de postcompilador de Microsoft.  

## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/index.md)
