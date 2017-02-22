---
title: "Editor de condiciones de reglas (Cuadro de di&#225;logo) (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI"
helpviewer_keywords: 
  - "cuadro de diálogo Editor de condiciones de reglas"
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Editor de condiciones de reglas (Cuadro de di&#225;logo) (Heredado)
En este tema se describe el uso del cuadro de diálogo **Editor de condiciones de reglas** en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado.Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Puede crear y modificar las condiciones de reglas declarativas usando el cuadro de diálogo **Editor de condiciones de reglas**.Estas condiciones de reglas se exponen como propiedades en las actividades predefinidas de Windows Workflow Foundation:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
 Puede tener acceso al cuadro de diálogo **Editor de condiciones de reglas** utilizando el [Seleccionar condición \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
 En la tabla siguiente se describen los elementos de la interfaz de usuario \(IU\) del cuadro de diálogo **Editor de condiciones de reglas**.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------------------------------|-----------------|  
|**Condición:**|Escriba la expresión para la condición de la regla.|  
|**Aceptar**|Haga clic en esta opción para guardar la condición de la regla.|  
  
## Escribir expresiones de condiciones  
 Las expresiones de condiciones se escriben como texto.Puede escribir **this.** en el editor para hacer referencia a los campos, propiedades y métodos utilizados en el flujo de trabajo, mediante un menú tipo IntelliSense.También puede escribir directamente un nombre de miembro del flujo de trabajo.Puede agregar operadores lógicos a la condición, por ejemplo AND, OR y NOT.También puede agregar predicados.Un predicado es un operador binario y dos operandos.Los operadores binarios admitidos son **\=\=**, **\>**, **\<**, **\>\=** y **\<\=**.Los operandos admitidos son valor constante, función aritmética y miembros con ámbito público.  
  
 Puede especificar el tipo de la comparación y puede comparar con **null** o una cadena vacía.Puede anidar las llamadas a miembros en una variable que contenga un tipo complejo, por ejemplo, `this.Address.State == "WA"`.  
  
 El editor de condiciones de reglas admite los operadores siguientes:  
  
-   Operadores relacionales: \=\=, \=, \!\=  
  
-   Operaciones de comparación: \<, \<\=, \>, \>\=  
  
-   Operadores aritméticos: \+, \- , \*, \/, MOD  
  
-   Operadores lógicos: AND, &&, OR, &#124;&#124;, NOT, \!  
  
-   Operadores bit a bit: &, &#124;  
  
 La prioridad de los operadores de las expresiones sigue las reglas de prioridad de los operadores de C\#.  
  
 El editor de condiciones de reglas admite las expresiones numéricas siguientes:  
  
 este.i \=\= 1D \(se resuelve como 1.0\)  
  
 este.i \=\= 1E1 \(se resuelve como 10.0\)  
  
 este.i \=\= 1L \(se resuelve como Long\)  
  
 este.i \=\= 1M \(se resuelve como decimal\)  
  
 este.i \=\= 1F \(se resuelve como Single\)  
  
 este.i \=\= 1U \(se resuelve como unsigned int\)  
  
 Para obtener más información sobre las condiciones, vea [Usar condiciones en flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65009).  
  
## Vea también  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Seleccionar condición \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Uso de condiciones en flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Ayuda de la interfaz de usuario del diseñador heredado para Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)