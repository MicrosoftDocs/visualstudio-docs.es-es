---
title: Cuadro de diálogo Editor de conjunto de reglas (heredado) | Microsoft Docs
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
ms.openlocfilehash: 8010bbbc38dee980ebe89dc60ccb513379103a26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846314"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Editor de conjunto de reglas (Cuadro de diálogo) (Heredado)
En este tema se describe cómo usar el cuadro de diálogo **Editor de conjunto de reglas** en heredado [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 El cuadro de diálogo **Editor de conjunto de reglas** se usa para crear y modificar conjuntos de reglas de [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) , que se serializan en un archivo. rules.

> [!NOTE]
> Si desea abrir el archivo. rules con el **Editor XML con codificación**, primero debe cerrar la ventana del diseñador asociada para el flujo de trabajo o la actividad.

 Para obtener información sobre cómo tener acceso al cuadro de diálogo **Editor de conjunto de reglas** , consulte [Cómo: crear un conjunto de reglas de PolicyActivity (heredado)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> El editor de reglas del [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado que se usa para tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] no es compatible con múltiples versiones.

 En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **Editor de conjunto de reglas** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Agregar regla**|Agrega una definición de regla al conjunto de reglas.|
|**Eliminar**|Elimina la regla seleccionada del conjunto de reglas.|
|**Encadenamiento**|Especifica qué tipo de encadenamiento hacia delante se debe utilizar con el conjunto de reglas. Las opciones disponibles son:<br /><br /> -   **Encadenamiento completo**, que especifica que se usen todos los mecanismos de encadenamiento de reenvío: implícito, atribución de métodos y explícito usando una función de **actualización** .<br />-   **Secuenciales**, que especifica que no se debe utilizar ningún encadenamiento hacia delante.<br />-   **Solo actualización explícita**, que especifica que solo se realice el encadenamiento hacia delante en las acciones de **actualización** .<br /><br /> Para obtener más información sobre el encadenamiento hacia delante, vea [uso de la actividad PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx).|
|**Nombre**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por nombre.|
|**Prioridad**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por prioridad.|
|**Reevaluación**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por tipo de reevaluación.|
|**Vista previa de la regla**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por la vista previa de la condición y las acciones de una regla.|
|**Nombre:**|Se usa para escribir el nombre de la regla.|
|**Prior**|Escriba una prioridad para la regla. La prioridad predeterminada es 0.|
|**Reevaluación:**|Especifica qué tipo de reevaluación de regla se debe utilizar con la regla. Las opciones disponibles son:<br /><br /> -   **Siempre**, que hace que la regla se vuelva a evaluar según sea necesario.<br />-   **Nunca**, lo que hace que la regla no se vuelva a evaluar nunca. En este caso una regla se ejecuta sólo una vez.|
|**Activo**|Se selecciona para hacer que la regla esté activa.|
|**Cumple**|Escriba una expresión para la condición de la regla. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|
|**Acciones Then:**|Escriba una expresión para las acciones Then. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|
|**Acciones Else:**|Escriba una expresión para las acciones Else. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|
|**OK (CORRECTO)**|Haga clic en Aceptar para guardar el conjunto de reglas en un archivo .rules.|

 Para obtener más información sobre los conjuntos de reglas, vea [uso de la actividad PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx).

## <a name="entering-condition-and-action-expressions"></a>Escribir expresiones de condiciones y de acciones
 Escriba las expresiones de la condición y las acciones then y else como texto en sus respectivos cuadros de texto en el cuadro de diálogo **Editor de conjunto de reglas** . Puede escribir **esto.** en el editor para hacer referencia a campos, propiedades y métodos utilizados en el flujo de trabajo, mediante un tipo de menú de IntelliSense. También puede escribir directamente un nombre de miembro del flujo de trabajo. Puede llamar a métodos estáticos en tipos a los que se hace referencia escribiendo el nombre de la clase seguido por el nombre del método.

 Puede agregar operadores lógicos a la condición, por ejemplo AND, OR y NOT. También puede agregar predicados. Un predicado es un operador binario y dos operandos. Los operadores binarios admitidos son = =, >, \<, > = y <=. Los operandos admitidos son valor constante, función aritmética y miembros con ámbito público.

 Puede especificar el tipo para la comparación y puede compararlo con **null** o una cadena vacía. Puede anidar las llamadas a miembros en una variable que contenga un tipo complejo, por ejemplo, `this.Address.State == "WA"`.

 Las expresiones admiten los operadores siguientes:

- Operadores relacionales: ==, =, !=

- Operadores de comparación: <, \<=, > , >=

- Operadores aritméticos: +, - , *, /, MOD

- Operadores lógicos: AND,  &&, OR,  &#124;&#124;, NOT,!

- Operadores bit a bit: &, &#124;

  La prioridad de los operadores de las expresiones sigue las reglas de prioridad de los operadores de C#.

  Para obtener más información sobre las condiciones, vea [uso de condiciones en flujos de trabajo](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Funciones Halt y Update
 **Después, acciones:** y **otras acciones:** las expresiones admiten las funciones **Halt** y **Update** . Para usar la función **Halt** , escriba **detener** en una **acción then: o,** si no, **acción:** cuadro de texto. La acción de **detención** hace que la ejecución del conjunto de reglas se detenga inmediatamente y el control vuelve al código de llamada. La función de **actualización** se usa con el encadenamiento hacia delante.

 Una instrucción **Update** se puede expresar en el editor de una de estas dos formas: ambos formularios se muestran en el ejemplo siguiente:

```
Update(this.Address.State)
Update("this/Address/State")
```

 Para obtener más información sobre el uso de **Update** con el encadenamiento hacia delante, vea [uso de la actividad PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx).

## <a name="see-also"></a>Consulte también
 [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [cuadro de diálogo Seleccionar conjunto de reglas (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [uso de la actividad PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx) [uso de condiciones en flujos de trabajo](https://msdn2.microsoft.com/library/bb628447.aspx)
