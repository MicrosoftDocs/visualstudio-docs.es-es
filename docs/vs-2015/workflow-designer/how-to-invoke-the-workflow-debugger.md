---
title: Filtrar Invocar el depurador de flujo de trabajo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9e607e3229225c2eeafe530ee685691b25f5ecfe
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998157"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Filtrar Invocar al depurador de flujo de trabajo
Generalmente, los flujos de trabajo se depuran de la misma manera que los programas escritos otros lenguajes de programación de Visual Studio. Puede iniciar el depurador de flujo de trabajo de las siguientes maneras:  
  
-   Seleccione **asociar al proceso** en el **depurar** menú para seleccionar el proceso de host para la instancia de flujo de trabajo. Este procedimiento es igual que el que se utiliza para adjuntar a un proceso de host en código administrado.  
  
-   Presione **F5** para iniciar la ejecución de una instancia del flujo de trabajo o continuar ejecutándose después de que se ha alcanzado un punto de interrupción.  
  
-   Usar depuración remota. Para obtener información sobre el uso de la depuración remota, vea [Cómo: Habilitar la depuración remota](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Si la aplicación de flujo de trabajo tiene como destino el x86 arquitectura y se hospeda en un equipo que ejecuta un sistema operativo de 64 bits, la depuración remota no funcionará a menos que [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] esté instalado en el equipo remoto o el destino de la aplicación de flujo de trabajo se cambia a **Cualquier CPU**.  
  
### <a name="stepping-through-code"></a>Ejecución paso a paso del código  
  
-   **El paso**: Puede entrar en una actividad usando **F11**. El depurador avanza paso a paso por todos los controladores definidos. Si no hay ningún controlador definido, puede ejecutar la actividad paso a paso o, en las actividades compuestas, que contienen otras actividades, puede entrar en la primera actividad en ejecución.  
  
-   **Paso para salir:** Puede salir paso a paso una actividad usando **MAYÚS + F11**. Al salir paso a paso de una actividad, se ejecutan hasta el final la actividad actual y todas sus actividades del mismo nivel. A continuación, el depurador se interrumpe en el elemento primario de la actividad actual. Al salir paso a paso de un controlador del código, el depurador se interrumpe en la actividad a la que está asociado el controlador.  
  
-   **Paso a paso**: Puede ejecutar paso a paso a través de una actividad usando **F10**. Al ejecutar paso a paso por procedimientos una actividad compuesta, el depurador se interrumpe en el primer elemento secundario ejecutable de la actividad compuesta. Al ejecutar paso a paso por procedimientos una actividad no compuesta, como <xref:System.Activities.Statements.Assign>, el depurador ejecuta la actividad y sus controladores asociados y se interrumpe en la actividad siguiente. Si la actividad que se ejecuta es la última actividad secundaria de una actividad compuesta, después de la ejecución el depurador se interrumpe en la actividad primaria.  
  
### <a name="debugging-with-f5"></a>Depurar con F5  
  
-   Si va a compilar un proyecto de aplicación de consola de flujos de trabajo, presione **F5** para comenzar la depuración en su aplicación y el flujo de trabajo. Si está compilando una biblioteca de actividades por sí sola, es preciso que disponga de una aplicación host ejecutable como proyecto de inicio. Para establecer un proyecto de inicio en **el Explorador de soluciones**, haga clic en el nombre del proyecto del host y seleccione **establecer como proyecto de inicio**.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Establecer puntos de interrupción en flujos de trabajo](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Depurar flujos de trabajo con el Diseñador de flujo de trabajo](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)