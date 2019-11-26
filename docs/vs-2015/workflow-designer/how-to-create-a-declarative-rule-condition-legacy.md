---
title: 'Cómo: crear una condición de regla declarativa (heredada) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2dc63fc58b22792e566df91bd86cac40e3fd2e65
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297489"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Cómo: Crear una condición de regla declarativa (Heredado)
En este tema se describe cómo declarar una condición de regla usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Una instrucción de condición se evalúa como **true** o **false**. Una condición de regla declarativa es una instrucción de condición que se crea mediante el [cuadro de diálogo Editor de condiciones de reglas (heredado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) y se almacena como XML con el flujo de trabajo. Puede incluir predicados que comparan el estado del flujo de trabajo y álgebra booleana que combina varios predicados.

 Las condiciones de regla declarativa se utilizan en las siguientes actividades predefinidas de Windows Workflow Foundation:

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Para crear una condición de regla declarativa mediante el Editor de condiciones de reglas

1. En la ventana **propiedades** de la actividad, haga clic en la propiedad **condición** o en la propiedad **UntilCondition** , dependiendo de la actividad.

2. Seleccione **condición de regla declarativa** en la lista para la propiedad.

3. Expanda la **condición** o la propiedad **UntilCondition** .

4. Haga clic en la propiedad **ConditionName** .

5. Haga clic en los puntos suspensivos de **ConditionName** **[...]** para abrir el cuadro de diálogo **seleccionar condición** .

6. Haga clic en **nueva condición** para abrir el cuadro de diálogo **Editor de condiciones de reglas** .

7. Escriba la expresión de la condición en el cuadro de texto **condición** .

     Para obtener información sobre cómo crear expresiones de condición, vea [cuadro de diálogo Editor de condiciones de reglas (heredado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Cuando haya terminado de crear la expresión de condición, haga clic en **Aceptar** para cerrar el cuadro de diálogo y crear la condición de regla con un nombre asignado.

     Se abre el cuadro de diálogo **seleccionar condición** .

     Para obtener información sobre cómo usar el cuadro de diálogo **seleccionar condición** , vea [seleccionar condición (cuadro de diálogo) (heredado)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Vea también
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md) [usar el ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65066) [mediante la actividad IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65075) [usar la actividad de replicador](https://go.microsoft.com/fwlink?LinkID=65080) [mediante el](https://go.microsoft.com/fwlink?LinkID=65091) cuadro de [diálogo Editor de condiciones de reglas de actividad (heredado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) cuadro de diálogo [seleccionar condición (heredado](../workflow-designer/select-condition-dialog-box-legacy.md) ) [uso de condiciones en flujos de trabajo](https://go.microsoft.com/fwlink?LinkID=65009)