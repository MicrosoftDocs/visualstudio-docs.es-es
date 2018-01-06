---
title: "Cuadro de diálogo de Editor de condiciones de regla (heredado) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords: Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: a4f38bed7fc164fd5283b98afe780bc81a6a7265
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Editor de condiciones de reglas (Cuadro de diálogo) (Heredado)
Este tema se describe cómo utilizar el **Editor de condiciones de regla** cuadro de diálogo heredado [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Crear y modificar las condiciones de regla declarativa mediante la **Editor de condiciones de regla** cuadro de diálogo. Estas condiciones de reglas se exponen como propiedades en las actividades predefinidas de Windows Workflow Foundation:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
 Tiene acceso a la **Editor de condiciones de regla** cuadro de diálogo mediante el uso de la [seleccione el cuadro de diálogo de condición (heredado)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
 La tabla siguiente describen los elementos de interfaz de usuario de la **Editor de condiciones de regla** cuadro de diálogo.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------|-----------------|  
|**Condición:**|Escriba la expresión para la condición de la regla.|  
|**VALE**|Haga clic en esta opción para guardar la condición de la regla.|  
  
## <a name="entering-condition-expressions"></a>Escribir expresiones de condiciones  
 Las expresiones de condiciones se escriben como texto. Puede escribir **esto.** en el editor para hacer referencia a campos, propiedades y métodos que se utilizan en el flujo de trabajo, mediante un menú de IntelliSense. También puede escribir directamente un nombre de miembro del flujo de trabajo. Puede agregar operadores lógicos a la condición, por ejemplo AND, OR y NOT. También puede agregar predicados. Un predicado es un operador binario y dos operandos. Los operadores binarios admitidos son  **==** ,  **>** ,  **\<** ,  **>=** , y  **<=** . Los operandos admitidos son valor constante, función aritmética y miembros con ámbito público.  
  
 Puede especificar el tipo de la comparación y puede comparar con **null** o una cadena vacía. Puede anidar las llamadas a miembros en una variable que contenga un tipo complejo, por ejemplo, `this.Address.State == "WA"`.  
  
 El editor de condiciones de reglas admite los operadores siguientes:  
  
-   Operadores relacionales: ==, =, !=  
  
-   Operadores de comparación: <, \<=, >, > =  
  
-   Operadores aritméticos: +, - , *, /, MOD  
  
-   Operadores lógicos: Y, & &, OR, &#124; &#124; no es así,!  
  
-   Operadores bit a bit: &, &#124;  
  
 La prioridad de los operadores de las expresiones sigue las reglas de prioridad de los operadores de C#.  
  
 El editor de condiciones de reglas admite las expresiones numéricas siguientes:  
  
 este.i == 1D (se resuelve como 1.0)  
  
 este.i == 1E1 (se resuelve como 10.0)  
  
 este.i == 1L (se resuelve como Long)  
  
 este.i == 1M (se resuelve como decimal)  
  
 este.i == 1F (se resuelve como Single)  
  
 este.i == 1U (se resuelve como unsigned int)  
  
 Para obtener más información acerca de las condiciones, consulte [uso de condiciones en flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65009).  
  
## <a name="see-also"></a>Vea también  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Seleccione el cuadro de diálogo de condición (heredado)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Usar condiciones en flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Ayuda de la interfaz de usuario del diseñador heredado para Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)