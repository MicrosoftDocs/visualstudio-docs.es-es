---
title: 'Tutorial: Depurar código de C#'
description: Obtenga información sobre las características del depurador de Visual Studio y sobre cómo iniciarlo, recorrer el código e inspeccionar los datos de una aplicación de C#.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 04/23/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 741c22e8116d47a51a75369b5b114725c1f64bf8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909269"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Tutorial: Información sobre cómo depurar código de C# con Visual Studio

En este artículo se describen las características del depurador de Visual Studio en un tutorial paso a paso. Si quiere ahondar en las características del depurador, vea [Primer vistazo al depurador](../../debugger/debugger-feature-tour.md). Normalmente, *depurar una aplicación* significa ejecutar la aplicación con el depurador activado. Al hacerlo, el depurador ofrece muchas formas de ver lo que hace el código durante la ejecución. Esto permite revisar el código y fijarse en los valores almacenados en variables, establecer inspecciones en ellas para ver cuándo cambian los valores, examinar la ruta de ejecución del código, ver si una rama de código está en funcionamiento, etc. Si esta es la primera vez que intenta depurar código, le recomendamos que lea [Depuración para principiantes sin experiencia](../../debugger/debugging-absolute-beginners.md) antes de continuar con este artículo.

Aunque la aplicación de demostración está en C#, la mayoría de las características son aplicables a C++, Visual Basic, F#, Python, JavaScript y otros lenguajes compatibles con Visual Studio (F# no admite Editar y continuar, mientras que F# y JavaScript no admiten la ventana **Automático**). Las capturas de pantalla son de código C#.

En este tutorial va a:

> [!div class="checklist"]
> * Iniciar el depurador y llegar a puntos de interrupción
> * Conocer los comandos para analizar el código en el depurador
> * Inspeccionar variables en la información sobre datos y las ventanas del depurador
> * Examinar la pila de llamadas

## <a name="prerequisites"></a>Requisitos previos

::: moniker range=">=vs-2019"

Debe tener instalados Visual Studio 2019 y la carga de trabajo **Desarrollo multiplataforma de .NET Core**.

::: moniker-end
::: moniker range="vs-2017"

Debe tener instalados Visual Studio 2017 y la carga de trabajo **Desarrollo multiplataforma de .NET Core**.

::: moniker-end

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

Si tiene que instalar la carga de trabajo pero ya tiene Visual Studio, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el Instalador de Visual Studio. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, **Modificar**.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, creará un proyecto de aplicación de consola de .NET Core. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

::: moniker range="vs-2017"

1. Abra Visual Studio 2017.

2. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el cuadro de diálogo **Nuevo proyecto** del panel de la izquierda, expanda **C#** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)** . Después, asigne el nombre *get-started-debugging* al proyecto.

     Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)** , elija en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**.

     Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

::: moniker-end

::: moniker range="vs-2019"

1. Abra Visual Studio 2019.

   Si la ventana de inicio no está abierta, elija **Archivo** > **Ventana Inicio**.

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

