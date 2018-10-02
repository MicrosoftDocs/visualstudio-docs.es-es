---
title: Depurar aplicaciones multiproceso en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff0030baec409ae54dc5ebb219f5419e583a0efd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580039"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicaciones multiproceso en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [depurar aplicaciones multiproceso en Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debug-multithreaded-applications-in-visual-studio).  
  
Un subproceso es una secuencia de instrucciones a la que el sistema operativo asigna tiempo de procesador. Cada proceso que se ejecuta en el sistema operativo contiene al menos un subproceso. Los procesos que tienen más de un subproceso se denominan multiproceso.  
  
 Equipos con varios procesadores, con varios núcleos o con tecnología hyperthreading pueden ejecutar varios subprocesos al mismo tiempo. El procesamiento en paralelo de varios subprocesos puede mejorar notablemente el rendimiento del programa, pero también puede dificultar la depuración porque incluye la necesidad de efectuar el seguimiento de varios subprocesos.  
  
 Además, multithreading incluye algunos tipos de errores nuevos. Por ejemplo, a menudo dos o más subprocesos deben tener acceso al mismo recurso, pero únicamente un subproceso puede tener acceso al recurso sin ningún riesgo a la vez. Se necesita algún formulario de exclusión mutua para asegurarse de que únicamente uno subproceso está teniendo acceso al recurso a la vez. Si la exclusión mutua se realiza correctamente, puede crear un *interbloqueo* condición donde ningún subproceso puede ejecutar. Los interbloqueos pueden ser un problema especialmente grave para realizar la depuración.  
  
 Visual Studio proporciona un **subprocesos** ventana, una ventana de subprocesos de GPU, una ventana Inspección paralela y otras características que facilitan la depuración multiproceso. La mejor manera de obtener información sobre las características de subprocesos es realizar los tutoriales. Consulte [Tutorial: depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md) y [Tutorial: depurar una aplicación de C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).  
  
 Visual Studio también proporciona eficaces puntos de interrupción y puntos de seguimiento, que pueden resultar muy útiles para depurar aplicaciones multiproceso. Puede utilizar filtros de puntos de interrupción para colocar puntos de interrupción en subprocesos individuales. Consulte [usar puntos de interrupción](../debugger/using-breakpoints.md)  
  
 Depurar una aplicación multiproceso que tiene una interfaz de usuario puede resultar especialmente difícil. En ese caso, puede que considere ejecutar la aplicación en un segundo equipo y usar la depuración remota. Para obtener información, consulte [depuración remota](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md)  
 Explica los fundamentos de la depuración de procesos y subprocesos.  
  
 [Depurar varios procesos](../debugger/debug-multiple-processes.md)  
 Explica cómo depurar varios procesos.  
  
 [Cómo: Usar la ventana Subprocesos](../debugger/how-to-use-the-threads-window.md)  
 Procedimientos útiles para depurar subprocesos con el **subprocesos** ventana.  
  
 [Cómo: Cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Tres maneras de modificar el contexto de depuración a otro subproceso.  
  
 [Cómo: Marcar y desmarcar subprocesos](../debugger/how-to-flag-and-unflag-threads.md)  
 Marque los subprocesos a los que desea prestar especial atención mientras se realiza la depuración.  
  
 [Cómo: Establecer un nombre de subproceso en código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Asigne al subproceso de un nombre que se ve en el **subprocesos** ventana.  
  
 [Cómo: Establecer un nombre de subproceso en código administrado](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Asigne al subproceso de un nombre que se ve en el **subprocesos** ventana.  
  
 [Tutorial: Depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md).  
 Un paseo guiado por las características de depuración de subprocesos, con especial hincapié en los procedimientos de [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].  
  
 [Cómo: Depurar en un clúster de alto rendimiento](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Técnicas para depurar una aplicación que se ejecuta en un clúster de alto rendimiento.  
  
 [Sugerencias para depurar subprocesos en código nativo](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Técnicas simples que pueden ser útiles para depurar los subprocesos nativos.  
  
 [Usar la ventana Tareas](../debugger/using-the-tasks-window.md)  
 Muestra una lista de todos los objetos de tarea administrados o nativos que incluye su estado y otra información útil.  
  
 [Uso de la ventana Pilas paralelas](../debugger/using-the-parallel-stacks-window.md)  
 Muestra pilas de llamadas de varios subprocesos (o tareas) en una vista única y también combina segmentos de pila que son comunes entre los subprocesos (o tareas).  
  
 [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Tutorial que muestra cómo utilizar ventanas de tareas y pilas paralelas.  
  
 [Cómo: Usar la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)  
 Examinar los valores y las expresiones entre varios subprocesos.  
  
 [Cómo: Usar la ventana Subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
 Examinar y trabajar con subprocesos que se ejecutan en la GPU durante la depuración.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)  
 -   Use filtros de puntos de interrupción si desea colocar un punto de interrupción en un subproceso individual.  
  
-   Los puntos de seguimiento le habilitan para poder seguir paso a paso ejecución de su programa sin interrupciones. Esto puede ser útil para estudiar problemas como los interbloqueos.  
  
 [Subprocesamiento](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87)  
 Conceptos relacionados con el subprocesamiento en programación de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], incluido el código de ejemplo.  
  
 [Subprocesamiento múltiple en componentes](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 Cómo usar multithreading en componentes de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 [Compatibilidad del código antiguo con multithreading (Visual C++)](http://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c)  
 Conceptos relacionados con el subprocesamiento para programadores de C++ mediante MFC.  
  
## <a name="see-also"></a>Vea también  
 [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md)   
 [Depuración remota](../debugger/remote-debugging.md)



