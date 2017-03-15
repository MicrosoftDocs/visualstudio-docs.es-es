---
title: "Depurar aplicaciones multiproceso en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.gputthreads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar [Visual Studio], cálculo de alto rendimiento"
  - "depurar [Visual Studio], con subprocesamiento múltiple"
  - "depuración de alto rendimiento"
  - "depuración multiproceso"
  - "subprocesamiento [Visual Studio], depurar"
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar aplicaciones multiproceso en Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un subproceso es una secuencia de instrucciones a la que el sistema operativo asigna tiempo de procesador.  Cada proceso que se ejecuta en el sistema operativo contiene al menos un subproceso.  Los procesos que tienen más de un subproceso se denominan multiproceso.  
  
 Equipos con varios procesadores, con varios núcleos o con tecnología hyperthreading pueden ejecutar varios subprocesos al mismo tiempo.  El procesamiento en paralelo de varios subprocesos puede mejorar notablemente el rendimiento del programa, pero también puede dificultar la depuración porque incluye la necesidad de efectuar el seguimiento de varios subprocesos.  
  
 Además, multithreading incluye algunos tipos de errores nuevos.  Por ejemplo, a menudo dos o más subprocesos deben tener acceso al mismo recurso, pero únicamente un subproceso puede tener acceso al recurso sin ningún riesgo a la vez.  Se necesita algún formulario de exclusión mutua para asegurarse de que únicamente uno subproceso está teniendo acceso al recurso a la vez.  Si se realiza la exclusión mutua incorrectamente, puede crear una condición *interbloqueo* donde ningún subproceso se puede ejecutar.  Los interbloqueos pueden ser un problema especialmente grave para realizar la depuración.  
  
 Visual Studio proporciona una ventana **Subprocesos**, una ventana de subprocesos de GPU, una ventana Inspección paralela y otras características que facilitan la depuración multiproceso. La mejor manera de obtener información sobre las características de subprocesos es realizar los tutoriales.  Consulte [Tutorial: Depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md) y [Tutorial: Depurar una aplicación de C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md).  
  
 Visual Studio también proporciona eficaces puntos de interrupción y puntos de seguimiento, que pueden resultar muy útiles para depurar aplicaciones multiproceso.  Puede utilizar filtros de puntos de interrupción para colocar puntos de interrupción en subprocesos individuales.  Consulte [Usar puntos de interrupción](../debugger/using-breakpoints.md)  
  
 Depurar una aplicación multiproceso que tiene una interfaz de usuario puede resultar especialmente difícil.  En ese caso, puede que considere ejecutar la aplicación en un segundo equipo y usar la depuración remota.  Para obtener más información, consulte [Depuración remota](../debugger/remote-debugging.md).  
  
## En esta sección  
 [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md)  
 Explica los fundamentos de la depuración de procesos y subprocesos.  
  
 [Depurar procesos](../debugger/debug-multiple-processes.md)  
 Explica cómo depurar varios procesos.  
  
 [Cómo: Utilizar la ventana Subprocesos](../debugger/how-to-use-the-threads-window.md)  
 Procedimientos útiles para depurar subprocesos con la ventana **Subprocesos**.  
  
 [Cómo: Cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Tres maneras de modificar el contexto de depuración a otro subproceso.  
  
 [Cómo: Marcar y quitar marcadores de subprocesos](../debugger/how-to-flag-and-unflag-threads.md)  
 Marque los subprocesos a los que desea prestar especial atención mientras se realiza la depuración.  
  
 [Cómo: Establecer un nombre de subproceso en código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Asigne al subproceso uno de los nombres que aparecen en la ventana **Subprocesos**.  
  
 [Cómo: Establecer un nombre de subproceso en código administrado](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Asigne al subproceso uno de los nombres que aparecen en la ventana **Subprocesos**.  
  
 [Tutorial: Depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md)  
 Un paseo guiado por las características de depuración de subprocesos, con especial hincapié en los procedimientos de [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 [Cómo: Depurar en un clúster de alto rendimiento](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Técnicas para depurar una aplicación que se ejecuta en un clúster de alto rendimiento.  
  
 [Sugerencias para depurar subprocesos en código nativo](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Técnicas simples que pueden ser útiles para depurar los subprocesos nativos.  
  
 [Usar la ventana Tareas](../debugger/using-the-tasks-window.md)  
 Muestra una lista de todos los objetos de tarea administrados o nativos que incluye su estado y otra información útil.  
  
 [Uso de la ventana Tareas paralelas](../debugger/using-the-parallel-stacks-window.md)  
 Muestra pilas de llamadas de varios subprocesos \(o tareas\) en una vista única y también combina segmentos de pila que son comunes entre los subprocesos \(o tareas\).  
  
 [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Tutorial que muestra cómo utilizar ventanas de tareas y pilas paralelas.  
  
 [Cómo: Utilizar la Ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)  
 Examinar los valores y las expresiones entre varios subprocesos.  
  
 [Cómo: Utilizar la ventana Subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
 Examinar y trabajar con subprocesos que se ejecutan en la GPU durante la depuración.  
  
## Secciones relacionadas  
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)  
 -   Use filtros de puntos de interrupción si desea colocar un punto de interrupción en un subproceso individual.  
  
-   Los puntos de seguimiento le habilitan para poder seguir paso a paso ejecución de su programa sin interrupciones.  Esto puede ser útil para estudiar problemas como los interbloqueos.  
  
 [Threading](../Topic/Managed%20Threading.md)  
 Conceptos relacionados con el subprocesamiento en programación de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], incluido el código de ejemplo.  
  
 [Multithreading in Components](../Topic/Multithreading%20in%20Components.md)  
 Cómo usar multithreading en componentes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Compatibilidad del código antiguo con multithreading \(Visual C\+\+\)](/visual-cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 Conceptos relacionados con el subprocesamiento para programadores de C\+\+ mediante MFC.  
  
## Vea también  
 [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md)   
 [Depuración remota](../debugger/remote-debugging.md)