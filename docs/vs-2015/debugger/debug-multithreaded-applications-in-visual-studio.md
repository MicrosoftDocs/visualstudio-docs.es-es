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
ms.openlocfilehash: 8cb43c9a32f3dfd0a6383d466f7cd283acf0ab3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691277"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicaciones multiproceso en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un subproceso es una secuencia de instrucciones a la que el sistema operativo asigna tiempo de procesador. Cada proceso que se ejecuta en el sistema operativo contiene al menos un subproceso. Los procesos que tienen más de un subproceso se denominan multiproceso.

 Equipos con varios procesadores, con varios núcleos o con tecnología hyperthreading pueden ejecutar varios subprocesos al mismo tiempo. El procesamiento en paralelo de varios subprocesos puede mejorar notablemente el rendimiento del programa, pero también puede dificultar la depuración porque incluye la necesidad de efectuar el seguimiento de varios subprocesos.

 Además, multithreading incluye algunos tipos de errores nuevos. Por ejemplo, a menudo dos o más subprocesos deben tener acceso al mismo recurso, pero únicamente un subproceso puede tener acceso al recurso sin ningún riesgo a la vez. Se necesita algún formulario de exclusión mutua para asegurarse de que únicamente uno subproceso está teniendo acceso al recurso a la vez. Si la exclusión mutua se realiza incorrectamente, puede crear una condición de *interbloqueo* en la que no se pueda ejecutar ningún subproceso. Los interbloqueos pueden ser un problema especialmente grave para realizar la depuración.

 Visual Studio proporciona una ventana **subprocesos** , una ventana subprocesos de GPU, una ventana Inspección paralela y otras características que facilitan la depuración multiproceso. La mejor manera de obtener información sobre las características de subprocesos es realizar los tutoriales. Vea [Tutorial: depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md) y [Tutorial: depurar una aplicación C++ amp](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Visual Studio también proporciona eficaces puntos de interrupción y puntos de seguimiento, que pueden resultar muy útiles para depurar aplicaciones multiproceso. Puede utilizar filtros de puntos de interrupción para colocar puntos de interrupción en subprocesos individuales. Vea [usar puntos de interrupción](../debugger/using-breakpoints.md)

 Depurar una aplicación multiproceso que tiene una interfaz de usuario puede resultar especialmente difícil. En ese caso, puede que considere ejecutar la aplicación en un segundo equipo y usar la depuración remota. Para obtener más información, vea [depuración remota](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>En esta sección
 [Depurar subprocesos y procesos](../debugger/debug-threads-and-processes.md) Explica los aspectos básicos de la depuración de subprocesos y procesos.

 [Depuración de varios procesos](../debugger/debug-multiple-processes.md) Explica cómo depurar varios procesos.

 [Cómo: usar la ventana subprocesos](../debugger/how-to-use-the-threads-window.md) Procedimientos útiles para depurar subprocesos con la ventana **subprocesos** .

 [Cómo: cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md) Tres formas de cambiar el contexto de depuración a otro subproceso.

 [Cómo: marcar y quitar marcadores de subprocesos](../debugger/how-to-flag-and-unflag-threads.md) Marque o marque los subprocesos a los que desea prestar atención especial durante la depuración.

 [Cómo: establecer un nombre de subproceso en código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md) Asigne un nombre al subproceso que vea en la ventana **subprocesos** .

 [Cómo: establecer un nombre de subproceso en código administrado](../debugger/how-to-set-a-thread-name-in-managed-code.md) Asigne un nombre al subproceso que vea en la ventana **subprocesos** .

 [Tutorial: depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Un paseo guiado por las características de depuración de subprocesos, con especial hincapié en los procedimientos de [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 [Cómo: depurar en un clúster de alto rendimiento](../debugger/how-to-debug-on-a-high-performance-cluster.md) Técnicas para depurar una aplicación que se ejecuta en un clúster de alto rendimiento.

 [Sugerencias para depurar subprocesos en código nativo](../debugger/tips-for-debugging-threads-in-native-code.md) Técnicas sencillas que pueden ser útiles para depurar subprocesos nativos.

 [Usar la ventana tareas](../debugger/using-the-tasks-window.md) Muestra una lista de todos los objetos de tarea administrados o nativos, incluido su estado y otra información útil.

 [Usar la ventana pilas paralelas](../debugger/using-the-parallel-stacks-window.md) Muestra las pilas de llamadas de varios subprocesos (o tareas) en una vista única y también combina los segmentos de pila que son comunes entre los subprocesos (o tareas).

 [Tutorial: depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md) Tutorial que muestra cómo usar las ventanas tareas paralelas y pilas paralelas.

 [Cómo: usar la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md) Inspeccione los valores y las expresiones entre varios subprocesos.

 [Cómo: usar la ventana subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md) Examine y trabaje con subprocesos que se ejecutan en la GPU durante la depuración.

## <a name="related-sections"></a>Secciones relacionadas

[Usar puntos de interrupción](../debugger/using-breakpoints.md)
- Use filtros de puntos de interrupción si desea colocar un punto de interrupción en un subproceso individual.

- Los puntos de seguimiento le habilitan para poder seguir paso a paso ejecución de su programa sin interrupciones. Esto puede ser útil para estudiar problemas como los interbloqueos.

  [Subprocesamiento](https://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) Conceptos de subprocesamiento en [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programación, incluido el código de ejemplo.

  [Subprocesamiento múltiple en componentes](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) Cómo usar multithreading en [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] componentes de.

  [Compatibilidad con multithreading para código anterior (Visual C++)](https://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) Conceptos de subprocesos y código de ejemplo para programadores de C++ mediante MFC.

## <a name="see-also"></a>Consulte también
 Depurar [subprocesos y procesos](../debugger/debug-threads-and-processes.md) [depuración remota](../debugger/remote-debugging.md)
