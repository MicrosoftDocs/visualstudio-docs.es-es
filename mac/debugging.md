---
title: Depuración con Visual Studio para Mac
description: La depuración es una parte común y necesaria de la programación. Como IDE consolidado, Visual Studio para Mac contiene un completo conjunto de características para facilitar la depuración. En este artículo se explica cómo usar todo el potencial de depuración de Visual Studio para Mac, desde la depuración segura a la visualización de datos.
author: therealjohn
ms.author: johmil
ms.date: 5/13/2020
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.topic: overview
ms.openlocfilehash: 09a761a8269fa40c3fab49a34b3e43a7f0ec63cd
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939079"
---
# <a name="debugging-with-visual-studio-for-mac"></a>Depuración con Visual Studio para Mac

Visual Studio para Mac tiene depuradores compatibles con las aplicaciones .NET Core, .NET Framework, Unity y Xamarin.

Visual Studio para Mac usa [*Mono Soft Debugger*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), que está implementado en el entorno de ejecución Mono, lo que permite a Visual Studio para Mac depurar código administrado en todas las plataformas.

## <a name="the-debugger"></a>Depurador

Visual Studio para Mac usa Mono Soft Debugger para depurar código administrado (C# o F#) en todas las aplicaciones de Xamarin. Mono Soft Debugger difiere de los depuradores normales en que se trata de un depurador cooperativo que está integrado en el entorno de ejecución Mono; el código generado y el entorno de ejecución Mono cooperan con el IDE para proporcionar una experiencia de depuración. El entorno de ejecución Mono expone la funcionalidad de depuración a través de un protocolo de conexión sobre el que puede leer más [en la documentación de Mono](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).

Los depuradores duros, como [LLDB]( http://lldb.llvm.org/index.html) o [GDB]( https://www.gnu.org/software/gdb/), controlan un programa sin el conocimiento ni la cooperación del programa depurado, aunque pueden resultar útiles al depurar aplicaciones de Xamarin en caso de que se necesite depurar código Android o iOS nativo.

En el caso de las aplicaciones de .NET Core y ASP.NET Core, Visual Studio para Mac usa el depurador de .NET Core. Este depurador también es un depurador cooperativo y funciona con el entorno de ejecución de .NET.

## <a name="using-the-debugger"></a>Empleo del depurador

Para empezar a depurar cualquier aplicación, asegúrese siempre de que la configuración esté establecida en **Depurar**. La configuración de depuración proporciona un útil conjunto de herramientas para permitir la depuración, como los puntos de interrupción, el uso de visualizadores de datos y la visualización de la pila de llamadas:

![La configuración es Debug.](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Establecer un punto de interrupción

Para establecer un punto de interrupción en el IDE, haga clic en el margen del editor, junto al número de línea del código en el que quiere interrumpir:

![Establecimiento de punto de interrupción en el margen](media/debugging-image0.png)

Puede ver todos los puntos de interrupción que se establecieron en el código en el  **Panel de puntos de interrupción**:

![Lista de puntos de interrupción](media/debugging-image0a.png)

## <a name="start-debugging"></a>Iniciar depuración

Para iniciar la depuración, seleccione el explorador, dispositivo o simulador/emulador de destino:

![Configuración de depuración](media/debugging-image_0.png)
![Selección de dispositivo de destino](media/debugging-image1.png)

Luego implemente la aplicación al hacer clic en el botón **Reproducir** o presionar **Cmd + Entrar**. Cuando se alcance un punto de interrupción, el código se resaltará en amarillo:

![Resaltado que muestra que se ha alcanzado el punto de interrupción](media/debugging-image2.png)

En este punto se pueden usar herramientas de depuración, como la usada para inspeccionar los valores de objetos, para obtener más información sobre lo que sucede en el código:

![Visualizaciones de depuración](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Puntos de interrupción condicionales

También puede establecer reglas que dicten las circunstancias en las que debería ocurrir un punto de interrupción, lo que se conoce como agregar un *punto de interrupción condicional*. Para establecer un punto de interrupción condicional, obtenga acceso a la **ventana de propiedades del punto de interrupción**, lo cual puede hacerse de dos maneras:

* Para agregar un nuevo punto de interrupción condicional, haga clic con el botón derecho en el margen del editor, a la izquierda del número de línea del código para el que quiere establecer un punto de interrupción y seleccione Nuevo punto de interrupción:

 ![Menú contextual de Punto de interrupción](media/debugging-image4.png)

* Para agregar una condición a un punto de interrupción existente, haga clic con el botón derecho en el punto de interrupción y seleccione **Propiedades de punto de interrupción** o bien, en el **Panel de puntos de interrupción**, seleccione el botón Editar punto de interrupción que se muestra a continuación:

 ![Edición de punto de interrupción existente en el panel de puntos de interrupción](media/debugging-image5.png)

Luego puede escribir la condición bajo la que quiere que se produzca el punto de interrupción:

 ![Condiciones de Editar punto de interrupción](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Ejecución paso a paso del código

Cuando se ha alcanzado un punto de interrupción, las herramientas de depuración permiten obtener el control sobre la ejecución del programa. Visual Studio para Mac muestra cuatro botones que permiten ejecutar y recorrer el código. En Visual Studio para Mac, tienen un aspecto similar al siguiente:

 ![Botones para recorrer el código](media/debugging-image7.png)

Estos son los cuatro botones:

* **Reproducir**: inicia la ejecución del código hasta el siguiente punto de interrupción.
* **Paso a paso por procedimientos**: ejecuta la siguiente línea de código. Si la siguiente línea es una llamada a función, Paso a paso por procedimientos ejecuta la función y se detiene en la siguiente línea de código *después* de la función.
* **Depurar paso a paso con instrucciones**: también ejecuta la siguiente línea de código. Si la siguiente línea es una llamada de función, Depurar paso a paso con instrucciones se detendrá en la primera línea de la función, lo que le permitirá continuar con la depuración línea por línea de la función. Si la línea siguiente no es una función, se comportará igual Paso a paso por procedimientos.
* **Paso a paso para salir**: vuelve a la línea en la que se ha llamado a la función actual.

## <a name="change-which-statement-is-executed-next"></a>Cambio de la instrucción que se ejecuta a continuación

Cuando el depurador está pausado, hay una flecha en el margen que indica qué línea de código se ejecutará a continuación. Puede hacer clic en la flecha y arrastrarla a otra línea de código para cambiar qué instrucción se ejecutará. Puede conseguir lo mismo haciendo clic con el botón derecho en una línea de código y seleccionando **Establecer instrucción siguiente** en el menú contextual.

![Arrastre y colocación de la flecha para establecer la instrucción siguiente](media/debugger-drag-setnextstatement.gif)

> [!CAUTION]
> El cambio de la línea de ejecución actual puede producir un comportamiento inesperado en una aplicación. También hay algunas condiciones en las que no es posible cambiar la siguiente instrucción que se va a ejecutar. Por ejemplo, si se arrastra la flecha de un método a otro, no funcionará. En estos casos no admitidos, Visual Studio para Mac mostrará un cuadro de diálogo que le indicará que no es posible cambiar la línea de ejecución actual. 

## <a name="debugging-monos-class-libraries"></a>Depuración de bibliotecas de clases de Mono

Los productos de Xamarin se distribuyen con el código fuente de las bibliotecas de clases de Mono, que se puede usar para ver cómo funcionan las cosas con el depurador.

Puesto que esta característica consume más memoria durante la depuración, está desactivada de forma predeterminada.

Para habilitar esta característica, vaya a **Visual Studio para Mac > Preferencias > Depurador** y asegúrese de que la opción "**Depuración paso a paso por instrucciones del código externo**" esté **seleccionada**, como se ilustra a continuación:

![Opción Depuración paso a paso por instrucciones del código externo](media/debugging-image8.png)

## <a name="see-also"></a>Vea también

- [Depuración en Visual Studio (en Windows)](/visualstudio/debugger/)
