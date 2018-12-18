---
title: Cuadro de diálogo del Editor (heredado) conjunto de reglas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 3469e395ee50e63f8ac76e4181d02b777ccbd4ba
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942405"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Editor de conjunto de reglas (Cuadro de diálogo) (Heredado)
Este tema se describe cómo usar el **Editor de conjunto de reglas** cuadro de diálogo heredado [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 El **Editor de conjunto de reglas** cuadro de diálogo se usa para crear y modificar [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) conjuntos, que se serializan en un archivo. rules de reglas.  
  
> [!NOTE]
>  Si desea abrir el archivo .rules con el **Editor XML con codificación**, primero debe cerrar la ventana del diseñador asociada para el flujo de trabajo o actividad.  
  
 Para obtener información acerca de cómo obtener acceso a la **Editor de conjunto de reglas** cuadro de diálogo, vea [Cómo: crear un conjunto de reglas de PolicyActivity (heredado)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  El editor de reglas del [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado que se usa para tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] no es compatible con múltiples versiones.  
  
 La tabla siguiente describen los elementos de interfaz de usuario de la **Editor de conjunto de reglas** cuadro de diálogo.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------|-----------------|  
|**Agregar regla**|Agrega una definición de regla al conjunto de reglas.|  
|**Eliminar**|Elimina la regla seleccionada del conjunto de reglas.|  
|**Encadenamiento**|Especifica qué tipo de encadenamiento hacia delante se debe utilizar con el conjunto de reglas. Las opciones disponibles son:<br /><br /> -   **Encadenamiento completo**, que especifica el uso de mecanismos de encadenamiento hacia delante todos los: implícito, atribución de método y explícito utilizando una **actualización** función.<br />-   **Secuencial**, que especifica no se debe utilizar ningún encadenamiento hacia adelante.<br />-   **Sólo actualización explícita**, que especifica para realizar sólo el encadenamiento hacia delante en **actualización** acciones.<br /><br /> Para obtener más información sobre el encadenamiento progresivo, vea [mediante la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|**Name**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por nombre.|  
|**Prioridad**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por prioridad.|  
|**Reevaluación**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por tipo de reevaluación.|  
|**Vista previa de la regla**|Encabezado de columna de la lista de conjuntos de reglas. Haga clic en él para ordenar la lista de reglas por la vista previa de la condición y las acciones de una regla.|  
|**Nombre:**|Se usa para escribir el nombre de la regla.|  
|**Prioridad:**|Escriba una prioridad para la regla. La prioridad predeterminada es 0.|  
|**Reevaluación:**|Especifica qué tipo de reevaluación de regla se debe utilizar con la regla. Las opciones disponibles son:<br /><br /> -   **Siempre**, lo que hace que la regla se reevalúe cuando sea necesario.<br />-   **Nunca**, lo que hace que la regla se reevalúe nunca. En este caso una regla se ejecuta sólo una vez.|  
|**Active**|Se selecciona para hacer que la regla esté activa.|  
|**Condición:**|Escriba una expresión para la condición de la regla. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|  
|**Acciones Then:**|Escriba una expresión para las acciones Then. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|  
|**Acciones Else:**|Escriba una expresión para las acciones Else. Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|  
|**VALE**|Haga clic en Aceptar para guardar el conjunto de reglas en un archivo .rules.|  
  
 Para obtener más información sobre los conjuntos de reglas, consulte [mediante la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="entering-condition-and-action-expressions"></a>Escribir expresiones de condiciones y de acciones  
 Escriba las expresiones para la condición y Then y Else acciones como texto en sus respectivos cuadros en el **Editor de conjunto de reglas** cuadro de diálogo. Puede escribir **esto.** en el editor para hacer referencia a campos, propiedades y métodos utilizados en el flujo de trabajo, mediante un tipo de IntelliSense del menú. También puede escribir directamente un nombre de miembro del flujo de trabajo. Puede llamar a métodos estáticos en tipos a los que se hace referencia escribiendo el nombre de la clase seguido por el nombre del método.  
  
 Puede agregar operadores lógicos a la condición, por ejemplo AND, OR y NOT. También puede agregar predicados. Un predicado es un operador binario y dos operandos. Los operadores binarios admitidos son ==, >, \<, > =, y < =. Los operandos admitidos son valor constante, función aritmética y miembros con ámbito público.  
  
 Puede especificar el tipo para la comparación y puede comparar con **null** o una cadena vacía. Puede anidar las llamadas a miembros en una variable que contenga un tipo complejo, por ejemplo, `this.Address.State == "WA"`.  
  
 Las expresiones admiten los operadores siguientes:  
  
- Operadores relacionales: ==, =, !=  
  
- Operadores de comparación: <, \<=, >, > =  
  
- Operadores aritméticos: +, - , *, /, MOD  
  
- Operadores lógicos: Y, & &, OR, &#124; &#124;, NOT,!  
  
- Operadores bit a bit: &,&#124;  
  
  La prioridad de los operadores de las expresiones sigue las reglas de prioridad de los operadores de C#.  
  
  Para obtener más información acerca de las condiciones, consulte [usar condiciones en flujos de trabajo](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77).  
  
### <a name="halt-and-update-functions"></a>Funciones Halt y Update  
 **Acciones Then:** y **acciones Else:** expresiones admiten **Halt** y **actualización** funciones. Para usar el **Halt** de función, escriba **Halt** en un **, a continuación, acción:** o **acción Else:** cuadro de texto. El **Halt** acción hace que la ejecución del conjunto de reglas detener inmediatamente, y el control vuelve al código de llamada. Usa el **actualización** función con el encadenamiento hacia delante.  
  
 Un **actualización** instrucción se puede expresar en el editor de una de estas dos formas; se muestran en el ejemplo siguiente:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Para obtener más información sobre el uso de **actualización** con el encadenamiento progresivo, vea [mediante la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="see-also"></a>Vea también  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Cuadro de diálogo Establecer seleccione la regla (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Uso de la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Uso de condiciones en flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65009)