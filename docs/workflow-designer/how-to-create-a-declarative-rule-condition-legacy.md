---
title: "C&#243;mo: Crear una condici&#243;n de regla declarativa (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "instrucciones condicionales, condiciones de reglas declarativas"
  - "condiciones de reglas declarativas"
  - "cuadro de diálogo Editor de condiciones de reglas"
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# C&#243;mo: Crear una condici&#243;n de regla declarativa (Heredado)
En este tema se describe cómo declarar una condición de regla usando [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Una instrucción condicional se evalúa como **True** o **False**.Una condición de regla declarativa es una instrucción condicional que se crea usando el [Editor de condiciones de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) y se almacena como XML con el flujo de trabajo.Puede incluir predicados que comparan el estado del flujo de trabajo y álgebra booleana que combina varios predicados.  
  
 Las condiciones de regla declarativa se utilizan en las siguientes actividades predefinidas de Windows Workflow Foundation:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### Para crear una condición de regla declarativa mediante el Editor de condiciones de reglas  
  
1.  En la ventana **Propiedades** de la actividad, haga clic en la propiedad **Condition** o la propiedad **UntilCondition**, dependiendo de la actividad.  
  
2.  Seleccione **Condición de regla declarativa** en la lista de la propiedad.  
  
3.  Expanda la propiedad **Condition** o **UntilCondition**.  
  
4.  Haga clic en la propiedad **ConditionName**.  
  
5.  Haga clic en los puntos suspensivos **\[...\]** de **ConditionName** para abrir el cuadro de diálogo **Seleccionar condición**.  
  
6.  Haga clic en **Nueva condición** para abrir el cuadro de diálogo **Editor de condiciones de reglas**.  
  
7.  Escriba la expresión de la condición en el cuadro de texto **Condición**.  
  
     Para obtener información sobre cómo crear expresiones de condiciones, vea [Editor de condiciones de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Cuando termine de crear la expresión de condición, haga clic en **Aceptar** para cerrar el cuadro de diálogo y crear la condición de la regla con un nombre asignado.  
  
     Se abre el cuadro de diálogo **Seleccionar condición**.  
  
     Para obtener información sobre cómo usar el cuadro de diálogo **Seleccionar condición**, vea [Seleccionar condición \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## Vea también  
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)   
 [Uso de ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Uso de la actividad IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Uso de la actividad Replicator](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Uso de la actividad While](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Editor de condiciones de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Seleccionar condición \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Uso de condiciones en flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65009)