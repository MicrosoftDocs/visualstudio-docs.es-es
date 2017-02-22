---
title: "Invocar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "depurador, flujo de trabajo"
  - "depurar flujos de trabajo, iniciar el depurador"
  - "depuración, usar el depurador del flujo de trabajo"
  - "Entrar (comando)"
  - "Paso a paso para salir (comando)"
  - "Paso a paso por procedimientos (comando)"
  - "ejecutar instrucciones paso a paso"
  - "ejecutar instrucciones paso a paso, comandos"
  - "depurador de flujos de trabajo, iniciar"
  - "flujos de trabajo, depurador"
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Invocar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation (Heredado)
En este tema se describe cómo usar el depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para depurar aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado.Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Generalmente, los flujos de trabajo heredados se depuran de la misma manera que los programas escritos en otros lenguajes de programación de Visual Studio.Puede iniciar el depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] for Windows Workflow Foundation de las formas siguientes:  
  
-   Seleccione **Asociar al proceso** en el menú **Depurar** para seleccionar una instancia de flujo de trabajo en ejecución entre los procesos disponibles.  
  
-   Presione **F5** para empezar a ejecutar una instancia del flujo de trabajo o continuar la ejecución una vez que se ha alcanzado un punto de interrupción.  
  
## Ejecución paso a paso del código  
 El depurador admite uno de los procedimientos de depuración más comunes, la ejecución paso a paso, es decir, la ejecución del código de línea en línea.Hay tres comandos para ejecutar el código paso a paso:  
  
-   **Entrar**: puede depurar paso a paso por instrucciones una actividad usando **F11**.El depurador avanza paso a paso por todos los controladores definidos.Si no hay ningún controlador definido, puede ejecutar la actividad paso a paso o, en las actividades compuestas, que contienen otras actividades, puede entrar en la primera actividad en ejecución.No se puede entrar en los controladores de código desde el diseñador en las actividades siguientes: **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup** o **ReplicatorActivity**.Para depurar los controladores asociados a estas actividades, debe colocar puntos de interrupción explícitos en el código.  
  
-   **Paso a paso para salir**: puede salir paso a paso de una actividad presionando **Shift\-F11**.Al salir paso a paso de una actividad, se ejecutan hasta el final la actividad actual y todas sus actividades del mismo nivel.A continuación, el depurador se interrumpe en el elemento primario de la actividad actual.Al salir paso a paso de un controlador del código, el depurador se interrumpe en la actividad a la que está asociado el controlador.  
  
-   **Paso a paso por procedimientos**: puede ejecutar paso a paso por procedimientos una actividad mediante **F10**.Al ejecutar paso a paso por procedimientos una actividad compuesta.las interrupciones del depurador en el primer elemento secundario ejecutable de la actividad compuesta.Al ejecutar paso a paso por procedimientos una actividad no compuesta, como **CodeActivity**, el depurador ejecuta la actividad y sus controladores asociados y se interrumpe en la actividad siguiente.Si la actividad que se ejecuta es la última actividad secundaria de una actividad compuesta, después de la ejecución el depurador se interrumpe en la actividad primaria.  
  
## Adjuntar a un proceso  
 Para depurar un flujo de trabajo adjuntando a un proceso, seleccione el proceso disponible en el cuadro de lista **Procesos disponibles** del cuadro de diálogo **Asociar al proceso**.Si no aparece **Automático: código de flujo de trabajo** no aparece en el cuadro de texto **Adjuntar a**, haga clic en **Seleccionar**.En el cuadro de diálogo **Seleccionar tipo de código**, haga clic en **Depurar estos tipos de código** y seleccione **Flujo de trabajo**.A continuación, haga clic en **Aceptar** y en **Adjuntar**.  
  
## Depurar con F5  
 Si una aplicación host de flujo de trabajo y una DLL de flujos de trabajo se encuentran en proyectos de Visual Studio diferentes, por ejemplo al usar una biblioteca de actividades de flujo de trabajo, debe establecer el proyecto DLL de flujos de trabajo como proyecto de inicio de la solución de Visual Studio para depurar el flujo de trabajo mediante **F5**.También debe establecer la ruta de acceso de la aplicación host en la propiedad **Programa externo de inicio** del proyecto DLL de flujos de trabajo.  
  
 Para establecer un proyecto de inicio en el Explorador de soluciones, haga clic con el botón secundario en el nombre del proyecto y seleccione **Establecer como proyecto de inicio**.Para establecer la ruta de acceso del host en la propiedad **Programa externo de inicio**, haga doble clic en el nodo **Propiedades** del proyecto de flujo de trabajo en el Explorador de soluciones y seleccione la pestaña **Depurar**.En **Acción de inicio**, seleccione **Programa externo de inicio** y escriba la ruta de acceso del archivo .exe host del flujo de trabajo que desea depurar.  
  
 Si la aplicación host se establece como proyecto de inicio, sólo se invoca el depurador de Visual Studio para depurar, y no se invoca el depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] for Windows Workflow Foundation.Si se utiliza el depurador de Visual Studio, sólo se alcanzan los puntos de interrupción del código de C\# o Visual Basic, pero no los puntos de interrupción establecidos en el diseñador de flujo de trabajo.Por ejemplo, se utiliza un punto de interrupción establecido en una actividad <xref:System.Workflow.Activities.ParallelActivity> en el diseñador si se utiliza el depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] for Windows Workflow Foundation, pero no si se utiliza el depurador de Visual Studio.  
  
## Vea también  
 [Cómo: Establecer puntos de interrupción en los flujos de trabajo \(Heredado\)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)