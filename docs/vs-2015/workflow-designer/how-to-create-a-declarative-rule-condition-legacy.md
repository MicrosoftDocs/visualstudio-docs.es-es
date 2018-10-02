---
title: 'Cómo: crear una condición de regla declarativa (heredado) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 59eebe93b5c11fa1b02dc9ae481d0658010e961b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574951"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Cómo: Crear una condición de regla declarativa (Heredado)
En este tema se describe cómo declarar una condición de regla usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Una declaración de condición se evalúa como **True** o **False**. Una condición de regla declarativa es una instrucción de condición que se crea mediante la [cuadro de diálogo de Editor de condición de regla (heredado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) y almacenados como XML con el flujo de trabajo. Puede incluir predicados que comparan el estado del flujo de trabajo y álgebra booleana que combina varios predicados.  
  
 Las condiciones de regla declarativa se utilizan en las siguientes actividades predefinidas de Windows Workflow Foundation:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Para crear una condición de regla declarativa mediante el Editor de condiciones de reglas  
  
1.  En la actividad **propiedades** ventana, haga clic en el **condición** propiedad o **UntilCondition** propiedad, dependiendo de la actividad.  
  
2.  Seleccione **condición de regla declarativa** en la lista para la propiedad.  
  
3.  Expanda el **condición** o **UntilCondition** propiedad.  
  
4.  Haga clic en el **ConditionName** propiedad.  
  
5.  Haga clic en el **ConditionName** elipses **[...]**  para abrir el **Seleccionar condición** cuadro de diálogo.  
  
6.  Haga clic en **nueva condición** para abrir el **Editor de condiciones de regla** cuadro de diálogo.  
  
7.  Escriba la expresión para la condición en la **condición** cuadro de texto.  
  
     Para obtener información sobre cómo crear expresiones de condiciones, consulte [cuadro de diálogo de Editor de condición de regla (heredado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Cuando haya terminado de crear la expresión de condición, haga clic en **Aceptar** para cerrar el cuadro de diálogo y crear la condición de regla con un nombre asignado.  
  
     El **Seleccionar condición** abre el cuadro de diálogo.  
  
     Para obtener información sobre cómo usar el **Seleccionar condición** cuadro de diálogo, vea [seleccione el cuadro de diálogo de condición (heredado)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>Vea también  
 [Actividades de flujo de trabajo heredado](../workflow-designer/legacy-workflow-activities.md)   
 [Uso de ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Usar la actividad IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Uso de la actividad Replicator](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Usar While actividad](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Cuadro de diálogo Editor de condiciones de regla (heredado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Cuadro de diálogo Seleccionar condición (heredado)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Uso de condiciones en flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65009)