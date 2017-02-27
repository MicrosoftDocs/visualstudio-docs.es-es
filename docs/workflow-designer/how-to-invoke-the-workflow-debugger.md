---
title: "Invocar el depurador de flujo de trabajo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Invocar el depurador de flujo de trabajo
Generalmente, los flujos de trabajo se depuran de la misma manera que los programas escritos en otros lenguajes de programación de Visual Studio.Puede iniciar el depurador de flujo de trabajo de las siguientes maneras:  
  
-   Seleccione **Asociar al proceso** en el menú **Depurar** para seleccionar el proceso de host para la instancia de flujo de trabajo.Este procedimiento es igual que el que se utiliza para adjuntar a un proceso de host en código administrado.  
  
-   Presione **F5** para empezar a ejecutar una instancia del flujo de trabajo o continuar la ejecución una vez que se ha alcanzado un punto de interrupción.  
  
-   Usar depuración remota.Para obtener información sobre cómo usar la depuración remota, vea [Cómo: Habilitar la depuración remota](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Si la aplicación de flujo de trabajo tiene como destino la arquitectura x86 y se hospeda en un equipo que ejecuta un sistema operativo de 64 bits, la depuración remota no funcionará a menos que [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] esté instalado en el equipo remoto o el destino de la aplicación de flujo de trabajo se cambie a **Cualquier CPU**.  
  
### Ejecución paso a paso del código  
  
-   **Entrar**: puede depurar paso a paso por instrucciones una actividad usando **F11**.El depurador avanza paso a paso por todos los controladores definidos.Si no hay ningún controlador definido, puede ejecutar la actividad paso a paso o, en las actividades compuestas, que contienen otras actividades, puede entrar en la primera actividad en ejecución.  
  
-   **Paso a paso para salir:** puede salir paso a paso de una actividad si presiona **Mayús \+ F11**.Al salir paso a paso de una actividad, se ejecutan hasta el final la actividad actual y todas sus actividades del mismo nivel.A continuación, el depurador se interrumpe en el elemento primario de la actividad actual.Al salir paso a paso de un controlador del código, el depurador se interrumpe en la actividad a la que está asociado el controlador.  
  
-   **Paso a paso por procedimientos**: puede ejecutar paso a paso por procedimientos una actividad utilizando **F10**.Al ejecutar paso a paso por procedimientos una actividad compuesta, el depurador se interrumpe en el primer elemento secundario ejecutable de la actividad compuesta.Al ejecutar paso a paso por procedimientos una actividad no compuesta, como <xref:System.Activities.Statements.Assign>, el depurador ejecuta la actividad y sus controladores asociados y se interrumpe en la actividad siguiente.Si la actividad que se ejecuta es la última actividad secundaria de una actividad compuesta, después de la ejecución el depurador se interrumpe en la actividad primaria.  
  
### Depurar con F5  
  
-   Si está compilando un proyecto de Aplicación de consola de flujos de trabajo, bastará con que presione **F5** para empezar a depurar en su aplicación y flujo de trabajo.Si está compilando una biblioteca de actividades por sí sola, es preciso que disponga de una aplicación host ejecutable como proyecto de inicio.Para establecer un proyecto de inicio en el **Explorador de soluciones**, haga clic con el botón secundario en el nombre de proyecto del host y seleccione **Establecer como proyecto de inicio**.  
  
## Vea también  
 [Establecer puntos de interrupción en los flujos de trabajo](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)   
 [Depurar flujos de trabajo con el Diseñador de flujo de trabajo](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)