---
title: Primer vistazo al depurador
description: Empiece a depurar aplicaciones mediante el depurador de Visual Studio
ms.custom: ''
ms.date: 04/08/2019
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89debcfdeec2c9d363c6935bd2cfdd1ebf403f76
ms.sourcegitcommit: d55438841123aad56a524a65332a86ad67af386b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73599299"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Primer vistazo al depurador de Visual Studio

En este tema se presentan las herramientas de depuración que proporciona Visual Studio. En el contexto de Visual Studio, *depurar la aplicación* normalmente significa ejecutar la aplicación con el depurador asociado (es decir, en modo depurador). Al hacerlo, el depurador ofrece muchas formas de ver lo que hace el código durante la ejecución. Esto permite revisar el código y fijarse en los valores almacenados en las variables, establecer inspecciones en ellas para ver cuándo cambian esos valores, examinar la ruta de ejecución del código, etc. Si esta es la primera vez que intenta depurar código, es posible que quiera leer [Depuración para principiantes sin experiencia](../debugger/debugging-absolute-beginners.md) antes de continuar con este tema.

Las características que se explican aquí son aplicables a C#, C++, Visual Basic, JavaScript y otros lenguajes compatibles con Visual Studio (a menos que se indique lo contrario).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Establecer un punto de interrupción e iniciar el depurador

Para depurar, tiene que iniciar la aplicación con el depurador asociado al proceso de la aplicación. **F5** (**Depurar > Iniciar depuración**) es la forma más habitual de hacerlo. Pero de momento es posible que no haya establecido ningún punto de interrupción para examinar el código de la aplicación, por lo que eso es lo que se va a hacer primero y luego se va a iniciar la depuración. Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código.

Si tiene un archivo abierto en el editor de código, puede establecer un punto de interrupción si hace clic en el margen situado a la izquierda de una línea de código.

![Establecimiento de un punto de interrupción](../debugger/media/dbg-tour-set-a-breakpoint.gif "Establecer un punto de interrupción")

Presione **F5** (**Depurar > Iniciar depuración**) o el botón **Iniciar depuración** ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración") en la barra de herramientas de depuración para que el depurador se ejecute hasta el primer punto de interrupción que encuentre. Si la aplicación todavía no se está ejecutando, F5 inicia el depurador y lo detiene en el primer punto de interrupción.

Los puntos de interrupción son una característica de utilidad cuando se conoce la línea o la sección de código que se quiere examinar en detalle.

## <a name="navigate"></a> Exploración del código en el depurador mediante comandos de varios pasos

Se proporcionan métodos abreviados de teclado para la mayoría de los comandos porque hacen que la exploración del código de las aplicaciones sea más rápida. (Los comandos equivalentes, como los comandos de menú, se muestran entre paréntesis).

Para iniciar la aplicación con el depurador asociado, presione **F11** (**Depurar > Depurar paso a paso por instrucciones**). F11 es el comando **Depurar paso a paso por instrucciones** y permite avanzar la ejecución de la aplicación de instrucción en instrucción. Cuando se inicia la aplicación con F11, el depurador se interrumpe en la primera instrucción que se ejecuta.

![Paso a paso por instrucciones F11](../debugger/media/dbg-tour-f11.png "Paso a paso por instrucciones F11")

La flecha amarilla representa la instrucción en la que el depurador se ha detenido, lo cual también suspende la ejecución de la aplicación en el mismo punto (esta instrucción todavía no se ha ejecutado).

F11 es una buena forma de examinar el flujo de ejecución con más detalle. (Además se muestran otras opciones para moverse más rápido por el código). De forma predeterminada, el depurador omite el código que no es de usuario (si quiere más detalles, vea [Solo mi código](../debugger/just-my-code.md)).

>[!NOTE]
> En código administrado, aparece un cuadro de diálogo que le pregunta si quiere recibir una notificación cuando salte automáticamente propiedades y operadores (comportamiento predeterminado). Si quiere cambiar el valor más adelante, deshabilite **Step over properties and operators** (Saltar propiedades y operadores) en el menú **Herramientas > Opciones**, en **Depuración**.

## <a name="step-over-code-to-skip-functions"></a>Saltar código para omitir funciones

Cuando se encuentre en una línea de código que sea una llamada de función o método, puede presionar **F10** (**Depurar > Saltar**) en lugar de F11.

