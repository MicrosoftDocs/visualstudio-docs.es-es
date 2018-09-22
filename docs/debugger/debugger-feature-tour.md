---
title: Empezar a depurar en VS 2017
description: Empezar a depurar aplicaciones mediante el depurador de Visual Studio
ms.custom: mvc
ms.date: 06/15/2018
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
ms.openlocfilehash: e2339dcfe80e994b8bc9062d137263d3b25d274d
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542421"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Primer vistazo al depurador de Visual Studio

Este tema presentan las herramientas proporcionadas por Visual Studio del depurador. En el contexto de Visual Studio, cuando se *depurar la aplicación*, suele significar que se está ejecutando la aplicación con el depurador asociado (es decir, en el modo del depurador). Al hacerlo, el depurador proporciona muchas formas de ver lo que hace el código mientras se ejecuta. Puede ver los valores almacenados en variables y recorrer el código, puede establecer inspecciones de variables para ver cuando cambian los valores, puede examinar la ruta de acceso de ejecución del código, et al. Si se trata de la primera vez que ha probado para depurar el código, es posible que desea leer [de depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) antes de pasar a través de este tema.

Las características descritas aquí son aplicables a C#, C++, Visual Basic, JavaScript y otros lenguajes compatibles con Visual Studio (excepto donde se indique).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Establecer un punto de interrupción e iniciar el depurador

Para depurar, deberá iniciar la aplicación con el depurador asociado al proceso de la aplicación. **F5** (**Depurar > Iniciar depuración**) es la manera más común de hacerlo. Sin embargo, en estos momentos no es posible que ha establecido ningún punto de interrupción para examinar la aplicación de código, por lo que se realizará primero y, a continuación, iniciar la depuración. Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código. 

Si tiene un archivo abierto en el editor de código, puede establecer un punto de interrupción, haga clic en el margen situado a la izquierda de una línea de código.

![Establezca un punto de interrupción](../debugger/media/dbg-tour-set-a-breakpoint.gif "establecer un punto de interrupción")

Presione **F5** (**Depurar > Iniciar depuración**) o el **Iniciar depuración** botón ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración ") en la barra de herramientas de depuración y se ejecuta el depurador para el primer punto de interrupción que encuentra. Si aún no se ejecuta la aplicación, F5 inicia al depurador y se detiene en el primer punto de interrupción.

Puntos de interrupción son una característica muy útil cuando se sabe que la línea de código o en la sección de código que desea examinar con detalle.

## <a name="navigate"></a> Navegar por el código en el depurador mediante comandos de paso

Se proporcionan métodos abreviados de teclado para la mayoría de los comandos porque hacen que la exploración del código de aplicación más rápido. (Equivalente a comandos, como los comandos de menú se muestran entre paréntesis).

Para iniciar la aplicación con el depurador adjunto, presione **F11** (**Depurar > paso a paso**). F11 es el **paso a paso** comando y hace avanzar la una instrucción ejecución de aplicación a la vez. Cuando se inicia la aplicación con F11, el depurador se interrumpe en la primera instrucción que se ejecuta.

![F11 Paso a paso](../debugger/media/dbg-tour-f11.png "F11 paso a paso")

La flecha amarilla representa la instrucción en el que el depurador está en pausa, que también suspende la ejecución de la aplicación en el mismo punto (esta instrucción no se ha ejecutado).

F11 es una buena manera para examinar el flujo de ejecución en el nivel más detallado. (Para mover más rápido a través del código, le mostraremos algunas otras opciones.) De forma predeterminada, el depurador omite el código de no usuario (si desea obtener más información, consulte [solo mi código](../debugger/just-my-code.md)).

>[!NOTE]
> En código administrado, verá un cuadro de diálogo que le pregunta si desea recibir una notificación cuando automáticamente saltar propiedades y operadores (comportamiento predeterminado). Si desea cambiar la configuración más adelante, deshabilitar **saltar propiedades y operadores** en el **Herramientas > opciones** menú bajo **depuración**.

## <a name="step-over-code-to-skip-functions"></a>Recorrer el código para omitir las funciones

Cuando se encuentra en una línea de código que es una llamada de función o método, puede presionar **F10** (**Depurar > saltar**) en lugar de F11.

F10 hace avanzar al depurador sin entrar en las funciones o métodos en el código de aplicación (todavía se ejecuta el código). Presione F10, puede omitir con respecto al código que no le interesa. De este modo, puede obtener rápidamente al código que más le interesen.

## <a name="step-into-a-property"></a>Ir a una propiedad

Como se mencionó anteriormente, de forma predeterminada, el depurador omite las propiedades administradas y campos, pero la **ir a específico** comando le permite invalidar este comportamiento.

Haga doble clic en un campo o propiedad y elija **ir a específico**, a continuación, elija una de las opciones disponibles.

![Ir a específico](../debugger/media/dbg-tour-step-into-specific.png "ir a específico")

En este ejemplo, **ir a específico** nos obtiene al código de `Path.set`.

![Ir a específico](../debugger/media/dbg-tour-step-into-specific-2.png "ir a específico")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Ejecutar hasta un punto en su código rápidamente con el mouse

