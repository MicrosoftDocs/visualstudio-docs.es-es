---
title: "Conjunto de reglas de cuadro de diálogo de Editor (heredado) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords: Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 1c0b55f1539526e9386df2d6de050c14fb8f59cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Editor de conjunto de reglas (Cuadro de diálogo) (Heredado)
Este tema se describe cómo utilizar el **Editor de conjunto de reglas** cuadro de diálogo heredado [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 El **Editor de conjunto de reglas** cuadro de diálogo se usa para crear y modificar [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) regla conjuntos, que se serializan en un archivo. Rules.  
  
> [!NOTE]
>  Si desea abrir el archivo .rules con el **Editor XML con codificación**, primero debe cerrar la ventana del diseñador asociada para el flujo de trabajo o actividad.  
  
 Para obtener información sobre cómo obtener acceso a la **Editor de conjunto de reglas** cuadro de diálogo, vea [Cómo: crear un conjunto de reglas de PolicyActivity (heredado)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  El editor de reglas del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado que se usa para tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] no es compatible con múltiples versiones.  
  
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
  
-   Operadores lógicos: Y, & &, OR, &#124; &#124; no es así,!  
  
-   Operadores bit a bit: &, &#124;  
  
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
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Cuadro de diálogo Seleccione la regla establecer (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Uso de la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Usar condiciones en flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65009)