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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07710ed0188baf48a567bb3c003f174814c30094
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "53907896"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicaciones multiproceso en Visual Studio
Un subproceso es una secuencia de instrucciones a los que el sistema operativo concede el tiempo de procesador. Cada proceso que se ejecuta en el sistema operativo contiene al menos un subproceso. Los procesos que tienen más de un subproceso se denominan multiproceso.  
  
Equipos con varios procesadores, procesadores multinúcleo o procesos de hyperthreading pueden ejecutar varios subprocesos simultáneos. Procesamiento en paralelo mediante varios subprocesos puede mejorar considerablemente el rendimiento del programa, pero es posible que también dificultar la depuración más porque se está realizando el seguimiento de muchos subprocesos.  
  
El multithreading puede introducir a nuevos tipos de posibles errores. Por ejemplo, dos o más subprocesos que deba tener acceso al mismo recurso, pero solo un subproceso a la vez sin ningún riesgo puede tener acceso al recurso. Algún tipo de exclusión mutua es necesario asegurarse de que solo un subproceso tiene acceso al recurso en cualquier momento. Si la exclusión mutua se implementa incorrectamente, puede crear un *interbloqueo* condición donde no se ejecutará ningún subproceso. Los interbloqueos suelen ser un problema difícil de depurar.

## <a name="tools-for-debugging-multithreaded-apps"></a>Herramientas para depurar aplicaciones multiproceso

Visual Studio proporciona diferentes herramientas para su uso en la depuración de aplicaciones multiproceso.

- Para los subprocesos, las herramientas principales para depurar subprocesos son la **subprocesos** (ventana), los marcadores de subprocesos en ventanas de código fuente, el **pilas paralelas** ventana, el **inspección paralela** ventana y el **ubicación de depuración** barra de herramientas. Para obtener información sobre la **subprocesos** ventana y **ubicación de depuración** barra de herramientas, consulte [Tutorial: Depuración con la ventana Subprocesos](../debugger/how-to-use-the-threads-window.md). Para obtener información sobre cómo usar el **pilas paralelas** y **inspección paralela** windows, vea [empezar a depurar una aplicación multiproceso](../debugger/get-started-debugging-multithreaded-apps.md). Ambos temas muestra cómo usar los marcadores de subprocesos.
  
- Para código que usa el [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o [Runtime de simultaneidad](/cpp/parallel/concrt/concurrency-runtime/), son las herramientas principales para depurar el **pilas paralelas** (ventana), el **Inspección paralela** ventana y el **tareas** ventana, que también es compatible con JavaScript. Para empezar, vea [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md) y [Tutorial: Depurar una aplicación C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Para depurar subprocesos en la GPU, la herramienta principal es el **subprocesos de GPU** ventana. Vea [Cómo: usar la ventana Subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Para los procesos, las herramientas principales son el **asociar al proceso** cuadro de diálogo, el **procesos** ventana y el **ubicación de depuración** barra de herramientas.  
  
Visual Studio también proporciona eficaces puntos de interrupción y puntos de seguimiento, que pueden ser útiles al depurar aplicaciones multiproceso. Usar filtros y las condiciones de punto de interrupción para colocar puntos de interrupción en subprocesos individuales. Puntos de seguimiento Habilitar seguimiento de la ejecución del programa sin interrumpir para estudiar problemas como interbloqueos. Para obtener más información, consulte [acciones de punto de interrupción y puntos de seguimiento](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Depurar una aplicación multiproceso que tiene una interfaz de usuario puede resultar especialmente difícil. Es posible que tenga en cuenta que se ejecuta la aplicación en un segundo equipo y usar la depuración remota. Para obtener más información, consulte [depuración remota](../debugger/remote-debugging.md).  
  
## <a name="articles-about-debugging-multithreaded-apps"></a>Artículos sobre cómo depurar aplicaciones multiproceso

 [Empezar a depurar una aplicación multiproceso](../debugger/get-started-debugging-multithreaded-apps.md)   
 Un paseo por subproceso de depuración de las características, con énfasis en las características de la **pilas paralelas** ventana y la **inspección paralela** ventana.

 [Herramientas para depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md)  
 Enumera las características de las herramientas para depurar procesos y subprocesos.  
  
 [Depuración de varios procesos](../debugger/debug-multiple-processes.md)  
 Explica cómo depurar varios procesos.

 [Tutorial: Depuración con la ventana Subprocesos](../debugger/how-to-use-the-threads-window.md).  
 Tutorial que muestra cómo utilizar el **subprocesos** ventana y la **ubicación de depuración** barra de herramientas. 

 [Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Tutorial que muestra cómo utilizar el **pilas paralelas** y **tareas** windows.  
  
 [Cómo: cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Varias formas de cambiar el contexto de depuración a otro subproceso.  
  
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

[Uso de puntos de interrupción](../debugger/using-breakpoints.md)  
[Subprocesamiento](/dotnet/standard/threading/index)  
[Multithreading en componentes](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
[Soporte técnico del código antiguo con multithreading (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md)   
 [Depuración remota](../debugger/remote-debugging.md)