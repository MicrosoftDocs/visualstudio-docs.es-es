---
title: "C&#243;mo: Establecer puntos de interrupci&#243;n en los flujos de trabajo (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "puntos de interrupción, establecer en flujos de trabajo"
  - "depurar flujos de trabajo, establecer puntos de interrupción"
  - "depuración, establecer los puntos de interrupción en flujos de trabajo"
  - "flujos de trabajo, establecer puntos de interrupción"
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# C&#243;mo: Establecer puntos de interrupci&#243;n en los flujos de trabajo (Heredado)
En este tema se describe cómo establecer puntos de interrupción en aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] compiladas usando [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado.Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando la aplicación [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Cuando use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado de [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] para compilar una aplicación [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)], puede establecer puntos de interrupción en código C\# y Visual Basic de la misma manera que en Visual Studio.Como es de esperar, la ejecución del flujo de trabajo se detiene en cada punto de interrupción que se establece.  
  
 Un punto de interrupción tiene tres estados: *En espera*, *Enlazado* y *Error*.Cuando se establece un punto de interrupción, está En espera y se representa mediante un icono rojo vacío.Cuando el tiempo de ejecución ha cargado el tipo de flujo de trabajo, cambia a Enlazado y se representa mediante un icono rojo sólido.Si se especifica un formato incorrecto para el punto de interrupción, como con un nombre de actividad que no es válido, aparece una ventana de error.El punto de interrupción, de todas formas, se agrega a la ventana de punto de interrupción, pero se marca con una "x" pequeña.  
  
 Puede establecer puntos de interrupción en una actividad de la superficie de diseño de flujo de trabajo de las maneras siguientes:  
  
-   Haga clic con el botón secundario en la actividad y seleccione **Punto de interrupción** o **Insertar punto de interrupción**.  
  
-   Seleccione la actividad y presione F9.  
  
-   Seleccione **Nuevo punto de interrupción** en el menú **Depurar**.  
  
     También puede utilizar esta opción para establecer un nuevo punto de interrupción al depurar, si el depurador se detiene en un punto de interrupción.  
  
    > [!NOTE]
    >  No se pueden establecer puntos de interrupción en los flujos de trabajo invocados.  
  
### Para establecer un punto de interrupción utilizando la opción Nuevo punto de interrupción del menú Depurar  
  
1.  En el menú **Depurar**, seleccione **Nuevo punto de interrupción**.  
  
2.  Haga clic en **Interrumpir en función**.  
  
     Aparece el cuadro de diálogo **Nuevo punto de interrupción**.  
  
3.  Especifique el nombre de una actividad en el cuadro de texto **Función** utilizando esta sintaxis: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    >  Opcionalmente, en lugar de utilizar el nombre de actividad en el cuadro de texto **Función**, puede establecer un punto de interrupción especificando la ruta de acceso absoluta de la actividad de flujo de trabajo.Por ejemplo, suponga tiene una solución de flujo de trabajo denominada **WorkflowConsoleApplication1** y un flujo de trabajo en la solución denominado **Workflow1** que utiliza una actividad llamada **Delay1**.Puede utilizar el nombre de actividad **Delay1** o especificar la ruta de acceso como **Delay1:WorkflowConsoleApplication1 .Workflow1** o **Delay1:WorkflowConsoleApplication1.Workflow1:{6614886A\-608E\-412B\-BF98\-99FF1559DDDF}**.  
  
4.  Active la casilla **Usar IntelliSense para comprobar el nombre de la función**.  
  
     Si esta casilla no está activada, no se realiza ninguna comprobación de nombre de punto de interrupción.  
  
5.  Seleccione **Flujo de trabajo** en la lista **Lenguaje**.  
  
6.  Haga clic en **Aceptar**.  
  
## Vea también  
 [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)   
 [Invocar el Depurador de Microsoft Visual Studio para Windows Workflow Foundation \(Heredado\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)