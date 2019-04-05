---
title: Depurar aplicaciones multiproceso
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 821396989a2de9444fdbf3499709588d00e66b45
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "59001901"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicaciones multiproceso en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un subproceso es una secuencia de instrucciones a la que el sistema operativo asigna tiempo de procesador. Cada proceso que se ejecuta en el sistema operativo contiene al menos un subproceso. Los procesos que tienen más de un subproceso se denominan multiproceso.

 Equipos con varios procesadores, con varios núcleos o con tecnología hyperthreading pueden ejecutar varios subprocesos al mismo tiempo. El procesamiento en paralelo de varios subprocesos puede mejorar notablemente el rendimiento del programa, pero también puede dificultar la depuración porque incluye la necesidad de efectuar el seguimiento de varios subprocesos.

 Además, multithreading incluye algunos tipos de errores nuevos. Por ejemplo, a menudo dos o más subprocesos deben tener acceso al mismo recurso, pero únicamente un subproceso puede tener acceso al recurso sin ningún riesgo a la vez. Se necesita algún formulario de exclusión mutua para asegurarse de que únicamente uno subproceso está teniendo acceso al recurso a la vez. Si la exclusión mutua se realiza correctamente, puede crear un *interbloqueo* condición donde ningún subproceso puede ejecutar. Los interbloqueos pueden ser un problema especialmente grave para realizar la depuración.

 Visual Studio proporciona un **subprocesos** ventana, una ventana de subprocesos de GPU, una ventana Inspección paralela y otras características que facilitan la depuración multiproceso. La mejor manera de obtener información sobre las características de subprocesos es realizar los tutoriales. Vea [Tutorial: Depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md) y [Tutorial: Depurar una aplicación de C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Visual Studio también proporciona eficaces puntos de interrupción y puntos de seguimiento, que pueden resultar muy útiles para depurar aplicaciones multiproceso. Puede utilizar filtros de puntos de interrupción para colocar puntos de interrupción en subprocesos individuales. Consulte [usar puntos de interrupción](../debugger/using-breakpoints.md)

 Depurar una aplicación multiproceso que tiene una interfaz de usuario puede resultar especialmente difícil. En ese caso, puede que considere ejecutar la aplicación en un segundo equipo y usar la depuración remota. Para obtener información, consulte [depuración remota](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>En esta sección
 [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md) explica los conceptos básicos de la depuración de procesos y subprocesos.

 [Depurar varios procesos](../debugger/debug-multiple-processes.md) se explica cómo depurar varios procesos.

 [Cómo: Utilice la ventana subprocesos](../debugger/how-to-use-the-threads-window.md) procedimientos útiles para depurar subprocesos con el **subprocesos** ventana.

 [Cómo: Cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md) tres formas de cambiar el contexto de depuración a otro subproceso.

 [Cómo: Marca y desmarcar subprocesos](../debugger/how-to-flag-and-unflag-threads.md) Marque los subprocesos que desea prestar especial atención al depurar.

 [Cómo: Establecer un nombre de subproceso en código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md) asigne al subproceso de un nombre que se ve en el **subprocesos** ventana.

 [Cómo: Establecer un nombre de subproceso en código administrado](../debugger/how-to-set-a-thread-name-in-managed-code.md) asigne al subproceso de un nombre que se ve en el **subprocesos** ventana.

 [Tutorial: Depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Un paseo guiado por las características de depuración de subprocesos, con especial hincapié en los procedimientos de [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 [Cómo: Depurar en un clúster de alto rendimiento](../debugger/how-to-debug-on-a-high-performance-cluster.md) técnicas para depurar una aplicación que se ejecuta en un clúster de alto rendimiento.

 [Sugerencias para depurar subprocesos en código nativo](../debugger/tips-for-debugging-threads-in-native-code.md) técnicas sencillas que pueden ser útiles para depurar subprocesos nativos.

 [Usar la ventana tareas](../debugger/using-the-tasks-window.md) muestra una lista de todos los objetos de tarea administrados o nativos que incluye su estado y otra información útil.

 [Uso de la ventana Pilas paralelas](../debugger/using-the-parallel-stacks-window.md) llamada muestra las pilas de varios subprocesos (o tareas) en una vista única y también combina segmentos de pila que son comunes entre los subprocesos (o tareas).

 [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md) tutorial que muestra cómo utilizar las ventanas Parallel Tasks y Parallel Stacks.

 [Cómo: Utilizar la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md) inspeccionar valores y expresiones en varios subprocesos.

 [Cómo: Utilice la ventana de subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md) examinar y trabajar con subprocesos que se ejecutan en la GPU durante la depuración.

## <a name="related-sections"></a>Secciones relacionadas
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)
 -   Use filtros de puntos de interrupción si desea colocar un punto de interrupción en un subproceso individual.

- Los puntos de seguimiento le habilitan para poder seguir paso a paso ejecución de su programa sin interrupciones. Esto puede ser útil para estudiar problemas como los interbloqueos.

  [Subprocesamiento](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) Threading conceptos en [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programación, incluido el código de ejemplo.

  [Subprocesamiento múltiple en componentes](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) cómo usar multithreading en [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] componentes.

  [Compatibilidad con multithreading (Visual C++) del código antiguo](http://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) conceptos y el código de ejemplo de subprocesamiento para programadores de C++ mediante MFC.

## <a name="see-also"></a>Vea también
 [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md) [depuración remota](../debugger/remote-debugging.md)