F10 hace avanzar el depurador sin depurar las funciones ni los métodos del código de la aplicación paso a paso por instrucciones (el código se sigue ejecutando). Al presionar F10, puede saltar el código que no le interese. De este modo, puede llegar rápidamente al código que más le interesa.

## <a name="step-into-a-property"></a>Depurar paso a paso por instrucciones una propiedad

Como se ha mencionado anteriormente, el depurador omite de forma predeterminada las propiedades y los campos administrados, pero el comando **Ir a específico** permite invalidar este comportamiento.

Haga clic con el botón derecho en un campo o propiedad y elija **Ir a específico**. Luego elija una de las opciones disponibles.

![Ir a específico](../debugger/media/dbg-tour-step-into-specific.png "Ir a específico")

En este ejemplo, **Ir a específico** lleva al código de `Path.set`.

![Ir a específico](../debugger/media/dbg-tour-step-into-specific-2.png "Ir a específico")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Ejecutar hasta un punto del código rápidamente con el mouse

En el depurador, mantenga el puntero sobre una línea de código hasta que el botón **Run to Click** (Ejecutar hasta clic) (ejecutar hasta aquí) ![Ejecutar hasta clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparezca a la izquierda.

![Ejecutar hasta clic](../debugger/media/dbg-tour-run-to-click-2.png "Icono para ejecutar hasta la línea")

> [!NOTE]
> El botón **Ejecutar hasta clic** (Ejecutar hasta aquí) está disponible a partir de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Haga clic en el botón **Ejecutar hasta clic** (ejecutar hasta aquí). El depurador avanza hasta la línea de código donde se ha hecho clic.

Usar este botón es similar a establecer un punto de interrupción temporal. Este comando también es útil para desplazarse rápidamente dentro de una región visible del código de la aplicación. Puede usar **Ejecutar hasta clic** en cualquier archivo abierto.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Avanzar el depurador fuera de la función actual

A veces, es posible que quiera continuar la sesión de depuración pero avanzar el depurador hasta el final de la función actual.

Presione **Mayús + F11** (o **Depurar > Paso a paso para salir**).

Este comando reanuda la ejecución de la aplicación (y hace avanzar el depurador) hasta que se devuelve la función actual.

## <a name="run-to-cursor"></a>Ejecutar hasta el cursor

Para detener el depurador, presione el botón rojo **Detener depuración** ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Habilitar herramientas de diagnóstico durante la depuración") o **Mayús** + **F5**.

Haga clic con el botón derecho en una línea de código de la aplicación y elija **Ejecutar hasta el cursor**. Este comando inicia la depuración y establece un punto de interrupción temporal en la línea de código actual.

![Ejecutar hasta el cursor](../debugger/media/dbg-tour-run-to-cursor.png "Ejecutar hasta el cursor")

Si ha establecido puntos de interrupción, el depurador se detiene en el primero que alcanza.

Presione **F5** hasta llegar a la línea de código donde ha seleccionado **Ejecutar hasta el cursor**.

Este comando resulta útil cuando se edita código y se quiere establecer rápidamente un punto de interrupción temporal e iniciar el depurador al mismo tiempo.

> [!NOTE]
> Puede usar **Ejecutar hasta el cursor** en la ventana **Pila de llamadas** mientras está depurando.

## <a name="restart-your-app-quickly"></a>Reiniciar la aplicación rápidamente

Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "Reiniciar aplicación") de la barra de herramientas de depuración (**Ctrl + Mayús +F5**).

El botón **Reiniciar** permite ahorrar tiempo, ya que hace que no sea necesario detener la aplicación y reiniciar el depurador. El depurador se detiene en el primer punto de interrupción que se alcanza al ejecutar el código.

Si quiere detener el depurador y volver al editor de código, puede presionar el botón rojo ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Habilitar herramientas de diagnóstico durante la depuración") en lugar de **Reiniciar**.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Edición del código y continuación de la depuración (C#, VB, C++, XAML)

En la mayoría de los lenguajes compatibles con Visual Studio, puede editar el código en medio de una sesión de depuración y continuar con la depuración. Para usar esta característica, haga clic en el código con el cursor mientras está en pausa en el depurador, realice las ediciones y presione **F5**, **F10** o **F11** para continuar con la depuración.