En el depurador, mantenga el mouse sobre una línea de código hasta la **hacer clic y ejecutar** botón (ejecutar hasta aquí) ![hacer clic y ejecutar](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece a la izquierda.

![Hacer clic y ejecutar](../debugger/media/dbg-tour-run-to-click-2.png "hacer clic y ejecutar")

> [!NOTE]
> El **hacer clic y ejecutar** botón (ejecutar hasta aquí) es nuevo en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Haga clic en el **hacer clic y ejecutar** botón (ejecutar hasta aquí). El depurador avanza a la línea de código donde se hizo clic.

Mediante este botón es similar a la configuración de un punto de interrupción temporal. Este comando también es útil para desplazarse rápidamente dentro de una región visible del código de aplicación. Puede usar **hacer clic y ejecutar** en cualquier archivo abierto.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Avanzar al depurador fuera de la función actual

A veces, desea continuar la sesión de depuración pero avanzar al depurador totalmente a través de la función actual.

Presione **MAYÚS + F11** (o **Depurar > Salir**).

Este comando reanuda la ejecución de la aplicación (y hace avanzar el depurador) hasta que devuelve la función actual.

## <a name="run-to-cursor"></a>Ejecutar hasta el cursor

Detenga el depurador presionando el **Detener depuración** botón rojo ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Detener depuración") o **MAYÚS**  +  **F5**.

Haga clic en una línea de código de la aplicación y elija **ejecutar hasta el Cursor**. Este comando inicia la depuración y establece un punto de interrupción temporal en la línea de código actual.

![Ejecutar hasta el Cursor](../debugger/media/dbg-tour-run-to-cursor.png "ejecutar hasta el Cursor")

Si ha configurado los puntos de interrupción, el depurador se detiene en el primer punto de interrupción que visita.

Presione **F5** hasta llegar a la línea de código si seleccionas **ejecutar hasta el Cursor**.

Este comando resulta útil cuando se edita código y desea establecer un punto de interrupción temporal de rápidamente e iniciar al depurador al mismo tiempo.

> [!NOTE]
> Puede usar **ejecutar hasta el Cursor** en el **pila de llamadas** ventana durante la depuración.

## <a name="restart-your-app-quickly"></a>Reinicie la aplicación rápidamente

Haga clic en el **reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "Reiniciar aplicación") botón en la barra de herramientas Depurar (**Ctrl + Mayús + F5**).

Al presionar **reiniciar**, ahorra tiempo en comparación con la aplicación de detener y reiniciar el depurador. El depurador se detiene en el primer punto de interrupción que se obtiene acceso mediante la ejecución de código.

Si desea detener el depurador y regresar en el editor de código, puede presionar el delimitador de color rojo ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Detener depuración") botón en lugar de **reiniciar**.

## <a name="inspect-variables-with-data-tips"></a>Inspeccionar las variables con sugerencias de datos

Ahora que sabe cómo un poco, tener una buena oportunidad para empezar a inspeccionar el estado de la aplicación (variables) con el depurador. Las características que permiten inspeccionar las variables son algunas de las características más útiles del depurador, y hay diferentes maneras de hacerlo. A menudo, cuando se intenta depurar un problema, está intentando averiguar si las variables almacena los valores que se esperan que tengan un estado de aplicación en particular.

Mientras está en pausa en el depurador, mantenga el mouse sobre un objeto con el mouse y ver su valor de propiedad predeterminado (en este ejemplo, el nombre de archivo `market 031.jpg` es el valor de propiedad predeterminado).

![Ver información sobre datos](../debugger/media/dbg-tour-data-tips.gif "ver una sugerencia de datos")

Expanda el objeto para ver todas sus propiedades (como el `FullPath` propiedad en este ejemplo).

A menudo, cuando se depura, desea que una forma rápida de comprobar los valores de propiedad en objetos, y las sugerencias de datos son una buena forma de hacerlo.

