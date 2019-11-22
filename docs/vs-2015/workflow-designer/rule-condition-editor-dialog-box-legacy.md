---
title: Rule Condition Editor Dialog Box (Legacy) | Microsoft Docs
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
ms.openlocfilehash: a632b90e89e58c26ec72083fe3f4ed9223826dae
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302854"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Editor de condiciones de reglas (Cuadro de diálogo) (Heredado)
This topic describes how use the **Rule Condition Editor** dialog box in the legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 You create and modify declarative rule conditions by using the **Rule Condition Editor** dialog box. Estas condiciones de reglas se exponen como propiedades en las actividades predefinidas de Windows Workflow Foundation:

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

  You access the **Rule Condition Editor** dialog box by using the [Select Condition Dialog Box (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

  The following table describes the user interface (UI) elements of the **Rule Condition Editor** dialog box.

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Condition:**|Escriba la expresión para la condición de la regla.|
|**OK**|Haga clic en esta opción para guardar la condición de la regla.|

## <a name="entering-condition-expressions"></a>Escribir expresiones de condiciones
 Las expresiones de condiciones se escriben como texto. You can type **this.** into the editor to reference fields, properties, and methods used in the workflow, using an IntelliSense-like menu. También puede escribir directamente un nombre de miembro del flujo de trabajo. Puede agregar operadores lógicos a la condición, por ejemplo AND, OR y NOT. También puede agregar predicados. Un predicado es un operador binario y dos operandos. The binary operators supported are **==** , **>** , **\<** , **>=** , and **<=** . Los operandos admitidos son valor constante, función aritmética y miembros con ámbito público.

 You can specify the type for the comparison, and you can compare to **null** or an empty string. Puede anidar las llamadas a miembros en una variable que contenga un tipo complejo, por ejemplo, `this.Address.State == "WA"`.

 El editor de condiciones de reglas admite los operadores siguientes:

- Operadores relacionales: ==, =, !=

- Comparison operators: <, \<=, >, >=

- Operadores aritméticos: +, - , *, /, MOD

- Logical operators: AND, &&, OR, &#124;&#124;, NOT, !

- Bitwise operators: &, &#124;

  La prioridad de los operadores de las expresiones sigue las reglas de prioridad de los operadores de C#.

  El editor de condiciones de reglas admite las expresiones numéricas siguientes:

  este.i == 1D (se resuelve como 1.0)

  este.i == 1E1 (se resuelve como 10.0)

  este.i == 1L (se resuelve como Long)

  este.i == 1M (se resuelve como decimal)

  este.i == 1F (se resuelve como Single)

  este.i == 1U (se resuelve como unsigned int)

  For more information about conditions, see [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Vea también
 [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039) [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049) [Select Condition Dialog Box (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md) [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009) [Legacy Designer for Windows Workflow Foundation UI Help](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)