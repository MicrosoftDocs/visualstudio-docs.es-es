---
title: Modelos comunes para aplicaciones multiproceso con comportamiento deficiente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.tools.gallery
helpviewer_keywords: Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
ms.assetid: 00d10629-e20f-4d6d-8643-c59a3879812e
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 744e3031c94a3b152728000e7c5425f85fb9e9ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Modelos comunes para aplicaciones multiproceso con comportamiento deficiente
El visualizador de simultaneidad ayuda a los desarrolladores a visualizar el comportamiento de una aplicación multiproceso. Esta herramienta incluye una galería de modelos comunes para aplicaciones multiproceso que se comporten incorrectamente. La galería incluye patrones visuales típicos y reconocibles que se exponen a través de la herramienta, junto con una explicación del comportamiento que cada patrón representa, el resultado probable de ese comportamiento y el enfoque más común para resolverlo.  
  
## <a name="lock-contention-and-serialized-execution"></a>Contención de bloqueo y ejecución serializada  
 ![Contención de bloqueo cuyo resultado es una ejecución serializada](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")  
  
 A veces, una aplicación en paralelo continúa ejecutándose en serie repetidamente, aunque tenga varios subprocesos y el equipo tenga un número suficiente de núcleos lógicos. El primer síntoma es un bajo rendimiento multiproceso, incluso un poco más lento que una implementación en serie. En la vista Subprocesos, no se ven varios subprocesos que se ejecutan en paralelo; en su lugar, se ve un solo subproceso ejecutándose en cualquier momento. En este punto, si hace clic en un segmento de sincronización en un subproceso, puede ver una pila de llamadas para el subproceso bloqueado (pila de llamadas de bloqueo) y el subproceso que quitó la condición de bloqueo (pila de llamadas de desbloqueo). Además, si la pila de llamadas de desbloqueo se produce en el proceso que está analizando, se muestra un conector listo para subprocesos. A partir de aquí, puede navegar al código desde las pilas de llamadas de bloqueo y de desbloqueo para seguir investigando la causa de la serialización.  
  
 Como se muestra en la siguiente ilustración, el visualizador de simultaneidad también puede exponer este síntoma en la vista Uso de CPU, donde, a pesar de la presencia de varios subprocesos, la aplicación consume solo un núcleo lógico.  
  
 Para obtener más información, consulte "Patrón de rendimiento 1: identificar la contención de bloqueo" en el blog de Hazim Shafi [Herramientas de rendimiento en paralelo para Windows](http://go.microsoft.com/fwlink/?LinkID=160569) en el sitio web del blog de MSDN.  
  
 ![Contención de bloqueo](../profiling/media/lockcontention_2.png "LockContention_2")  
  
## <a name="uneven-workload-distribution"></a>Distribución de carga de trabajo desigual  
 ![Carga de trabajo desigual](../profiling/media/unevenworkload_1.png "UnevenWorkLoad_1")  
  
 Cuando se produce una distribución irregular de trabajo entre varios subprocesos paralelos en una aplicación, aparece un patrón de escalón típico a medida que cada subproceso completa su trabajo, como se muestra en la ilustración anterior. El visualizador de simultaneidad suele mostrar tiempos de inicio muy similares para cada subproceso simultáneo. Sin embargo, estos subprocesos normalmente finalizan de forma irregular, en lugar de finalizar simultáneamente. Este patrón indica una distribución irregular de trabajo entre un grupo de subprocesos paralelos, lo que puede provocar una disminución del rendimiento. El mejor enfoque para este problema es volver a evaluar el algoritmo utilizado para dividir el trabajo entre los subprocesos paralelos.  
  
 Como se muestra en la siguiente ilustración, el visualizador de simultaneidad también puede exponer este síntoma en la vista Uso de CPU como un descenso gradual del uso de CPU.  
  
 ![Carga de trabajo desigual](../profiling/media/unevenworkload_2.png "UnevenWorkLoad_2")  
  
## <a name="oversubscription"></a>Suscripción excesiva  
 ![Suscripción excesiva](../profiling/media/oversubscription.png "Oversubscription")  
  
 En el caso de la suscripción excesiva, el número de subprocesos activos en un proceso es mayor que el número de núcleos lógicos disponibles en el sistema. La ilustración anterior muestra los resultados de la suscripción excesiva, con bandas de adelantamiento significativas en todos los subprocesos activos. Además, la leyenda muestra que un gran porcentaje de tiempo se invierte en el adelantamiento (84 por ciento en este ejemplo). Esto puede indicar que el proceso está solicitando al sistema que ejecute más subprocesos simultáneos que el número de núcleos lógicos. Sin embargo, esto también puede indicar que otros procesos del sistema están usando recursos que se daba por hecho que estaban disponibles para este proceso.  
  
 Debe plantearse lo siguiente al evaluar este problema:  
  
-   El sistema global puede presentar una suscripción excesiva. Tenga en cuenta que otros procesos del sistema pueden estar adelantándose a los subprocesos. Al hacer una pausa sobre un segmento de adelantamiento en la vista Subprocesos, se muestra información sobre herramientas en que se identifican el subproceso y el proceso que adelantó el subproceso. Este proceso no es necesariamente el que se ejecutó durante todo el tiempo que el proceso se adelantó, pero proporciona una sugerencia sobre lo que creó la presión de adelantamiento sobre el proceso.  
  
-   Evalúe cómo el proceso determina el número apropiado de subprocesos para su ejecución durante esta fase de trabajo. Si el proceso calcula directamente el número de subprocesos paralelos activos, considere la posibilidad de modificar ese algoritmo para representar mejor el número de núcleos lógicos disponibles en el sistema. Si utiliza el Runtime de simultaneidad, la biblioteca TPL o PLINQ, estas bibliotecas se encargan de calcular el número de subprocesos.  
  
## <a name="inefficient-io"></a>E/S ineficaz  
 ![E/S ineficaz](../profiling/media/inefficient_io.png "Inefficient_IO")  
  
 El uso excesivo o indebido de E/S es una causa común de ineficacia de las aplicaciones. Piense en la ilustración anterior. El perfil de escala de tiempo visible muestra que E/S consume el 42 por ciento del tiempo de subproceso visible. La escala de tiempo muestra grandes cantidades de E/S, lo que indica que E/S suele bloquear la aplicación de la que se ha generado el perfil. Para ver detalles sobre los tipos de E/S y el punto en que el programa está bloqueado, haga zoom en las regiones problemáticas, examine el perfil de escala de tiempo visible y, a continuación, haga clic en un bloqueo de E/S concreto para ver las pilas de llamadas actuales.  
  
## <a name="lock-convoys"></a>Convoyes de bloqueo  
 ![Convoyes de bloqueo](../profiling/media/lock_convoys.png "Lock_Convoys")  
  
 Los convoyes de bloqueo se producen cuando la aplicación adquiere bloqueos por orden de llegada y cuando la tasa de llegada del bloqueo es mayor que la tasa de adquisición. La combinación de estas dos condiciones hace que las solicitudes del bloqueo inicien una copia de seguridad. Una forma de combatir este problema es usar bloqueos "no equitativos" o bloqueos que den acceso al primer subproceso que encuentren en estado desbloqueado. La ilustración anterior muestra este comportamiento del convoy. Para resolver el problema, intente reducir la contención de los objetos de sincronización y utilizar bloqueos no equitativos.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)