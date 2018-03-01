---
title: "Cómo: Elegir eventos de muestreo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8475544d6ecb822a25a423b73543d7364d79da10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-sampling-events"></a>Cómo: Elegir eventos de muestreo
De forma predeterminada, las herramientas de generación de perfiles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] recopilan datos de rendimiento en un intervalo especificado como un número de ciclos de procesador que utiliza el proceso del que se genera el perfil. El número predeterminado de ciclos en un intervalo es de 10 000 000, que es aproximadamente 0,01 segundos en un equipo de 1 GH. Puede cambiar el número de ciclos en un intervalo, así como el evento de muestras. Los siguientes eventos de muestras están disponibles:  
  
-   Ciclos de reloj: para problemas relacionados con la CPU.  
  
-   Errores de página: para problemas relacionados con la memoria.  
  
-   Llamadas del sistema: para problemas relacionados con E/S.  
  
-   Contador de rendimiento: contadores de CPU para problemas de rendimiento de bajo nivel.  
  
> [!IMPORTANT]
>  Si recopila datos de memoria de .NET (asignaciones, duraciones de objeto o ambos) mediante el método de muestreo, se omiten todos los eventos de muestreo especificados por el usuario y se utilizan los eventos de asignación de memoria o de recolección de elementos no utilizados apropiados, o ambos, para recopilar datos.  
  
### <a name="to-select-a-sample-event"></a>Para seleccionar un evento de muestras  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2.  En las **Páginas de propiedades**, haga clic en las propiedades de **Muestreo** .  
  
3.  En la lista desplegable **Evento de muestras**, seleccione el evento de muestras que quiere utilizar para generar perfiles de la aplicación.  
  
    > [!NOTE]
    >  Los **Contadores de rendimiento disponibles** solo están habilitados si selecciona **Contador de rendimiento** en la lista desplegable **Evento de muestras**.  
  
4.  Si selecciona **Contador de rendimiento**, seleccione un contador de CPU específico en el control de vista de árbol **Contadores de rendimiento disponibles**.  
  
    -   Los contadores en el nodo **Eventos portátiles** están disponibles en todos los tipos de procesadores.  
  
    -   Los contadores en el nodo **Eventos de plataforma** son específicos del procesador en el equipo actual y podrían no estar disponibles en otros tipos de procesadores.  
  
5.  Al seleccionar un evento de muestras, el valor del intervalo de muestreo predeterminado se muestra en el cuadro de texto **Intervalo de muestreo**. Si es necesario, puede escribir el valor que quiera en el cuadro de texto.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Cómo: Elegir métodos de colección](../profiling/how-to-choose-collection-methods.md)   
 [Contadores de CPU y de Windows](../profiling/cpu-and-windows-counters.md)   
 [Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)   
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)