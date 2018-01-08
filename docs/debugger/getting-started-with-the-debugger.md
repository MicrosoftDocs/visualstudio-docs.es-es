---
title: "Proporciona información sobre cómo depurar con Visual Studio | Documentos de Microsoft"
ms.custom: H1HackMay2017
ms.date: 10/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords: debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a09e0c54f1d7f0e49f08ddf65afbeb030a7087f1
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="learn-to-debug-using-visual-studio"></a>Proporciona información sobre cómo depurar con Visual Studio

En este tema se presenta las características del depurador de Visual Studio en un tutorial paso a paso. Si desea que una vista de nivel superior de las características del depurador, vea [depurador paseo](../debugger/debugger-feature-tour.md).

O bien, puede leer a lo largo de para ver las características del depurador o puede descargar el ejemplo completo que se utiliza en el paseo y siga los pasos que usted mismo. Para descargar el ejemplo y seguir el tutorial, vaya a [fotográfica Visor demostración](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo")  |    [Vea un vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sobre la depuración que muestra los pasos similares. |

Aunque la aplicación de demostración es C#, las características son aplicables a C++, Visual Basic, JavaScript y otros lenguajes compatibles con Visual Studio (excepto donde se indicó).

## <a name="start-the-debugger"></a>Iniciar al depurador.

1. Para seguir a lo largo de estos pasos en Visual Studio, descargue el ejemplo [en esta página](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > Debe instalar Visual Studio con la carga de trabajo de desarrollo de escritorio de .NET para ejecutar la aplicación que estamos usando en la demostración.

2. Descomprima el proyecto.

3. Abra Visual Studio y seleccione la **archivo > Abrir** menú de comandos, y luego elija **proyecto/solución**y, a continuación, abra la carpeta donde descargó el proyecto.

     ![Abra el proyecto de ejemplo](../debugger/media/dbg-tour-open-project.png "Abrir proyecto")

3. Abra la demostración de Visor de fotos de WPF > carpeta de C#, elija el archivo photoapp.sln y seleccione **abiertos**.

     Abre el proyecto en Visual Studio. El Explorador de soluciones en el panel derecho muestra todos los archivos de proyecto.

    ![Archivos del explorador de soluciones](../debugger/media/dbg-tour-solution-explorer.png "el Explorador de soluciones")

4. Presione F5 (**Depurar > Iniciar depuración** o **Iniciar depuración** botón ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración") en la barra de herramientas de depuración).

     ![Aplicación de Visor de fotografía](../debugger/media/dbg-tour-wpf-app.png "aplicación de Visor de fotografías")

     F5, se inicia la aplicación con el depurador asociado al proceso de la aplicación, pero derecha ahora se no hemos agregado ningún punto de interrupción o se llevan a cabo ninguna acción especial para examinar el código. Por lo que simplemente cargue la aplicación y ver las imágenes fotográficas.

     En este paseo se Eche un vistazo más de cerca a esta aplicación con el depurador y obtener características de un vistazo el depurador.

5. Detenga el depurador presionando la detención en rojo ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Detener depuración") botón.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Establecer un punto de interrupción e iniciar el depurador

Para depurar, debe iniciar la aplicación con el depurador asociado al proceso de aplicación.

1. En el `MainWindow` constructor de MainWindow.xaml.cs, establezca un punto de interrupción, haga clic en el margen izquierdo de la primera línea de código.

     ![Establecer un punto de interrupción](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

6. Presione F5 o **Iniciar depuración** botón, la aplicación se inicia, y el depurador ejecuta hasta la línea de código en la que estableció el punto de interrupción.

    La flecha amarilla representa la instrucción en el que el depurador está en pausa, que también suspende la ejecución de la aplicación en el mismo punto (esta instrucción no se ha ejecutado).

    F5 continúa ejecutando la aplicación hasta el punto de interrupción siguiente. (Si la aplicación no se está ejecutando, F5 inicia al depurador y se detiene en el primer punto de interrupción.)

    Los puntos de interrupción son una característica útil si conoce la línea de código o la sección de código que se va a examinar en detalle.

## <a name="restart-your-app-quickly"></a>Reinicie la aplicación rápidamente

1. Haga clic en el **reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") botón en la barra de herramientas Depurar (Ctrl + Mayús + F5).

    Cuando se presiona **reiniciar**, le permite ahorrar tiempo frente a la aplicación de detener y reiniciar el depurador. El depurador se detiene en el primer punto de interrupción se visita mediante la ejecución de código.

    El depurador se detiene de nuevo en el punto de interrupción que estableció en el `MainWindow` constructor.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegar por el código en el depurador mediante comandos de paso

En su mayoría, usamos los métodos abreviados de teclado en este caso, porque es una buena forma de obtener rápida al ejecutar la aplicación en el depurador (comandos equivalentes como menú comandos se muestran entre paréntesis).

1. Presione F11 (**Depurar > Depurar paso a paso**) dos veces para avanzar la ejecución de la aplicación a la `InitializeComponent()` (función).

     ![Presione F11 para depurar paso a paso código](../debugger/media/dbg-tour-f11.png "paso a paso F11")

     F11 es el **paso a paso** comando y hace avanzar la una instrucción ejecución de aplicación a la vez. F11 es una buena manera de examinar el flujo de ejecución en el nivel más detallado. (Para mover contenidos más rápido a través del código, le mostramos algunas otras opciones también.) De forma predeterminada, el depurador omite los código de no usuario (si desea obtener más información, consulte [solo mi código](../debugger/just-my-code.md)).

     >[!NOTE]
     > En código administrado, verá un cuadro de diálogo que le pregunta si desea recibir una notificación cuando automáticamente saltar propiedades y operadores (comportamiento predeterminado). Si desea cambiar la configuración más adelante, deshabilitar **saltar propiedades y operadores** en el **Herramientas > opciones** menú situado bajo **depuración**.

2. Presione F10 (**Depurar > paso a paso por**) varias veces hasta que el depurador se detiene en la primera línea de código en el `OnApplicationStartup` controlador de eventos.

     ![Use F10 para código paso a paso por](../debugger/media/dbg-tour-f10-step-over.png "F10 a paso por procedimientos")

     F10 hace avanzar al depurador sin entrar en funciones o métodos en el código de la aplicación (todavía se ejecuta el código). Presione F10 la `InitializeComponent` llamada al método (en lugar de F11) se recién saltado por el código de implementación para `InitializeComponent` (es decir, que quizá se no estamos está interesados en este momento).

## <a name="step-into-a-property"></a>Ir a una propiedad

1. Con el depurador pausó en esta línea de código:

    ````
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Haga doble clic en la línea de código y elija **ir a específico**, a continuación, **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Use el paso en la característica concreta](../debugger/media/dbg-tour-step-into-specific.png "ir a específico")

    Como se mencionó anteriormente, de forma predeterminada, el depurador omite las propiedades administradas y los campos, pero la **ir a específico** comando le permite invalidar este comportamiento. Por ahora, queremos ver lo que sucede cuando el `Path.set` ejecuciones de establecedor de propiedad. **Ir a específico** obtiene nos la `Path.set` código aquí.

     ![resultado de paso a paso específico](../debugger/media/dbg-tour-step-into-specific-2.png "ir a específico")

     El `Update` método en este código parece que podría ser interesante, por lo que permite utiliza el depurador para examinar ese código cerca.

5. Mantenga el mouse sobre la `Update` método hasta que el verde **ejecutar, haga clic en** botón ![ejecutar, haga clic en](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece a la izquierda.

     ![Usar la ejecución, haga clic en características](../debugger/media/dbg-tour-run-to-click-2.png "ejecutar, haga clic en")

    >  [!NOTE] 
    > El **ejecutar, haga clic en** botón es nuevo en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Si no ve el botón de flecha verde, utilice F11 en este ejemplo en su lugar para hacer avanzar al depurador.

6. Haga clic en el **ejecutar, haga clic en** botón ![ejecutar, haga clic en](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Mediante este botón es similar a establecer un punto de interrupción temporal. **Ejecutar, haga clic en** es útil para desplazarse rápidamente dentro de un área visible del código de la aplicación (puede hacer clic en cualquier archivo abierto).

    El depurador avanza hasta el `Update` implementación del método.

7. Presione F11 para ir a la `Update` método.

     ![Resultado de ejecución paso a paso en el método Update](../debugger/media/dbg-tour-update-method.png "Step en Update (método)")

    En este caso, encontramos más código que parezca interesante; la aplicación obtiene todos los archivos *.jpg que residen en un directorio concreto y, a continuación, crear un objeto de la fotografía para cada archivo. Este código nos da una buena oportunidad para iniciar inspeccionar el estado de la aplicación (variables) con el depurador. Se hará en las secciones siguientes de este tutorial.

    Características que permiten inspeccionar las variables son una de las características más útiles del depurador, y hay diferentes maneras de hacerlo. A menudo, cuando se intenta depurar un problema, está intentando averigüe si las variables almacena los valores que se esperan que tengan en un momento determinado.

## <a name="examine-the-call-stack"></a>Examinar la pila de llamadas

- Mientras está en pausa en la `Update` método, haga clic en el **pila de llamadas** ventana, que está abierto en el panel inferior derecho de forma predeterminada.

     ![Examinar la pila de llamadas](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

    El **pila de llamadas** ventana muestra el orden en el que se esté llamando métodos y funciones. La primera línea muestra la función actual (la `Update` método en la aplicación de paseo). La segunda línea muestra que `Update` se ha llamado desde el `Path.set` propiedad y así sucesivamente.

    >  [!NOTE]
    > El **pila de llamadas** ventana es similar a la perspectiva de la depuración de algunos IDE como Eclipse.

    La pila de llamadas es una buena forma de examinar y comprender el flujo de ejecución de una aplicación.

    Haga doble clic en una línea de código que se vaya a ver ese código de origen y que también cambia el ámbito actual va a inspeccionar el depurador. Esta acción no hace avanzar al depurador.

    También puede utilizar los menús contextuales de la **pila de llamadas** ventana para realizar otras actividades. Por ejemplo, puede insertar los puntos de interrupción en funciones especificadas, avanzar el depurador mediante **ejecutar hasta el Cursor**y vaya a examinar el código fuente. Para obtener más información, consulte [Cómo: examinar la pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Salir

Supongamos que haya terminado examinando el `Update` método de Data.cs y desea sacar partido de la función, pero permanezca en el depurador. Puede hacerlo mediante el **paso a paso fuera** comando.

1. Presione MAYÚS + F11 (o **Depurar > Salir**).

     Este comando reanuda la ejecución de la aplicación (y hace avanzar el depurador) hasta que regresa la función actual.

     Debe tener en el `Update` llamada de método en Data.cs.

2. Presione MAYÚS + F11 nuevo y el depurador va hacia arriba en la pila de llamadas de nuevo a la `OnApplicationStartup` controlador de eventos.

## <a name="run-to-cursor"></a>Ejecutar hasta el cursor

1. Elija la **Detener depuración** botón rojo ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Detener depuración") o MAYÚS + F5.

2. En el `Update` método en Data.cs, haga clic en el `Add` llamadas de método y elija **ejecutar hasta el Cursor**. Este comando inicia la depuración y establece un punto de interrupción temporal en la línea de código actual.

     ![Usar la ejecución en función de Cursor](../debugger/media/dbg-tour-run-to-cursor.png "ejecutar hasta el Cursor")

    Se debe poner en pausa en el punto de interrupción en `MainWindow` (ya que es el primer punto de interrupción establecido).

3. Presione F5 para avanzar a la `Add` método si seleccionas **ejecutar hasta el Cursor**.

    Este comando es útil cuando se edita código y desea establecer un punto de interrupción temporal rápidamente e iniciar al depurador.

## <a name="change-the-execution-flow"></a>Cambiar el flujo de ejecución

1. Con el depurador pausó en la `Add` llamada al método, use el mouse para arrastrar la flecha amarilla (el puntero de ejecución) a la izquierda y mover la flecha amarilla hacia arriba una línea a la `foreach` bucle.

     ![Mueva el puntero de ejecución](../debugger/media/dbg-tour-move-the-execution-pointer.gif "mover el puntero de ejecución")

    Al cambiar el flujo de ejecución, puede hacer cosas como probar las rutas de acceso de ejecución de código diferente o vuelva a ejecutar el código sin necesidad de reiniciar al depurador.

2. Ahora, presione F5.

    Puede ver las imágenes que se agrega a la ventana de aplicación. Dado que se vuelva a ejecutar código en el `foreach` bucle, algunas de las imágenes se han agregado dos veces.
    
    > [!WARNING]
    > A menudo necesita tener cuidado con esta característica, y verá una advertencia en la información sobre herramientas. Puede ver otras advertencias, demasiado. Mueva el puntero, no puede revertir la aplicación a un estado anterior de la aplicación.

## <a name="inspect-variables-with-data-tips"></a>Inspeccionar las variables con sugerencias de datos

1. Abra Data.cs en la aplicación de demostración de Visor de fotos, haga clic en el `private void Update` declaración de función y elija **ejecutar hasta el Cursor** (evitar que la aplicación en primer lugar si ya se está ejecutando).

    Esto pausará la aplicación con el depurador adjunto. Esto nos permite examinar su estado.

2. Mantenga el mouse sobre la `Add` método llamar y haga clic en el **ejecutar, haga clic en** botón ![ejecutar, haga clic en](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. Ahora, mantenga el mouse sobre el objeto de archivo (`f`) y ver su valor de propiedad predeterminado, el nombre de archivo `market 031.jpg`.

     ![Ver información sobre datos](../debugger/media/dbg-tour-data-tips.gif "ver una sugerencia de datos")

4. Expanda el objeto para ver todas sus propiedades, como el `FullPath` propiedad.

    A menudo, durante la depuración, desee una forma rápida de comprobar los valores de propiedad en objetos y las sugerencias de datos son una buena manera de hacerlo.

    > [!TIP]
    > En los lenguajes más compatibles, puede editar código en el medio de una sesión de depurador si encuentra algo que desea cambiar. Para obtener más información, consulte [editar y continuar](../debugger/edit-and-continue.md). Para usar esta característica en esta aplicación, sin embargo, podría primero necesitamos actualizar la versión de la aplicación de .NET Framework.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspeccionar las variables con las ventanas automático y variables locales

1. Mire el **automático** ventana en la parte inferior del editor de código.

     ![Inspeccionar las variables en la ventana automático](../debugger/media/dbg-tour-autos-window.png "ventana automático")

    En el **automático** ventana, verá las variables y su valor actual. El **automático** ventana muestra todas las variables utilizadas en la línea actual o en la línea anterior (en C++, la ventana muestra las variables en las tres líneas de código anteriores. Compruebe la documentación para el comportamiento específico del idioma).

    > [!NOTE]
    > En JavaScript, el **locales** ventana es compatible pero no la **automático** ventana.

2. A continuación, examine la **locales** ventana.

    El **locales** ventana muestra las variables que están en el ámbito actual.

    ![Inspeccionar las variables en la ventana variables locales](../debugger/media/dbg-tour-locals-window.png "ventana variables locales")

    Actualmente, el `this` objeto y el objeto de archivo (`f`) están en el ámbito actual. Para obtener más información, consulte [inspeccionar las Variables en las ventanas de variables locales y automático](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Establece una inspección

1. En la ventana del editor de código principal, haga clic en el objeto de archivo (`f`) y elija **Agregar inspección**.

    Puede usar un **inspección** ventana para especificar una variable (o una expresión) que desea que esté atento en.

    Ahora, tiene una inspección activada la `File` objeto y se puede ver su valor cambia conforme se desplaza por el depurador. A diferencia de las otras ventanas de variables, la **inspección** ventana siempre muestra las variables que está viendo (están atenuadas cuando sale del ámbito).

2. En el `Add` método, haga clic en el color verde ![ejecutar, haga clic en](../debugger/media/dbg-tour-run-to-click.png "RunToClick") nuevamente en el botón (o presione F11 varias veces) para avanzar a través de la `foreach` bucle.

    ![Establece una inspección en una variable](../debugger/media/dbg-tour-watch-window.png "ventana Inspección")

    También puede ver la primera imagen se agregan a la ventana principal de la ejecución de aplicación de ejemplo, pero esto se produce en un subproceso de aplicación diferente, por lo que las imágenes que aún no esté visibles.

    Para obtener más información, consulte [establece una inspección mediante la inspección y las ventanas de inspección rápida](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Examinar una excepción

1. En la ventana de aplicación de ejecución, elimine el texto en el **ruta de acceso** cuadro de entrada y seleccione el **cambio** botón.

     ![Hacer que se produzca una excepción](../debugger/media/dbg-tour-cause-an-exception.png "producirá una excepción")

     La aplicación produce una excepción y el depurador le lleva a la línea de código que produjo la excepción.
     
     ![Aplicación auxiliar de excepciones](../debugger/media/dbg-tour-exception-helper.png "aplicación auxiliar de excepciones")

     En este caso, el **aplicación auxiliar de excepciones** muestra un `System.ArgumentException` y un mensaje de error que indica que la ruta de acceso no es un formato válido. Por lo tanto, sabemos que se produjo el error en un argumento de método o función.

     En este ejemplo, el `DirectoryInfo` llamada dio el error en la cadena vacía que se almacenan en la `value` variable. (Mantenga el mouse sobre `value` para ver la cadena vacía.)

     La aplicación auxiliar de excepciones es una característica excelente que puede ayudarle a depurar los errores. También puede hacer cosas como vista de detalles del error y agregue una inspección de la aplicación auxiliar de excepciones. O bien, si es necesario, puede cambiar las condiciones para producir la excepción concreta.

    >  [!NOTE] 
    > Reemplaza el Asistente de excepciones en la aplicación auxiliar de excepciones [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Expanda el **configuración de excepciones** nodo para ver más opciones controlar este tipo de excepción, pero no es necesario cambiar ninguna acción para este paseo le!

3. Presione F5 para continuar con la aplicación.

Para obtener más información sobre las características del depurador, vea [depurador sugerencias y trucos](../debugger/debugger-tips-and-tricks.md).

## <a name="see-also"></a>Vea también

[Depurar en Visual Studio](../debugger/index.md)  
[Guía de características del depurador](../debugger/debugger-feature-tour.md)
