---
title: Rule Set Editor Dialog Box (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83cdd4f549655be524abdd2a4708b316f6747b3e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302760"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Editor de conjunto de reglas (Cuadro de diálogo) (Heredado)
This topic describes how use the **Rule Set Editor** dialog box in the legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 The **Rule Set Editor** dialog box is used to create and modify [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) rule sets, which are serialized to a .rules file.

> [!NOTE]
> If you want to open the .rules file with the **XML Editor with encoding**, you must first close the associated designer window for the workflow or activity.

 For information about how to access the **Rule Set Editor** dialog box, see [How to: Create a PolicyActivity Rule Set (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> El editor de reglas del [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado que se usa para tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] no es compatible con múltiples versiones.

 The following table describes the user interface (UI) elements of the **Rule Set Editor** dialog box.

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Add Rule**|Agrega una definición de regla al conjunto de reglas.|
|**Eliminar**|Elimina la regla seleccionada del conjunto de reglas.|
|**Chaining**|Especifica qué tipo de encadenamiento hacia delante se debe utilizar con el conjunto de reglas. Las opciones disponibles son:<br /><br /> -   **Full Chaining**, which specifies to use all forward chaining mechanisms: implicit, method attributing, and explicit using an **Update** function.<br />-   **Sequential**, which specifies not to use any forward chaining.<br />-   **Explicit Update Only**, which specifies to only perform forward chaining on **Update** actions.<br /><br /> For more information about forward chaining, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).|
|**Nombre**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por nombre.|
|**Priority**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por prioridad.|
|**Reevaluation**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por tipo de reevaluación.|
|**Rule Preview**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por la vista previa de la condición y las acciones de una regla.|
|**Name:**|Se usa para escribir el nombre de la regla.|
|**Priority:**|Escriba una prioridad para la regla. La prioridad predeterminada es 0.|
|**Reevaluation:**|Especifica qué tipo de reevaluación de regla se debe utilizar con la regla. Las opciones disponibles son:<br /><br /> -   **Always**, which causes the rule to be reevaluated as needed.<br />-   **Never**, which causes the rule to never be reevaluated. En este caso una regla se ejecuta sólo una vez.|
|**Active**|Se selecciona para hacer que la regla esté activa.|
|**Condition:**|Escriba una expresión para la condición de la regla. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|
|**Then Actions:**|Escriba una expresión para las acciones Then. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|
|**Else Actions:**|Escriba una expresión para las acciones Else. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|
|**OK**|Haga clic en Aceptar para guardar el conjunto de reglas en un archivo .rules.|

 For more information about rule sets, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>Escribir expresiones de condiciones y de acciones
 You enter expressions for the Condition and the Then and Else actions as text in their respective text boxes in the **Rule Set Editor** dialog box. You can type **this.** into the editor to reference fields, properties and methods used in the workflow, using an IntelliSense-type of menu. También puede escribir directamente un nombre de miembro del flujo de trabajo. Puede llamar a métodos estáticos en tipos a los que se hace referencia escribiendo el nombre de la clase seguido por el nombre del método.

 Puede agregar operadores lógicos a la condición, por ejemplo AND, OR y NOT. También puede agregar predicados. Un predicado es un operador binario y dos operandos. The binary operators supported are ==, >, \<, >=, and <=. Los operandos admitidos son valor constante, función aritmética y miembros con ámbito público.

 You can specify the type for the comparison, and you can compare to **null** or an empty string. Puede anidar las llamadas a miembros en una variable que contenga un tipo complejo, por ejemplo, `this.Address.State == "WA"`.

 Las expresiones admiten los operadores siguientes:

- Operadores relacionales: ==, =, !=

- Comparison operators: <, \<=, >, >=

- Operadores aritméticos: +, - , *, /, MOD

- Logical operators: AND, &&, OR, &#124;&#124;, NOT, !

- Bitwise operators: &, &#124;

  La prioridad de los operadores de las expresiones sigue las reglas de prioridad de los operadores de C#.

  For more information about conditions, see [Using Conditions in Workflows](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Funciones Halt y Update
 **Then Actions:** and **Else Actions:** expressions support **Halt** and **Update** functions. To use the **Halt** function, type **Halt** into a **Then Action:** or **Else Action:** text box. The **Halt** action causes rule set execution to stop immediately, and control returns to the calling code. You use the **Update** function with forward chaining.

 An **Update** statement can be expressed in the editor in one of two forms; both forms are shown in the following example:

```
Update(this.Address.State)
Update("this/Address/State")
```

 For more information about using **Update** with forward chaining, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>Vea también
 [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004) [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009)