![Edición de código y depuración continua](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Para obtener más información sobre el uso de la característica y las limitaciones de esta, consulte [Editar y continuar](../debugger/edit-and-continue.md).

Para modificar el código XAML durante una sesión de depuración, consulte [Escribir y depurar código XAML en ejecución con la recarga frecuente de XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="inspect-variables-with-data-tips"></a>Inspeccionar variables con información sobre datos

Ahora que sabe manejarse un poco, tiene una buena oportunidad de empezar a inspeccionar el estado de la aplicación (variables) con el depurador. Las características que permiten inspeccionar variables son algunas de las más útiles del depurador, y hay diferentes formas de hacerlo. Con frecuencia, cuando intenta depurar un problema, está intentando averiguar si las variables están almacenando los valores que espera que tengan en un estado determinado de la aplicación.

Con el depurador detenido, mantenga el puntero sobre un objeto y vea su valor de propiedad predeterminado (en este ejemplo, el nombre de archivo `market 031.jpg` es el valor de propiedad predeterminado).

![Visualización de una sugerencia de datos](../debugger/media/dbg-tour-data-tips.gif "Visualización de una sugerencia de datos")

Expanda el objeto para ver todas sus propiedades (como la propiedad `FullPath` en este ejemplo).

A menudo, al depurar, necesita poder comprobar rápidamente los valores de propiedad de los objetos, y la información sobre datos es una buena forma de hacerlo.

> [!TIP]
> En la mayoría de los lenguajes compatibles, es posible editar código en mitad de una sesión de depuración. Para obtener más información, vea [Editar código y seguir depurando](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspeccionar variables con las ventanas Automático y Variables locales

Mientras depura, mire la ventana **Automático** de la parte inferior del editor de código.

![Ventana Automático](../debugger/media/dbg-tour-autos-window.png "Ventana Automático")

En la ventana **Automático** se ven las variables y su tipo y su valor actual. En la ventana **Automático** se muestran todas las variables que se usan en la línea actual o la anterior (en C++, la ventana muestra las variables de las tres líneas de código anteriores. Vea la documentación para obtener información sobre el comportamiento específico del lenguaje).

> [!NOTE]
> En JavaScript, se admite la ventana **Variables locales**, pero no la ventana **Automático**.

A continuación, mire la ventana **Variables locales**. En la ventana **Variables locales** se muestran las variables del ámbito actual.

![Ventana Locales](../debugger/media/dbg-tour-locals-window.png "Ventana Locales")

En este ejemplo, el objeto `this` y el objeto `f` están en el ámbito. Para obtener más información, vea [Inspeccionar las variables en las ventanas automático y variables locales](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Establecer una inspección

Puede usar una ventana **Inspección** para especificar una variable (o una expresión) que quiera supervisar.

Mientras depura, haga clic con el botón derecho en un objeto y elija **Agregar inspección**.

![Ventana Inspección](../debugger/media/dbg-tour-watch-window.png "Ventana Inspección")

En este ejemplo, hay una inspección establecida en el objeto `f` y puede ver cómo cambia su valor conforme avanza el depurador. A diferencia de las otras ventanas de variables, en la ventana **Inspección** siempre se muestran las variables que se están viendo (y se atenúan cuando están fuera del ámbito).

Para obtener más información, vea [Variables de inspección con ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Examinar la pila de llamadas

Mientras depura, haga clic en la ventana **Pila de llamadas**, que está abierta de forma predeterminada en el panel inferior derecho.

![Examinar la pila de llamadas](../debugger/media/dbg-tour-call-stack.png "Examinar la pila de llamadas")

En la ventana **Pila de llamadas** se muestra el orden en el que se llama a los métodos y las funciones. En la línea superior se muestra la función actual (el método `Update` en este ejemplo). En la segunda línea se muestra que se ha llamado a `Update` desde la propiedad `Path.set`, etc. La pila de llamadas es una buena forma de examinar y entender el flujo de ejecución de una aplicación.

> [!NOTE]
> La ventana **Pila de llamadas** es similar a la perspectiva de depuración de algunos IDE, como Eclipse.

Puede hacer doble clic en una línea de código para ver ese código fuente. De este modo, también puede cambiar el ámbito que el depurador va a inspeccionar. Eso no hace avanzar el depurador.

También puede usar los menús contextuales de la ventana **Pila de llamadas** para hacer otras cosas. Por ejemplo, puede insertar puntos de interrupción en funciones concretas, reiniciar la aplicación mediante **Ejecutar hasta el cursor** y examinar el código fuente. Vea [Cómo: Examinar la pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="exception"></a> Examinar una excepción

Cuando la aplicación produce una excepción, el depurador le lleva a la línea de código que ha producido esa excepción.

![Asistente de excepciones](../debugger/media/dbg-tour-exception-helper.png "Asistente de excepciones")

En este ejemplo, el **Asistente de excepciones** muestra una excepción `System.Argument` y un mensaje de error que indica que la ruta de acceso no tiene un formato válido. Por lo tanto, se sabe que el error se ha producido en un argumento de método o función.

En este ejemplo, la llamada a `DirectoryInfo` ha producido el error en la cadena vacía almacenada en la variable `value`.

El Asistente de excepciones es una característica excelente que puede ayudar a depurar errores. También se pueden hacer cosas como ver detalles de errores y agregar una inspección desde el Asistente de excepciones. O bien, si fuera necesario, se pueden cambiar las condiciones para producir la excepción concreta. Para más información sobre cómo controlar las excepciones en el código, vea [Técnicas y herramientas de depuración](../debugger/write-better-code-with-visual-studio.md).

> [!NOTE]
> El Asistente de excepciones ha reemplazado al Asistente de excepciones a partir de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Expanda el nodo **Configuración de excepciones** para ver más opciones para controlar este tipo de excepción sin necesidad de cambiar nada de este paseo.

## <a name="configure-debugging"></a>Configuración de depuración

Puede configurar el proyecto para que se compile como una [configuración de depuración o versión](../debugger/how-to-set-debug-and-release-configurations.md), establecer las propiedades del proyecto para la depuración o establecer la [configuración general](../debugger/how-to-specify-debugger-settings.md) para la depuración. Además, puede configurar el depurador para mostrar información personalizada mediante características como el atributo [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) o, para C/C++, el [marco NatVis](create-custom-views-of-native-objects.md).

Las propiedades de depuración son específicas de cada tipo de proyecto. Por ejemplo, puede especificar un argumento que se pasa a la aplicación cuando se inicia. Para acceder a las propiedades específicas del proyecto, haga clic con el botón derecho en el proyecto en el Explorador de soluciones y seleccione **Propiedades**. Las propiedades de depuración suelen aparecer en la pestaña **Compilar** o **Depurar**, en función del tipo de proyecto específico.

![Propiedades del proyecto](../debugger/media/dbg-tour-project-properties.png "Propiedades del proyecto")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Depurar aplicaciones ASP.NET activas en Azure App Service

**Snapshot Debugger** toma una instantánea de las aplicaciones en producción cuando se ejecuta el código que le interesa. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

![Iniciar Snapshot Debugger](../debugger/media/snapshot-launch.png "Iniciar Snapshot Debugger")

La recopilación de instantáneas está disponible para las aplicaciones ASP.NET que se ejecutan en Azure App Service. Las aplicaciones ASP.NET deben ejecutarse en .NET Framework 4.6.1 o versiones posteriores y las aplicaciones ASP.NET Core en .NET Core 2.0 o versiones posteriores en Windows.

Para obtener más información, vea [Depurar aplicaciones de ASP.NET Azure activas con el depurador de instantáneas](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Ver las instantáneas con step-back de IntelliTrace (Visual Studio Enterprise)

**La característica step-back de IntelliTrace** toma automáticamente una instantánea de la aplicación en cada punto de interrupción y evento de paso del depurador. Las instantáneas registradas le permiten volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior. La característica step-back de IntelliTrace puede permitirle ahorrar tiempo cuando desea ver el estado anterior de la aplicación, pero no desea reiniciar la depuración ni volver a crear el estado de aplicación que se desea.

Para poder navegar y ver las instantáneas, use los botones **Retroceder paso a paso** y **Avanzar paso a paso** en la barra de herramientas de depuración. Estos botones permiten navegar por los eventos que aparecen en la pestaña **Eventos** en la ventana **Herramientas de diagnóstico**.

![Botones Retroceder paso a paso y Avanzar paso a paso](../debugger/media/intellitrace-step-back-icons-description.png  "Botones Retroceder paso a paso y Avanzar paso a paso")

Para obtener más información, vea la página [Inspeccionar el estado de aplicación anterior mediante step-back de IntelliTrace en Visual Studio](../debugger/view-historical-application-state.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha echado un vistazo rápido a muchas características del depurador. Es posible que quiera ahondar en alguna de estas características, como los puntos de interrupción.

> [!div class="nextstepaction"]
> [Aprender a usar puntos de interrupción](../debugger/using-breakpoints.md)
