---
title: Depurar aplicaciones multiproceso en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2017
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 1d238f1c6be12753fe87cece03139185e1c24ad6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854780"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicaciones multiproceso en Visual Studio
Un subproceso es una secuencia de instrucciones a la que el sistema operativo asigna tiempo de procesador. Cada proceso que se ejecuta en el sistema operativo contiene al menos un subproceso. Los procesos que tienen más de un subproceso se denominan multiproceso.  
  
Equipos con varios procesadores, con varios núcleos o con tecnología hyperthreading pueden ejecutar varios subprocesos al mismo tiempo. El procesamiento en paralelo de varios subprocesos puede mejorar notablemente el rendimiento del programa, pero también puede dificultar la depuración porque incluye la necesidad de efectuar el seguimiento de varios subprocesos.  
  
Además, multithreading incluye algunos tipos de errores nuevos. Por ejemplo, a menudo dos o más subprocesos deben tener acceso al mismo recurso, pero únicamente un subproceso puede tener acceso al recurso sin ningún riesgo a la vez. Se necesita algún formulario de exclusión mutua para asegurarse de que únicamente uno subproceso está teniendo acceso al recurso a la vez. Si la exclusión mutua se realiza correctamente, puede crear un *interbloqueo* condición donde ningún subproceso puede ejecutar. Los interbloqueos pueden ser un problema especialmente grave para realizar la depuración.

Visual Studio proporciona diferentes herramientas para su uso en la depuración de aplicaciones multiproceso.

- Para los subprocesos, las herramientas principales para depurar subprocesos son la **subprocesos** (ventana), los marcadores de subprocesos en ventanas de código fuente, **pilas paralelas** ventana, **inspección paralela** ventana, y el **ubicación de depuración** barra de herramientas. Para obtener información sobre la **subprocesos** ventana y **ubicación de depuración** barra de herramientas, consulte [Tutorial: depurar con la ventana subprocesos](../debugger/how-to-use-the-threads-window.md). Para obtener información sobre cómo usar el **pilas paralelas** y **inspección paralela** windows, vea [empezar a depurar una aplicación multiproceso](../debugger/get-started-debugging-multithreaded-apps.md). Ambos temas muestra cómo usar los marcadores de subprocesos.
  
- Para código que usa el [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o [Runtime de simultaneidad](/cpp/parallel/concrt/concurrency-runtime/), son las herramientas principales para depurar el **pilas paralelas** (ventana), el **Inspección paralela** ventana y el **tareas** ventana (la **tareas** ventana también es compatible con JavaScript). Para empezar, vea [Tutorial: depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md) y [Tutorial: depurar una aplicación de C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Para depurar subprocesos en la GPU, la herramienta principal es el **subprocesos de GPU** ventana. Consulte [Cómo: utilizar la ventana subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Para los procesos, las herramientas principales son el **asociar al proceso** cuadro de diálogo, el **procesos** ventana y el **ubicación de depuración** barra de herramientas.  
  
Visual Studio también proporciona eficaces puntos de interrupción y puntos de seguimiento, que pueden resultar muy útiles para depurar aplicaciones multiproceso. Puede usar filtros y las condiciones de punto de interrupción para colocar puntos de interrupción en subprocesos individuales. Consulte [usar puntos de interrupción](../debugger/using-breakpoints.md). 
  
Depurar una aplicación multiproceso que tiene una interfaz de usuario puede resultar especialmente difícil. En ese caso, puede que considere ejecutar la aplicación en un segundo equipo y usar la depuración remota. Para obtener información, consulte [depuración remota](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>En esta sección
 [Empezar a depurar una aplicación multiproceso](../debugger/get-started-debugging-multithreaded-apps.md).  
 Una visita guiada de subproceso de depuración de las características, con especial hincapié en las características de la **pilas paralelas** ventana y **inspección paralela** ventana.

 [Herramientas para depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md)  
 Enumera las características de las herramientas para depurar procesos y subprocesos.  
  
 [Depurar varios procesos](../debugger/debug-multiple-processes.md)  
 Explica cómo depurar varios procesos.

 [Tutorial: Depurar con la ventana subprocesos](../debugger/how-to-use-the-threads-window.md).  
 Tutorial que muestra cómo utilizar el **subprocesos** ventana y la **ubicación de depuración** barra de herramientas. 

 [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Tutorial que muestra cómo utilizar el **pilas paralelas** y **tareas** windows.  
  
 [Cómo: Cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Tres maneras de modificar el contexto de depuración a otro subproceso.  
  
 [Cómo: Marcar y desmarcar subprocesos](../debugger/how-to-flag-and-unflag-threads.md)  
 Marque los subprocesos a los que desea prestar especial atención mientras se realiza la depuración.    
  
 [Cómo: Depurar en un clúster de alto rendimiento](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Técnicas para depurar una aplicación que se ejecuta en un clúster de alto rendimiento.  

 [Sugerencias para depurar subprocesos en código nativo](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Técnicas simples que pueden ser útiles para depurar los subprocesos nativos. 

 [Cómo: Establecer un nombre de subproceso en código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Asigne al subproceso de un nombre que se ve en el **subprocesos** ventana.  
  
 [Cómo: Establecer un nombre de subproceso en código administrado](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Asigne al subproceso de un nombre que se ve en el **subprocesos** ventana. 
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)

- Utilice filtros o las condiciones de punto de interrupción cuando desea depurar un subproceso individual.  
  
- Los puntos de seguimiento le habilitan para poder seguir paso a paso ejecución de su programa sin interrupciones. Esto puede ser útil para estudiar problemas como los interbloqueos.  
  
  [Subprocesamiento](/dotnet/standard/threading/index)  
  Conceptos relacionados con el subprocesamiento en programación de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], incluido el código de ejemplo.  
  
  [Subprocesamiento múltiple en componentes](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
  Cómo usar multithreading en componentes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
  [Compatibilidad del código antiguo con multithreading (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
  Conceptos relacionados con el subprocesamiento para programadores de C++ mediante MFC.  
  
## <a name="see-also"></a>Vea también  
 [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md)   
 [Remote Debugging](../debugger/remote-debugging.md)