1. En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *consola*. Seguidamente, elija **C#** en la lista de lenguajes y luego, **Windows** en la lista de plataformas. 

   Después de aplicar los filtros de lenguaje y plataforma, elija la plantilla **Aplicación de consola (.NET Core)** y luego, **Siguiente**.

   ![Elección de la plantilla de C# para la aplicación de consola (.NET Core)](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Si no ve la plantilla **Aplicación de consola (.NET Core)** , puede instalarla desde la ventana **Crear un proyecto**. En el mensaje **¿No encuentra lo que busca?** , elija el vínculo **Instalar más herramientas y características**. Luego, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo multiplataforma de .NET Core**.

1. En la ventana **Configurar el nuevo proyecto**, escriba *GetStartedDebugging* en el cuadro **Nombre del proyecto**. Luego, elija **Crear**.

   Visual Studio se abre en el nuevo proyecto.
   
::: moniker-end

## <a name="create-the-application"></a>Crear la aplicación

1. En *Program.cs*, reemplace todo el código predeterminado con el siguiente:

    ```csharp
    using System;
    class ArrayExample
    {
        static void Main()
        {
            char[] letters = { 'f', 'r', 'e', 'd', ' ', 's', 'm', 'i', 't', 'h'};
            string name = "";
            int[] a = new int[10];
            for (int i = 0; i < letters.Length; i++)
            {
                name += letters[i];
                a[i] = i + 1;
                SendMessage(name, a[i]);
            }
            Console.ReadKey();
        }
        static void SendMessage(string name, int msg)
        {
            Console.WriteLine("Hello, " + name + "! Count to " + msg);
        }
    }
    ```

## <a name="start-the-debugger"></a>Inicio del depurador

1. Presione **F5** (**Depurar > Iniciar depuración**) o el botón **Iniciar depuración**![Iniciar depuración](../../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración") en la barra de herramientas de depuración.

     Al pulsar **F5**, la aplicación se inicia con el depurador activado para analizar los procesos. Como de momento no hemos hecho nada especial para examinar el código, la aplicación solo se carga y se muestra la salida de la consola.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     En este tutorial, analizaremos con más profundidad el uso de esta aplicación junto con el depurador y veremos las características del depurador.

2. Para detener el depurador, presione el botón de detención rojo ![Detener depuración](../../debugger/media/dbg-tour-stop-debugging.png "Habilitar herramientas de diagnóstico durante la depuración") (**Mayús** + **F5**).

3. En la ventana de consola, presione una tecla para cerrarla.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Establecer un punto de interrupción e iniciar el depurador

1. En el bucle `for` de la función `Main`, establezca un punto de interrupción haciendo clic en el margen izquierdo de la línea de código siguiente:

    `name += letters[i];`

    Aparece un círculo de color rojo ![Breakpoint](../../debugger/media/dbg-breakpoint.png "Punto de interrupción") donde se establece el punto de interrupción.

    Los puntos de interrupción son una de las características más básicas y esenciales de una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código.

2. Presione **F5** o el botón **Iniciar depuración**![Iniciar depuración](../../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración"). La aplicación se inicia y el depurador se ejecuta en la línea de código en la que haya establecido el punto de interrupción.

    ![Establecimiento y uso de los puntos de interrupción](../csharp/media/get-started-set-breakpoint.gif)

    La flecha amarilla representa la instrucción en la que el depurador se ha puesto en pausa, lo cual también suspende la ejecución de la aplicación en el mismo punto (esta instrucción todavía no se ha ejecutado).

     Si la aplicación todavía no se está ejecutando, **F5** permite iniciar el depurador, que se detendrá en el primer punto de interrupción. En caso contrario, **F5** permite continuar ejecutando la aplicación hasta el siguiente punto de interrupción.

    Los puntos de interrupción son una característica de utilidad cuando se conoce la línea o la sección de código que se quiere examinar en detalle. Para obtener información sobre los diferentes tipos de puntos de interrupción que se pueden establecer, como los puntos de interrupción condicionales, vea [Uso de puntos de interrupción](../../debugger/using-breakpoints.md).

## <a name="navigate-code-and-inspect-data-using-data-tips"></a>Navegación por el código e inspección de datos con sugerencias de datos

Normalmente, aquí usamos métodos abreviados de teclado porque son una buena forma de ejecutar rápidamente la aplicación en el depurador, pero los comandos equivalentes, como los comandos de menú, se muestran entre paréntesis.

1. Mientras está en pausa en la instrucción `name += letters[i]`, mantenga el mouse sobre la variable `letters` y verá su valor predeterminado, el valor del primer elemento de la matriz `char[10]`.

     Las características que le permiten inspeccionar las variables son una de las más útiles del depurador y ofrecen diferentes formas de hacerlo. A menudo, para depurar un problema, debe intentar averiguar si las variables están almacenando los valores que espera que tengan en un momento determinado.

1. Expanda la variable `letters` para ver sus propiedades, que incluyen todos los elementos que contiene.

     ![Captura de pantalla del depurador de Visual Studio con la instrucción "name+= letters[I]" resaltada y una lista desplegable que muestra los elementos de la matriz de letras.](../csharp/media/get-started-view-data-tip.png)

1. Después, mantenga el mouse sobre la variable `name` y verá su valor actual, una cadena vacía.

1. Presione **F10** dos veces, o bien elija **Depurar > Depurar paso a paso por procedimientos**, para avanzar hasta la llamada de método `SendMessage` y, después, vuelva a presionar **F10**.

     F10 hace avanzar el depurador hasta la siguiente instrucción sin depurar las funciones ni los métodos del código de la aplicación paso a paso por instrucciones (el código se sigue ejecutando). Al presionar F10 en la llamada de método `SendMessage`, se omite el código de implementación de `SendMessage` (algo que quizás no nos interese en este momento).

1. Presione **F10** varias veces, o bien elija **Depurar** > **Depurar paso a paso por procedimientos**, para iterar varias veces por el bucle `for`, deténgase de nuevo en el punto de interrupción y mantenga el mouse sobre la variable `name` cada vez para comprobar su valor.

     ![Captura de pantalla animada del depurador de Visual Studio en la que se muestra el efecto de presionar F10 para depurar paso a paso por procedimientos y recorrer en iteración un bucle durante la depuración.](../csharp/media/get-started-data-tip.gif)

     El valor de la variable cambia con cada iteración del bucle `for` y muestra los valores de `f`, después, `fr`, luego, `fre`, etc. Para hacer que el depurador avance por el bucle más rápido en este escenario, puede presionar **F5**, o bien elegir **Depurar** > **Continuar**, en su lugar, lo que le permite avanzar hasta el punto de interrupción en lugar de hasta la siguiente instrucción.

     A menudo, al realizar una depuración, queremos una forma rápida de comprobar los valores de las propiedades de las variables para ver si se almacenan los valores correspondientes, y las sugerencias de datos son una buena forma de verlo.

1. Mientras aún está en pausa en el bucle `for` del método `Main`, presione **F11** hasta que esté en pausa en la llamada de método `SendMessage`, o bien elija **Depurar > Depurar paso a paso por instrucciones**.

     Debe estar en esta línea de código:

     `SendMessage(name, a[i]);`

1. Presione **F11** una vez más para entrar en el método `SendMessage`.

     El puntero de color amarillo avanza hasta el método `SendMessage`.

     ![Uso de F11 para depurar código paso a paso por instrucciones](../csharp/media/get-started-f11.png "Depuración paso a paso por instrucciones con F10")

     F11 es el comando **Depurar paso a paso por instrucciones** y permite avanzar la ejecución de la aplicación de instrucción en instrucción. F11 es una buena forma de examinar el flujo de ejecución con más detalle. De forma predeterminada, el depurador omite el código que no es de usuario (si quiere más detalles, vea [Solo mi código](../../debugger/just-my-code.md)).

     Imagine que ha terminado de examinar el método `SendMessage` y quiere salir de él, pero permanecer en el depurador. Puede hacerlo con el comando **Salir de la depuración**.

1. Presione **Mayús** + **F11** (o **Depurar > Salir de la depuración**).

     Este comando reanuda la ejecución de la aplicación (y hace avanzar el depurador) hasta que se devuelve el método o la función actual.

     Debería volver a estar en el bucle `for` del método `Main`, detenido en la llamada al método `SendMessage`. Para más información sobre las distintas formas de desplazarse por el código, vea [Navegación por el código en el depurador](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Navegación por el código con Ejecutar hasta clic

1. Presione **F5** para volver a avanzar hasta el punto de interrupción.

1. En el editor de código, desplácese hacia abajo y mantenga el puntero sobre el método `Console.WriteLine` del método `SendMessage` hasta que aparezca el botón **Ejecutar hasta clic**![Ejecutar hasta clic](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") de color verde a la izquierda. La información sobre herramientas del botón muestra "Ejecutar hasta aquí".

     ![Uso de la característica Ejecutar hasta clic](../csharp/media/get-started-run-to-click.png "Icono para ejecutar hasta la línea")

   > [!NOTE]
   > El botón **Ejecutar hasta clic** es una novedad de [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. (Si no ve el botón con la flecha de color verde, presione **F11** en este ejemplo para hacer avanzar el depurador hasta el lugar correcto).

2. Haga clic en el botón **Ejecutar hasta clic**![Ejecutar hasta clic](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    El depurador avanza hasta el método `Console.WriteLine`.

    Usar este botón es similar a establecer un punto de interrupción temporal. La característica **Ejecutar hasta clic** es útil para desplazarse rápidamente por un área visible del código de la aplicación (puede hacer clic en cualquier archivo abierto).

## <a name="restart-your-app-quickly"></a>Reiniciar la aplicación rápidamente

Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas de depuración (**Ctrl** + **Mayús** + **F5**).

El botón **Reiniciar** permite ahorrar tiempo, ya que hace que no sea necesario detener la aplicación y reiniciar el depurador. El depurador se detiene en el primer punto de interrupción que se alcanza al ejecutar el código.

El depurador se detiene de nuevo en el punto de interrupción que ha establecido antes dentro del bucle `for`.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspeccionar variables con las ventanas Automático y Variables locales

1. Vea la ventana **Automático**, en la parte inferior del editor de código.

    Si está cerrada, ábrala mientras está en pausa en el depurador seleccionando **Depurar** > **Ventanas** > **Automático**.

    En la ventana **Automático** puede ver las variables y su valor actual. En la ventana **Automático** se muestran todas las variables que se usan en la línea actual o en la anterior. Para consultar el comportamiento específico de los lenguajes, vea la documentación.

1. A continuación, examine la ventana **Variables locales** en una pestaña situada junto a la ventana **Automático**.

1. Expanda la variable `letters` para mostrar los elementos que contiene.

     ![Inspección de variables en la ventana Variables locales](../csharp/media/get-started-locals-window.png "Ventana Locales")

    En la ventana **Variables locales** se muestran las variables que se encuentran en el [ámbito](https://www.wikipedia.org/wiki/Scope_(computer_science)) actual, es decir, en el contexto de ejecución actual.

## <a name="set-a-watch"></a>Establecer una inspección

1. En la ventana del editor de código principal, haga clic con el botón derecho en la variable `name` y elija **Agregar inspección**.

    En la parte inferior del editor de código se abre la ventana **Inspección**. Puede usar una ventana **Inspección** para especificar una variable (o una expresión) que quiera supervisar.

    Ahora, ha establecido una inspección en la variable `name` y puede ver cómo cambia su valor según avanza en el depurador. A diferencia de las otras ventanas de variables, en la ventana **Inspección** siempre se muestran las variables que está viendo (y se atenúan cuando están fuera del ámbito).

## <a name="examine-the-call-stack"></a>Examinar la pila de llamadas

1. Mientras esté en pausa en el bucle `for`, haga clic en la ventana **Pila de llamadas**, que se abrirá de forma predeterminada en el panel inferior derecho.

    Si está cerrada, ábrala mientras está en pausa en el depurador seleccionando **Depurar** > **Ventanas** > **Pila de llamadas**.

2. Presione **F11** varias veces hasta que vea que el depurador se detiene en el método `SendMessage`. Eche un vistazo a la ventana **Pila de llamadas**.

    ![Examen de la pila de llamadas](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    En la ventana **Pila de llamadas** se muestra el orden en el que se llama a los métodos y las funciones. En la línea superior se muestra la función actual (el método `SendMessage` en esta aplicación). En la segunda línea se mostrará que se ha llamado a `SendMessage` desde el método `Main`, y así sucesivamente.

   > [!NOTE]
   > La ventana **Pila de llamadas** es similar a la perspectiva de depuración de algunos IDE, como Eclipse.

    La pila de llamadas es una buena forma de examinar y entender el flujo de ejecución de una aplicación.

    Puede hacer doble clic en una línea de código para ver ese código fuente. De este modo, también puede cambiar el ámbito que el depurador va a inspeccionar. Esta acción no hace avanzar el depurador.

    También puede usar los menús contextuales de la ventana **Pila de llamadas** para hacer otras cosas. Por ejemplo, puede insertar puntos de interrupción en funciones especificadas, avanzar el depurador mediante **Ejecutar hasta el cursor** y examinar el código fuente. Para obtener más información, vea [Cómo: Examinar la pila de llamadas](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Cambio del flujo de ejecución

1. Presione **F11** dos veces para ejecutar el método `Console.WriteLine`.

1. Con el depurador en pausa en la llamada al método `SendMessage`, use el mouse para seleccionar la flecha de color amarillo (el puntero de ejecución) de la izquierda y moverla una línea hacia arriba, para volver a `Console.WriteLine`.

1. Presione **F11**.

    El depurador volverá a ejecutar el método `Console.WriteLine`, lo cual se puede consultar en la salida de la ventana de la consola.

    Al cambiar el flujo de ejecución, puede, por ejemplo, comprobar las diferentes rutas de ejecución de código o volver a ejecutar código sin tener que reiniciar el depurador.

    > [!WARNING]
    > A menudo es necesario tener cuidado con esta característica, ya que puede ser que vea una advertencia en la información en pantalla. También puede ser que reciba otras advertencias. El hecho de mover el puntero no permite revertir la aplicación a un estado anterior.

1. Presione **F5** para seguir ejecutando la aplicación.

    Enhorabuena por completar este tutorial.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a iniciar el depurador, a ejecutar el código paso a paso y a inspeccionar variables. Puede ser que le interese analizar las características del depurador con más detenimiento, así como consultar los vínculos disponibles con más información.

> [!div class="nextstepaction"]
> [Primer vistazo al depurador](../../debugger/debugger-feature-tour.md)
