---
title: Cuadro de diálogo Editor de condiciones de reglas (heredado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00df917b05f5073634b0956a0b44e5b0fc6026a6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846330"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Editor de condiciones de reglas (Cuadro de diálogo) (Heredado)
En este tema se describe cómo usar el cuadro de diálogo **Editor de condiciones de reglas** en el [!INCLUDE[wfd1](../includes/wfd1-md.md)]heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Puede crear y modificar condiciones de reglas declarativas mediante el cuadro de diálogo **Editor de condiciones de reglas** . Estas condiciones de reglas se exponen como propiedades en las actividades predefinidas de Windows Workflow Foundation:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

  Tiene acceso al cuadro de diálogo **Editor de condiciones de reglas** mediante el cuadro de [diálogo Seleccionar condición (heredado)](../workflow-designer/select-condition-dialog-box-legacy.md).

  En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **Editor de condiciones de reglas** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Condición:**|Escriba la expresión para la condición de la regla.|
|**ACEPTAR**|Haga clic en esta opción para guardar la condición de la regla.|

## <a name="entering-condition-expressions"></a>Escribir expresiones de condiciones
 Las expresiones de condiciones se escriben como texto. Puede escribir **esto.** en el editor para hacer referencia a campos, propiedades y métodos utilizados en el flujo de trabajo, mediante un menú similar a IntelliSense. También puede escribir directamente un nombre de miembro del flujo de trabajo. Puede agregar operadores lógicos a la condición, por ejemplo AND, OR y NOT. También puede agregar predicados. Un predicado es un operador binario y dos operandos. Los operadores binarios admitidos son **==** , **>** , **\<** , **>=** y **<=** . Los operandos admitidos son valor constante, función aritmética y miembros con ámbito público.

 Puede especificar el tipo para la comparación y puede compararlo con **null** o una cadena vacía. Puede anidar las llamadas a miembros en una variable que contenga un tipo complejo, por ejemplo, `this.Address.State == "WA"`.

 El editor de condiciones de reglas admite los operadores siguientes:

- Operadores relacionales: ==, =, !=

- Operadores de comparación: <, \<=, >, > =

- Operadores aritméticos: +, - , *, /, MOD

- Operadores lógicos: and, & & o, &#124; &#124;, not,!

- Operadores bit a bit: &,&#124;

  La prioridad de los operadores de las expresiones sigue las reglas de prioridad de los operadores de C#.

  El editor de condiciones de reglas admite las expresiones numéricas siguientes:

  este.i == 1D (se resuelve como 1.0)

  este.i == 1E1 (se resuelve como 10.0)

  este.i == 1L (se resuelve como Long)

  este.i == 1M (se resuelve como decimal)

  este.i == 1F (se resuelve como Single)

  este.i == 1U (se resuelve como unsigned int)

  Para obtener más información sobre las condiciones, vea [uso de condiciones en flujos de trabajo](https://msdn2.microsoft.com/library/bb628447.aspx).

## <a name="see-also"></a>Vea también
 [IfElseActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelseactivity.aspx) [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx) [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx) [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx) [cuadro de diálogo Seleccionar condición (heredado)](../workflow-designer/select-condition-dialog-box-legacy.md) [uso de condiciones en flujos de trabajo](https://msdn2.microsoft.com/library/bb628447.aspx) [Diseñador heredado para Windows Workflow Foundation ayuda de la interfaz de usuario](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)
