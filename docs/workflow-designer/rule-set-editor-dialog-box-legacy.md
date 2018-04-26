---
title: 'Diseñador de flujo de trabajo: conjunto de reglas de cuadro de diálogo de Editor (heredado)'
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77bb10e5237b33c60b0cd309c2d3c6c634182bc6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Editor de conjunto de reglas (Cuadro de diálogo) (Heredado)

Este tema se describe cómo utilizar el **Editor de conjunto de reglas** cuadro de diálogo en el Diseñador de flujo de trabajo de Windows heredado. Use el Diseñador de flujo de trabajo heredado cuando deba tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

El **Editor de conjunto de reglas** cuadro de diálogo se usa para crear y modificar [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) regla conjuntos, que se serializan en un archivo. Rules.

> [!NOTE]
> Si desea abrir el archivo .rules con el **Editor XML con codificación**, primero debe cerrar la ventana del diseñador asociada para el flujo de trabajo o actividad.

Para obtener información sobre cómo obtener acceso a la **Editor de conjunto de reglas** cuadro de diálogo, vea [Cómo: crear un conjunto de reglas de PolicyActivity (heredado)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> El editor de reglas del Diseñador de flujo de trabajo heredado que se usa como destino la versión 3.5 de .NET Framework o el conocido como WinFX no compatible con múltiples versiones.

La tabla siguiente describen los elementos de interfaz de usuario de la **Editor de conjunto de reglas** cuadro de diálogo.

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Agregar regla**|Agrega una definición de regla al conjunto de reglas.|
|**Eliminar**|Elimina la regla seleccionada del conjunto de reglas.|
|**Encadenamiento**|Especifica qué tipo de encadenamiento hacia delante se debe utilizar con el conjunto de reglas. Las opciones disponibles son:<br /><br /> -   **Encadenamiento completo**, que especifica que se use reenviar todos los mecanismos de encadenamiento: implícito, atribución de método y explícito utilizando una **actualización** función.<br />-   **Secuencial**, que especifica no se utiliza ningún encadenamiento hacia adelante.<br />-   **Sólo actualización explícita**, que especifica que sólo realice encadenamiento hacia adelante en **actualización** acciones.<br /><br /> Para obtener más información sobre el encadenamiento progresivo, vea [mediante la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|
|**Name**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por nombre.|
|**Prioridad**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por prioridad.|
|**Reevaluación**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por tipo de reevaluación.|
|**Vista previa de la regla**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por la vista previa de la condición y las acciones de una regla.|
|**Nombre:**|Se usa para escribir el nombre de la regla.|
|**Prioridad:**|Escriba una prioridad para la regla. La prioridad predeterminada es 0.|
|**Reevaluación:**|Especifica qué tipo de reevaluación de regla se debe utilizar con la regla. Las opciones disponibles son:<br /><br /> -   **Siempre**, lo que hace que la regla se reevalúe según sea necesario.<br />-   **Nunca**, lo que hace que la regla se reevalúe nunca. En este caso una regla se ejecuta sólo una vez.|
|**Active**|Se selecciona para hacer que la regla esté activa.|
|**Condición:**|Escriba una expresión para la condición de la regla. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|
|**A continuación, acciones:**|Escriba una expresión para las acciones Then. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|
|**Acciones Else:**|Escriba una expresión para las acciones Else. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|
|**VALE**|Haga clic en Aceptar para guardar el conjunto de reglas en un archivo .rules.|

 Para obtener más información acerca de los conjuntos de reglas, consulte [mediante la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>Escribir expresiones de condiciones y de acciones
 Escribir expresiones para las condiciones y Then y Else acciones como texto en sus respectivos cuadros la **Editor de conjunto de reglas** cuadro de diálogo. Puede escribir **esto.** en el editor para hacer referencia a campos, propiedades y métodos que se utilizan en el flujo de trabajo, utilizando un tipo de IntelliSense del menú. También puede escribir directamente un nombre de miembro del flujo de trabajo. Puede llamar a métodos estáticos en tipos a los que se hace referencia escribiendo el nombre de la clase seguido por el nombre del método.

 Puede agregar operadores lógicos a la condición, por ejemplo AND, OR y NOT. También puede agregar predicados. Un predicado es un operador binario y dos operandos. Los operadores binarios admitidos son ==, >, \<, > =, y < =. Los operandos admitidos son valor constante, función aritmética y miembros con ámbito público.

 Puede especificar el tipo de la comparación y puede comparar con **null** o una cadena vacía. Puede anidar las llamadas a miembros en una variable que contenga un tipo complejo, por ejemplo, `this.Address.State == "WA"`.

 Las expresiones admiten los operadores siguientes:

-   Operadores relacionales: ==, =, !=

-   Operadores de comparación: <, \<=, >, > =

-   Operadores aritméticos: +, - , *, /, MOD

-   Operadores lógicos: Y, & &, OR, &#124; &#124;, NOT,!

-   Operadores bit a bit: &,&#124;

 La prioridad de los operadores de las expresiones sigue las reglas de prioridad de los operadores de C#.

 Para obtener más información acerca de las condiciones, consulte [uso de condiciones en flujos de trabajo](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Funciones Halt y Update
 **Acciones Then:** y **acciones Else:** las expresiones admiten **detener** y **actualización** funciones. Para usar el **detener** función, escriba **detener** en un **, a continuación, acción:** o **acción Else:** cuadro de texto. El **detener** acción provoca la ejecución del conjunto de reglas detener inmediatamente, y el control vuelve al código de llamada. Usa el **actualización** función con el encadenamiento hacia delante.

 Un **actualización** instrucción se puede expresar en el editor en uno de estos dos formatos; se muestran en el ejemplo siguiente:

```
Update(this.Address.State)
Update("this/Address/State")
```

 Para obtener más información sobre el uso de **actualización** con el encadenamiento progresivo, vea [mediante la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>Vea también

- [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [Cuadro de diálogo Seleccionar conjunto de reglas (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [Uso de la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)
- [Usar condiciones en flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65009)