> [!TIP]
> En los lenguajes más compatibles, puede editar código en el medio de una sesión de depuración. Para obtener más información, consulte [editar y continuar](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspeccionar las variables con las ventanas automático y variables locales

Durante la depuración, examine el **automático** ventana en la parte inferior del editor de código.

![Ventana de autos](../debugger/media/dbg-tour-autos-window.png "ventana automático")

En el **automático** , ver variables junto con su valor actual y su tipo. El **automático** ventana muestra todas las variables usadas en la línea actual o la línea anterior (en C++, la ventana muestra las variables en las tres líneas de código anteriores. Consulte la documentación para el comportamiento específico del idioma).

> [!NOTE]
> En JavaScript, la **variables locales** pero no se admite la ventana de la **automático** ventana.

A continuación, examine el **variables locales** ventana. El **variables locales** ventana muestra las variables que están actualmente en el ámbito.

![Ventana variables locales](../debugger/media/dbg-tour-locals-window.png "ventana variables locales")

En este ejemplo, el `this` objeto y el objeto `f` están en el ámbito. Para obtener más información, consulte [inspeccionar Variables en las ventanas motor y variables locales Windows](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Establece una inspección

Puede usar un **inspección** ventana para especificar una variable (o una expresión) que desee vigilar en.

Durante la depuración, haga clic en un objeto y elija **Agregar inspección**.

![Ventana Inspección](../debugger/media/dbg-tour-watch-window.png "ventana Inspección")

En este ejemplo, tiene una inspección establecida en el `f` objeto y puede ver su valor cambia conforme se desplaza por el depurador. A diferencia de las otras ventanas de variables, la **inspección** windows Mostrar siempre las variables que está viendo (están atenuadas cuando fuera del ámbito).

Para obtener más información, consulte [establece una inspección mediante la inspección e inspección rápida Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Examinar la pila de llamadas

Haga clic en el **pila de llamadas** ventana durante la depuración, que está abierto en el panel inferior derecho de forma predeterminada.

![Examinar la pila de llamadas](../debugger/media/dbg-tour-call-stack.png "examinar la pila de llamadas")

El **pila de llamadas** ventana muestra el orden en el que obtener se llaman los métodos y funciones. La línea superior muestra la función actual (la `Update` método en este ejemplo). La segunda línea muestra que `Update` se llamó desde el `Path.set` propiedad y así sucesivamente. La pila de llamadas es una buena manera para examinar y entender el flujo de ejecución de una aplicación.

> [!NOTE]
> El **pila de llamadas** ventana es similar a la perspectiva de depuración de algunos IDE como Eclipse.

Haga doble clic en una línea de código para ir a mirar ese código fuente y que también cambia el ámbito actual va a inspeccionar el depurador. Esto no hace avanzar al depurador.

También puede usar los menús contextuales de la **pila de llamadas** ventana hacer otras cosas. Por ejemplo, puede insertar puntos de interrupción en funciones específicas, reinicie la aplicación mediante **ejecutar hasta el Cursor**y para ir a examinar el código fuente. Consulte [Cómo: examinar la pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="exception"></a> Examinar una excepción

Cuando la aplicación inicia una excepción, el depurador le lleva a la línea de código que produjo la excepción.

![Aplicación auxiliar de excepciones](../debugger/media/dbg-tour-exception-helper.png "aplicación auxiliar de excepciones")

En este ejemplo, el **aplicación auxiliar de excepciones** se muestra un `System.Argument` excepción y un mensaje de error que indica que la ruta de acceso no es un formato válido. Por lo tanto, sabemos que se produjo el error en un argumento de método o función.

En este ejemplo, el `DirectoryInfo` llamada dio el error en la cadena vacía que se almacenan en el `value` variable.

La aplicación auxiliar de excepciones es una característica excelente que puede ayudarle a depurar errores. También puede hacer cosas como vista de detalles del error y agregue una inspección de la aplicación auxiliar de excepciones. O bien, si es necesario, puede cambiar las condiciones para producir la excepción concreta.

>  [!NOTE]
> Reemplaza el Asistente de excepciones en la aplicación auxiliar de excepciones [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Expanda el **configuración de excepciones** nodo para ver más opciones sobre cómo controlar este tipo de excepción, pero no es necesario cambiar nada para este paseo!

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Depurar aplicaciones ASP.NET activas en Azure App Service

el **Snapshot Debugger** toma una instantánea de sus aplicaciones en producción cuando se ejecuta el código que le interesen. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

![Iniciar el depurador de instantáneas](../debugger/media/snapshot-launch.png "iniciar el depurador de instantáneas")

Recopilación de instantáneas está disponible para aplicaciones de ASP.NET que se ejecutan en Azure App Service. Se deben ejecutar las aplicaciones ASP.NET en .NET Framework 4.6.1 o versiones posteriores, y deben estar ejecutando aplicaciones de ASP.NET Core en .NET Core 2.0 o posterior en Windows.

Para obtener más información, consulte [depurar aplicaciones ASP.NET activas con el depurador de instantáneas](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Ver las instantáneas con step-back de IntelliTrace (Visual Studio Enterprise)

**Step-back de IntelliTrace** automáticamente toma una instantánea de la aplicación en cada punto de interrupción y el depurador de evento de paso. Las instantáneas registradas le permiten volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior. La característica step-back de IntelliTrace puede permitirle ahorrar tiempo cuando desea ver el estado anterior de la aplicación, pero no desea reiniciar la depuración ni volver a crear el estado de aplicación que se desea.

Para poder navegar y ver las instantáneas, use los botones **Retroceder paso a paso** y **Avanzar paso a paso** en la barra de herramientas de depuración. Estos botones permiten navegar por los eventos que aparecen en la pestaña **Eventos** en la ventana **Herramientas de diagnóstico**.

![Paso hacia atrás y adelante botones](../debugger/media/intellitrace-step-back-icons-description.png  "botones Retroceder paso a paso y reenviar")

Para obtener más información, consulte el [inspeccionar el estado anterior de aplicación con IntelliTrace](../debugger/view-historical-application-state.md) página.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha tenido un vistazo rápido a las numerosas características del depurador. Es posible que desee una información más detallada sobre estas características mediante una aplicación de ejemplo

> [!div class="nextstepaction"]
> [Información sobre cómo depurar con Visual Studio](../debugger/getting-started-with-the-debugger.md)
