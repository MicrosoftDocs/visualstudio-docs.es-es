---
title: Obtenga información sobre cómo depurar con el depurador de Visual Studio
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1144e7e33709510cb03ed02cb62020f81e8e8b62
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303151"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>Tutorial: Información sobre cómo depurar con Visual Studio

En este tema se presenta las características del depurador de Visual Studio en un tutorial paso a paso. Si desea una vista de nivel superior de las características del depurador, vea [Guía de características del depurador](../debugger/debugger-feature-tour.md). Cuando se *depurar la aplicación*, suele significar que se ejecuta la aplicación con el depurador adjunto. Al hacerlo, el depurador proporciona muchas formas de ver lo que hace el código mientras se ejecuta. Puede ver los valores almacenados en variables y recorrer el código, puede establecer inspecciones de variables para ver cuando cambian los valores, puede examinar la ruta de acceso de ejecución del código, et al. Si se trata de la primera vez que ha probado para depurar el código, es posible que desea leer [de depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) antes de pasar a través de este tema.

O bien, puede leer a lo largo de para ver las características del depurador o puede descargar el ejemplo completo que se usa en la Guía de características y siga los pasos usted mismo. Para descargar el ejemplo y seguir el tutorial, vaya a [demostración del Visor de fotos](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo")  |    [Vea un vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sobre la depuración que muestran los mismos pasos. |

Aunque la aplicación de demostración es C#, las características son aplicables a C++, Visual Basic, JavaScript y otros lenguajes compatibles con Visual Studio (excepto donde se indique).

En este tutorial va a:

> [!div class="checklist"]
> * Iniciar al depurador y alcanzar puntos de interrupción.
> * Obtenga información sobre los comandos para recorrer el código en el depurador
> * Inspeccionar las variables en las sugerencias de datos y las ventanas del depurador
> * Examinar la pila de llamadas
> * Usar la aplicación auxiliar de excepciones

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio 2017 y el. **El desarrollo de escritorio neto** carga de trabajo.

    Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

    Si necesita instalar la carga de trabajo pero ya tiene Visual Studio, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto** (seleccione **Archivo** > **Nuevo** > **Proyecto**). Se iniciará el Instalador de Visual Studio. Elija el. **El desarrollo de escritorio neto** carga de trabajo, a continuación, elija **modificar**.

## <a name="start-the-debugger"></a>Iniciar al depurador.

1. Para seguir estos pasos en Visual Studio, descargue el ejemplo [en esta página](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > Deberá instalar Visual Studio con la carga de trabajo de desarrollo de escritorio de .NET para ejecutar la aplicación que estamos usando en la demostración.

2. Descomprima el proyecto.

3. Abra Visual Studio y seleccione el **archivo > Abrir** menú de comandos y luego elija **proyecto/solución**y, a continuación, abra la carpeta donde descargó el proyecto.

     ![Abra el proyecto de ejemplo](../debugger/media/dbg-tour-open-project.png "Abrir proyecto")

3. Abra la demostración de Visor de fotos de WPF > carpeta de C#, elija el *photoapp.sln* de archivo y seleccione **abierto**.

     El proyecto se abre en Visual Studio. El Explorador de soluciones en el panel derecho muestra todos los archivos de proyecto.

    ![Los archivos del explorador de soluciones](../debugger/media/dbg-tour-solution-explorer.png "el Explorador de soluciones")

4. Presione **F5** (**Depurar > Iniciar depuración**) o el **Iniciar depuración** botón ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración ") en la barra de herramientas de depuración.

     ![Aplicación de Visor de fotos](../debugger/media/dbg-tour-wpf-app.png "aplicación de Visor de fotos")

     F5 inicia la aplicación con el depurador adjunto para el proceso de la aplicación, sino justo ahora, no hemos agregado ningún punto de interrupción o hecho nada especial para examinar el código. Por lo que solo carga la aplicación y ver las imágenes de fotografías.

     En este paseo, echaremos un vistazo a esta aplicación con el depurador y obtener las características de un vistazo en el depurador.

5. Detenga el depurador presionando el delimitador de color rojo ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Detener depuración") botón.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Establecer un punto de interrupción e iniciar el depurador

Para depurar, deberá iniciar la aplicación con el depurador asociado al proceso de la aplicación.

1. En el `MainWindow` constructor de MainWindow.xaml.cs, establezca un punto de interrupción, haga clic en el margen izquierdo de la primera línea de código.

     ![Establezca un punto de interrupción](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

    Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código. 

6. Presione **F5** o **Iniciar depuración** botón, la aplicación se inicia y se ejecuta el depurador a la línea de código donde estableció el punto de interrupción.

    La flecha amarilla representa la instrucción en el que el depurador está en pausa, que también suspende la ejecución de la aplicación en el mismo punto (esta instrucción no se ha ejecutado).

    F5 sigue ejecutando la aplicación para el punto de interrupción siguiente. (Si aún no se ejecuta la aplicación, F5 inicia al depurador y se detiene en el primer punto de interrupción).

    Puntos de interrupción son una característica muy útil cuando se sabe que la línea de código o en la sección de código que desea examinar con detalle.

## <a name="optional-restart-your-app-quickly"></a>(Opcional) Reinicie la aplicación rápidamente

Haga clic en el **reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") botón en la barra de herramientas Depurar (**Ctrl** + **MAYÚS**   +  **F5**).

Al presionar **reiniciar**, ahorra tiempo en comparación con la aplicación de detener y reiniciar el depurador. El depurador se detiene en el primer punto de interrupción que se obtiene acceso mediante la ejecución de código.

El depurador se detiene de nuevo en el punto de interrupción establecido, en el `MainWindow` constructor.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegar por el código en el depurador mediante comandos de paso

Principalmente, usamos los métodos abreviados de teclado en este caso, porque es una buena forma de obtener rápida al ejecutar la aplicación en el depurador (comandos equivalentes como menú de comandos se muestran entre paréntesis).

1. Presione **F11** (**Depurar > paso a paso**) dos veces para avanzar la ejecución de la aplicación a la `InitializeComponent()` función.

     ![Use F11 para depurar paso a paso el código](../debugger/media/dbg-tour-f11.png "paso a paso F11")

     F11 es el **paso a paso** comando y hace avanzar la una instrucción ejecución de aplicación a la vez. F11 es una buena manera para examinar el flujo de ejecución en el nivel más detallado. (Para mover más rápido a través del código, le mostraremos algunas otras opciones también.) De forma predeterminada, el depurador omite el código de no usuario (si desea obtener más información, consulte [solo mi código](../debugger/just-my-code.md)).

     >[!NOTE]
     > En código administrado, verá un cuadro de diálogo que le pregunta si desea recibir una notificación cuando automáticamente saltar propiedades y operadores (comportamiento predeterminado). Si desea cambiar la configuración más adelante, deshabilitar **saltar propiedades y operadores** en el **Herramientas > opciones** menú bajo **depuración**.

2. Presione **F10** (**Depurar > saltar**) varias veces hasta que el depurador se detiene en la primera línea de código en el `OnApplicationStartup` controlador de eventos.

     ![Use F10 para el código paso a paso por](../debugger/media/dbg-tour-f10-step-over.png "saltar F10")

     F10 hace avanzar al depurador sin entrar en las funciones o métodos en el código de aplicación (todavía se ejecuta el código). Al presionar F10 en el `InitializeComponent` llamada al método (en lugar de F11), se omite el código de implementación de `InitializeComponent` (que probablemente nos no estamos interesados en este momento).

## <a name="step-into-a-property"></a>Ir a una propiedad

1. Con el depurador pausó en esta línea de código:

    ````c#
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Haga doble clic en la línea de código y elija **ir a específico**, a continuación, **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Use el paso en la característica específica](../debugger/media/dbg-tour-step-into-specific.png "ir a específico")

    Como se mencionó anteriormente, de forma predeterminada, el depurador omite las propiedades administradas y campos, pero la **ir a específico** comando le permite invalidar este comportamiento. Por ahora, nos interesa ver lo que sucede cuando el `Path.set` ejecuciones de establecedor de propiedad. **Ir a específico** nos Obtiene el `Path.set` código aquí.

     ![resultado de ir a específico](../debugger/media/dbg-tour-step-into-specific-2.png "ir a específico")

     El `Update` método en este código parece que podría ser interesante, por lo que permite utiliza el depurador para examinar ese código de cerca.

5. Mantenga el mouse sobre el `Update` método hasta que el verde **hacer clic y ejecutar** botón ![hacer clic y ejecutar](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece a la izquierda.

     ![Use la ejecución, haga clic en características](../debugger/media/dbg-tour-run-to-click-2.png "hacer clic y ejecutar")

    >  [!NOTE]
    > El **hacer clic y ejecutar** es nuevo en el botón [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Si no ve el botón de flecha verde, utilice F11 en este ejemplo en su lugar para avanzar al depurador.

6. Haga clic en el **hacer clic y ejecutar** botón ![hacer clic y ejecutar](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Mediante este botón es similar a la configuración de un punto de interrupción temporal. **Hacer clic y ejecutar** es útil para desplazarse rápidamente dentro de un área visible del código de la aplicación (puede hacer clic en cualquier archivo abierto).

    El depurador avanza a la `Update` implementación del método.

7. Presione **F11** para adentrarse en el `Update` método.

     ![Resultado de la ejecución paso a paso en el método Update](../debugger/media/dbg-tour-update-method.png "paso en el método de actualización")

    En este caso, encontramos algunas más código que parece interesante; la aplicación obtiene todos los. *jpg* archivos que residen en un directorio determinado y, a continuación, crear un objeto de fotografías para cada archivo. Este código nos da una buena oportunidad para empezar a inspeccionar el estado de la aplicación (variables) con el depurador. Haremos en las secciones siguientes de este tutorial.

    Las características que permiten inspeccionar las variables son una de las características más útiles del depurador, y hay diferentes maneras de hacerlo. A menudo, cuando se intenta depurar un problema, está intentando averiguar si las variables almacena los valores que se esperan que tengan en un momento determinado.

## <a name="examine-the-call-stack"></a>Examinar la pila de llamadas

Mientras está en pausa en el `Update` método, haga clic en el **pila de llamadas** ventana, que está abierto en el panel inferior derecho de forma predeterminada.

![Examinar la pila de llamadas](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

El **pila de llamadas** ventana muestra el orden en el que obtener se llaman los métodos y funciones. La línea superior muestra la función actual (la `Update` método en la aplicación de la visita). La segunda línea muestra que `Update` se llamó desde el `Path.set` propiedad y así sucesivamente.

>  [!NOTE]
> El **pila de llamadas** ventana es similar a la perspectiva de depuración de algunos IDE como Eclipse.

La pila de llamadas es una buena manera para examinar y entender el flujo de ejecución de una aplicación.

Haga doble clic en una línea de código para ir a mirar ese código fuente y que también cambia el ámbito actual va a inspeccionar el depurador. Esta acción no hace avanzar al depurador.

También puede usar los menús contextuales de la **pila de llamadas** ventana hacer otras cosas. Por ejemplo, puede insertar puntos de interrupción en funciones especificadas, avanzar el depurador mediante **ejecutar hasta el Cursor**y vaya a examinar el código fuente. Para obtener más información, consulte [Cómo: examinar la pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Salir

Supongamos que se realiza examinando la `Update` método en Data.cs y desea sacar partido de la función, pero permanecen en el depurador. Puede hacerlo mediante el **paso a paso fuera** comando.

1. Presione **MAYÚS** + **F11** (o **Depurar > Salir**).

     Este comando reanuda la ejecución de la aplicación (y hace avanzar el depurador) hasta que devuelve la función actual.

     Debería estar en el `Update` llamada al método en Data.cs.

2. Presione **MAYÚS** + **F11** nuevo, y el depurador entra la pila de llamadas a la `OnApplicationStartup` controlador de eventos.

## <a name="run-to-cursor"></a>Ejecutar hasta el cursor

1. Elija la **Detener depuración** botón rojo ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Detener depuración") o **MAYÚS** + **F5** .

2. En el `Update` método *Data.cs*, haga clic en el `Add` método llamar y elija **ejecutar hasta el Cursor**. Este comando inicia la depuración y establece un punto de interrupción temporal en la línea de código actual.

     ![Usar la ejecución en función de Cursor](../debugger/media/dbg-tour-run-to-cursor.png "ejecutar hasta el Cursor")

    Se debe pausar en el punto de interrupción `MainWindow` (ya que es el primer punto de interrupción establecido).

3. Presione **F5** para avanzar a la `Add` método activaste **ejecutar hasta el Cursor**.

    Este comando resulta útil cuando se edita código y desea establecer un punto de interrupción temporal rápidamente e iniciar al depurador.

## <a name="change-the-execution-flow"></a>Cambiar el flujo de ejecución

1. Con el depurador pausó en el `Add` llamada al método, use el mouse para seleccionar la flecha amarilla (el puntero de ejecución) a la izquierda y mover la flecha amarilla hacia arriba una línea a la `foreach` bucle.

     ![Mueva el puntero de ejecución](../debugger/media/dbg-tour-move-the-execution-pointer.gif "mover el puntero de ejecución")

    Al cambiar el flujo de ejecución, puede hacer cosas como comprobar las rutas de ejecución de código diferente o volver a ejecutar código sin necesidad de reiniciar al depurador.

2. Ahora, presione **F5**.

    Puede ver las imágenes que se agrega a la ventana de la aplicación. Dado que se vuelve a ejecutar código en el `foreach` bucle, algunas de las imágenes se han agregado dos veces!

    > [!WARNING]
    > A menudo es necesario tener cuidado con esta característica, y verá una advertencia en la información sobre herramientas. Puede ver otras advertencias, demasiado. Mover el puntero no puede revertir la aplicación a un estado anterior de la aplicación.

## <a name="inspect-variables-with-data-tips"></a>Inspeccionar las variables con sugerencias de datos

1. Abra *Data.cs* en la aplicación de demostración de Visor de fotos, haga clic en el `private void Update` declaración de función y elija **ejecutar hasta el Cursor** (detener la aplicación en primer lugar si ya se está ejecutando).

    Esto pausará la aplicación con el depurador adjunto. Esto nos permite examinar su estado.

2. Mantenga el mouse sobre el `Add` método llamar y haga clic en el **hacer clic y ejecutar** botón ![hacer clic y ejecutar](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. Ahora, mantenga el mouse sobre el objeto de archivo (`f`) y ver su valor de propiedad predeterminado, el nombre de archivo *mercado jpg 031*.

     ![Ver información sobre datos](../debugger/media/dbg-tour-data-tips.gif "ver una sugerencia de datos")

4. Expanda el objeto para ver todas sus propiedades, como el `FullPath` propiedad.

    A menudo, cuando se depura, desea que una forma rápida de comprobar los valores de propiedad en objetos, y las sugerencias de datos son una buena forma de hacerlo.

    > [!TIP]
    > En los lenguajes más compatibles, puede editar el código en el medio de una sesión del depurador si encuentra algo que quiera cambiar. Para obtener más información, consulte [editar y continuar](../debugger/edit-and-continue.md). Para usar esta característica en esta aplicación, sin embargo, sería primero es necesario actualizar la versión de la aplicación de .NET Framework.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspeccionar las variables con las ventanas automático y variables locales

1. Examine el **automático** ventana en la parte inferior del editor de código.

     ![Inspeccionar las variables en la ventana automático](../debugger/media/dbg-tour-autos-window.png "ventana automático")

    En el **automático** ventana, puede ver las variables y su valor actual. El **automático** ventana muestra todas las variables usadas en la línea actual o la línea anterior (en C++, la ventana muestra las variables en las tres líneas de código anteriores. Consulte la documentación para el comportamiento específico del idioma).

    > [!NOTE]
    > En JavaScript, la **variables locales** pero no se admite la ventana de la **automático** ventana.

2. A continuación, examine el **variables locales** ventana.

    El **variables locales** ventana muestra las variables que están en el ámbito actual.

    ![Inspeccionar las variables en la ventana variables locales](../debugger/media/dbg-tour-locals-window.png "ventana variables locales")

    Actualmente, el `this` objeto y el objeto de archivo (`f`) están en el ámbito actual. Para obtener más información, consulte [inspeccionar Variables en las ventanas motor y variables locales Windows](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Establece una inspección

1. En la ventana del editor de código principal, haga clic en el objeto de archivo (`f`) y elija **Agregar inspección**.

    Puede usar un **inspección** ventana para especificar una variable (o una expresión) que desee vigilar en.

    Ahora, tendrá una inspección establecida en el `File` objeto y puede ver su valor cambia conforme se desplaza por el depurador. A diferencia de las otras ventanas de variables, la **inspección** ventana siempre muestra las variables que está viendo (están atenuadas cuando fuera del ámbito).

2. En el `Add` método, haga clic en el verde ![hacer clic y ejecutar](../debugger/media/dbg-tour-run-to-click.png "RunToClick") nuevamente en el botón (o presione F11 varias veces) para avanzar por el `foreach` bucle.

    ![Establece una inspección en una variable](../debugger/media/dbg-tour-watch-window.png "ventana Inspección")

    También puede ver la primera imagen se agregan a la ventana principal de la ejecución de aplicación de ejemplo, pero esto se produce en un subproceso de aplicación diferentes, por lo que las imágenes es posible que aún no esté visibles.

    Para obtener más información, consulte [establece una inspección mediante la inspección e inspección rápida Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Examinar una excepción

1. En la ventana de aplicación de ejecución, elimine el texto en el **ruta** cuadro de entrada y seleccione el **cambio** botón.

     ![Producir una excepción que se produzca](../debugger/media/dbg-tour-cause-an-exception.png "producirá una excepción")

     La aplicación inicia una excepción y el depurador le lleva a la línea de código que produjo la excepción.

     ![Aplicación auxiliar de excepciones](../debugger/media/dbg-tour-exception-helper.png "aplicación auxiliar de excepciones")

     En este caso, el **aplicación auxiliar de excepciones** se muestra un `System.ArgumentException` y un mensaje de error que indica que la ruta de acceso no es un formato válido. Por lo tanto, sabemos que se produjo el error en un argumento de método o función.

     En este ejemplo, el `DirectoryInfo` llamada dio el error en la cadena vacía que se almacenan en el `value` variable. (Mantenga el mouse sobre `value` para ver la cadena vacía.)

     La aplicación auxiliar de excepciones es una característica excelente que puede ayudarle a depurar errores. También puede hacer cosas como vista de detalles del error y agregue una inspección de la aplicación auxiliar de excepciones. O bien, si es necesario, puede cambiar las condiciones para producir la excepción concreta.

    >  [!NOTE]
    > Reemplaza el Asistente de excepciones en la aplicación auxiliar de excepciones [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Expanda el **configuración de excepciones** nodo para ver más opciones sobre cómo controlar este tipo de excepción, pero no es necesario cambiar nada para este paseo!

3. Presione **F5** para continuar la aplicación.

Para obtener más información acerca de las características del depurador, vea [depurador sugerencias y trucos](../debugger/debugger-tips-and-tricks.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo iniciar al depurador, paso a través del código e inspeccionar las variables. Es posible que desee obtener un alto nivel sobre las características del depurador junto con vínculos para obtener más información.

> [!div class="nextstepaction"]
> [Guía de características del depurador](../debugger/debugger-feature-tour.md)
