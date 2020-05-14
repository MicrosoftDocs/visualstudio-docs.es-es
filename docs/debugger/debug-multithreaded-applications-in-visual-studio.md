---
title: Depuración de aplicaciones multiproceso | Microsoft Docs
ms.custom: seodec18
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 668e95c340348eeb1fa509622aa44d99b65b6efc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431809"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicaciones multiproceso en Visual Studio
Un subproceso es una secuencia de instrucciones a la que el sistema operativo concede tiempo de procesador. Cada proceso que se ejecuta en el sistema operativo contiene al menos un subproceso. Los procesos que tienen más de un subproceso se denominan multiproceso.

Equipos con varios procesadores, procesadores de varios núcleos o procesos hyperthreading pueden ejecutar varios subprocesos simultáneos. El procesamiento en paralelo con muchos subprocesos puede mejorar considerablemente el rendimiento del programa, pero también puede dificultar la depuración porque se realiza el seguimiento de muchos subprocesos.

El multithreading puede introducir nuevos tipos de posibles errores. Por ejemplo, dos o más subprocesos pueden necesitar acceso al mismo recurso, pero únicamente un subproceso a la vez puede acceder al recurso con seguridad. Se necesita algún formulario de exclusión mutua para asegurarse de que únicamente un subproceso está teniendo acceso al recurso en cualquier momento. Si se implementa la exclusión mutua incorrectamente, puede crear una condición *interbloqueo* donde no se ejecutará ningún subproceso. Los interbloqueos suelen ser un problema difícil de depurar.

## <a name="tools-for-debugging-multithreaded-apps"></a>Herramientas para depurar aplicaciones multiproceso

Visual Studio proporciona diferentes herramientas para la depuración de aplicaciones multiproceso.

- En el caso de los subprocesos, las herramientas principales para depurar subprocesos son la ventana **Subprocesos**, los marcadores de subprocesos en ventanas de código fuente, la ventana **Pilas paralelas**, la ventana **Inspección paralela** y la barra de herramientas **Ubicación de depuración**. Para obtener información sobre la ventana **Subprocesos** y la barra de herramientas **Ubicación de depuración**, vea [Tutorial: Depuración con la ventana Subprocesos](../debugger/how-to-use-the-threads-window.md). Para obtener información sobre cómo usar las ventanas **Pilas paralelas** e **Inspección paralela**, vea [Introducción a la depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md). Ambos temas muestran cómo usar los marcadores de subproceso.

- En el caso del código que usa la [Biblioteca TPL](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o el [Runtime de simultaneidad](/cpp/parallel/concrt/concurrency-runtime/), las herramientas principales para depurar son la ventana **Pilas paralelas**, la ventana **Inspección paralela** y la ventana **Tareas**, que también admite JavaScript. Para empezar, vea [Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md) y [Tutorial: Depurar una aplicación de C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application).

- Para depurar subprocesos en la GPU, la herramienta principal es la ventana **Subprocesos de GPU**. Vea [Cómo: usar la ventana Subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md).

- En el caso de los procesos, las herramientas principales son el cuadro de diálogo **Asociar al proceso**, la ventana **Procesos** y la barra de herramientas **Ubicación de depuración**.

Visual Studio también proporciona eficaces puntos de interrupción y puntos de seguimiento, que pueden resultar útiles para depurar aplicaciones multiproceso. Use condiciones y filtros de puntos de interrupción para colocar puntos de interrupción en subprocesos individuales. Los puntos de seguimiento permiten poder seguir paso a paso la ejecución de su programa sin interrupciones, para estudiar problemas como los interbloqueos. Para más información, vea [Acciones de punto de interrupción y puntos de seguimiento](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Depurar una aplicación multiproceso que tiene una interfaz de usuario puede resultar especialmente difícil. Puede que considere ejecutar la aplicación en un segundo equipo y usar la depuración remota. Para más información, vea [Depuración remota](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Artículos sobre la depuración de aplicaciones multiproceso

 [Introducción a la depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md)

Un recorrido por las características de depuración de subprocesos en la ventana **Pilas paralelas** y la ventana **Inspección paralela**.

 [Herramientas para depurar subprocesos y procesos](../debugger/debug-threads-and-processes.md)

Se enumeran las características de las herramientas para depurar subprocesos y procesos.

 [Depuración de varios procesos](../debugger/debug-multiple-processes.md)

Explica cómo depurar varios procesos.

 [Tutorial: Depuración con la ventana Subprocesos](../debugger/how-to-use-the-threads-window.md).

Tutorial en el que se explica cómo usar la ventana **Subprocesos** y la barra de herramientas **Ubicación de depuración**.

 [Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)

Tutorial en el que se explica cómo usar las ventanas **Pilas paralelas** y **Tareas**.

 [Cómo: cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Varias maneras de modificar el contexto de depuración a otro subproceso.

 [Cómo: marcar y desmarcar subprocesos](../debugger/how-to-flag-and-unflag-threads.md)

Marque los subprocesos a los que desea prestar especial atención mientras se realiza la depuración.

 [Cómo: depurar en un clúster de alto rendimiento](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Técnicas para depurar una aplicación que se ejecuta en un clúster de alto rendimiento.

 [Sugerencias para depurar subprocesos en código nativo](../debugger/tips-for-debugging-threads-in-native-code.md)

Técnicas simples que pueden ser útiles para depurar los subprocesos nativos.

 [Cómo: establecer un nombre de subproceso en código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)

Asigne al subproceso uno de los nombres que aparecen en la ventana **Subprocesos**.

 [Cómo: establecer un nombre de subproceso en código administrado](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Asigne al subproceso uno de los nombres que aparecen en la ventana **Subprocesos**.

## <a name="see-also"></a>Vea también

- [Uso de puntos de interrupción](../debugger/using-breakpoints.md)
- [Subprocesamiento](/dotnet/standard/threading/index)
- [Multithreading en componentes](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)
- [Compatibilidad del código antiguo con multithreading](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md)
- [Depuración remota](../debugger/remote-debugging.md)