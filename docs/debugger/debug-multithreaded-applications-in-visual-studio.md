---
title: Depurar aplicaciones multiproceso | Microsoft Docs
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431809"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicaciones multiproceso en Visual Studio
Un subproceso es una secuencia de instrucciones a la que el sistema operativo concede el tiempo de procesador. Cada proceso que se ejecuta en el sistema operativo contiene al menos un subproceso. Los procesos que tienen más de un subproceso se denominan multiproceso.

Los equipos con varios procesadores, procesadores de varios núcleos o procesos de hyperthreading pueden ejecutar varios subprocesos simultáneos. El procesamiento en paralelo con muchos subprocesos puede mejorar considerablemente el rendimiento del programa, pero también puede dificultar la depuración porque está realizando el seguimiento de muchos subprocesos.

El multithreading puede introducir nuevos tipos de posibles errores. Por ejemplo, dos o más subprocesos pueden necesitar tener acceso al mismo recurso, pero solo un subproceso a la vez puede tener acceso de forma segura al recurso. Se necesita algún tipo de exclusión mutua para asegurarse de que solo un subproceso tiene acceso al recurso en cualquier momento. Si la exclusión mutua se implementa incorrectamente, puede crear una condición de *interbloqueo* en la que no se ejecutará ningún subproceso. Los interbloqueos suelen ser un problema difícil de depurar.

## <a name="tools-for-debugging-multithreaded-apps"></a>Herramientas para depurar aplicaciones multiproceso

Visual Studio proporciona diferentes herramientas para la depuración de aplicaciones multiproceso.

- Para los subprocesos, las herramientas principales para depurar subprocesos son la ventana **subprocesos** , los marcadores de subprocesos en las ventanas de código fuente, la ventana **pilas paralelas** , la ventana **inspección paralela** y la barra de herramientas **Ubicación de depuración** . Para obtener información sobre la **subprocesos** ventana y **ubicación de depuración** barra de herramientas, consulte [Tutorial: Depurar con la ventana Subprocesos](../debugger/how-to-use-the-threads-window.md). Para obtener información sobre cómo usar las ventanas **pilas paralelas** y **inspección paralela** , vea [Introducción a la depuración de una aplicación multiproceso](../debugger/get-started-debugging-multithreaded-apps.md). Ambos temas muestran cómo usar los marcadores de subproceso.

- En el caso del código que usa la [biblioteca de procesamiento paralelo de tareas (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o el [Runtime de simultaneidad](/cpp/parallel/concrt/concurrency-runtime/), las herramientas principales para la depuración son la ventana **pilas paralelas** , la ventana **inspección paralela** y la ventana **tareas** , que también admite Código. Para empezar, vea [Tutorial: depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md) y [Tutorial: depurar C++ una aplicación de amp](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application).

- Para depurar subprocesos en la GPU, la herramienta principal es la ventana **subprocesos de GPU** . Consulte [Cómo: usar la ventana subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md).

- En el caso de los procesos, las herramientas principales son el cuadro de diálogo **asociar al proceso** , la ventana **procesos** y la barra de herramientas **Ubicación de depuración** .

Visual Studio también proporciona puntos de interrupción y puntos de seguimiento eficaces, lo que puede resultar útil al depurar aplicaciones multiproceso. Use condiciones y filtros de punto de interrupción para colocar puntos de interrupción en subprocesos individuales. Los puntos de seguimiento le permiten realizar un seguimiento de la ejecución del programa sin interrupciones, para estudiar problemas como los interbloqueos. Para obtener más información, vea [acciones de punto de interrupción y puntos de seguimiento](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Depurar una aplicación multiproceso que tiene una interfaz de usuario puede resultar especialmente difícil. Puede considerar la posibilidad de ejecutar la aplicación en un segundo equipo y usar la depuración remota. Para obtener más información, vea [depuración remota](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Artículos sobre la depuración de aplicaciones multiproceso

 [Introducción a la depuración de una aplicación multiproceso](../debugger/get-started-debugging-multithreaded-apps.md)

Un paseo por las características de depuración de subprocesos, resaltando las características de la ventana **pilas paralelas** y la ventana **inspección paralela** .

 [Herramientas para depurar subprocesos y procesos](../debugger/debug-threads-and-processes.md)

Enumera las características de las herramientas para depurar subprocesos y procesos.

 [Depuración de varios procesos](../debugger/debug-multiple-processes.md)

Explica cómo depurar varios procesos.

 [Tutorial: Depurar con la ventana Subprocesos](../debugger/how-to-use-the-threads-window.md).

Tutorial que muestra cómo usar la ventana **subprocesos** y la barra de herramientas **Ubicación de depuración** .

 [Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)

Tutorial que muestra cómo usar las ventanas **pilas paralelas** y **tareas** .

 [Cambio a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Varias maneras de cambiar el contexto de depuración a otro subproceso.

 [Marcar y desmarcar subprocesos](../debugger/how-to-flag-and-unflag-threads.md)

Marque los subprocesos a los que desea prestar especial atención mientras se realiza la depuración.

 [Cómo: Depurar en un clúster de alto rendimiento](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Técnicas para depurar una aplicación que se ejecuta en un clúster de alto rendimiento.

 [Sugerencias para depurar subprocesos en código nativo](../debugger/tips-for-debugging-threads-in-native-code.md)

Técnicas simples que pueden ser útiles para depurar los subprocesos nativos.

 [Cómo establecer un nombre de subproceso en código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)

Asigne al subproceso uno de los nombres que aparecen en la ventana **Subprocesos**.

 [Definición de un nombre de subproceso en código administrado](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Asigne al subproceso uno de los nombres que aparecen en la ventana **Subprocesos**.

## <a name="see-also"></a>Vea también

- [Uso de puntos de interrupción](../debugger/using-breakpoints.md)
- [Subprocesamiento](/dotnet/standard/threading/index)
- [Multithreading en componentes](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)
- [Compatibilidad con multithreading para código anterior](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md)
- [Depuración remota](../debugger/remote-debugging.md)