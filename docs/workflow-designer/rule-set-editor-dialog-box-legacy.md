---
title: "Editor de conjunto de reglas (Cuadro de di&#225;logo) (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleSetDialog.UI"
helpviewer_keywords: 
  - "Cuadro de diálogo Editor de conjunto de reglas"
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Editor de conjunto de reglas (Cuadro de di&#225;logo) (Heredado)
En este tema se describe el uso del cuadro de diálogo **Editor de conjunto de reglas** en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado.Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 El cuadro de diálogo **Editor de conjunto de reglas** se usa para crear y modificar conjuntos de reglas de [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), que se serializan en un archivo .rules.  
  
> [!NOTE]
>  Si desea abrir el archivo .rules con el **Editor XML con codificación**, primero debe cerrar la ventana de diseñador asociada para el flujo de trabajo o actividad.  
  
 Para obtener información sobre cómo tener acceso al cuadro de diálogo **Editor de conjunto de reglas**, vea [Cómo: Crear un conjunto de reglas para PolicyActivity \(Heredado\)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  El editor de reglas del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado que se usa para tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] no es compatible con múltiples versiones.  
  
 En la tabla siguiente se describen los elementos de la interfaz de usuario \(IU\) del cuadro de diálogo **Editor de conjunto de reglas**.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------------------------------|-----------------|  
|**Agregar regla**|Agrega una definición de regla al conjunto de reglas.|  
|**Eliminar**|Elimina la regla seleccionada del conjunto de reglas.|  
|**Encadenamiento**|Especifica qué tipo de encadenamiento hacia delante se debe utilizar con el conjunto de reglas.Las opciones disponibles son:<br /><br /> -   **Encadenamiento completo**, que indica que se deben usar todos los mecanismos de encadenamiento hacia adelante: implícito, atribución de método y explícito utilizando una función **Update**.<br />-   **Secuencial**, que indica que no se debe usar ningún encadenamiento hacia adelante.<br />-   **Sólo actualización explícita**, que indica que sólo se debe realizar el encadenamiento hacia adelante en acciones **Actualizar**.<br /><br /> Para obtener más información sobre el encadenamiento hacia adelante, vea [Usar la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|**Nombre**|Encabezado de columna de la lista de conjuntos de reglas.Haga clic en él para ordenar la lista de reglas por nombre.|  
|**Prioridad**|Encabezado de columna de la lista de conjuntos de reglas.Haga clic en él para ordenar la lista de reglas por prioridad.|  
|**Reevaluación**|Encabezado de columna de la lista de conjuntos de reglas.Haga clic en él para ordenar la lista de reglas por tipo de reevaluación.|  
|**Vista previa de la regla**|Encabezado de columna de la lista de conjuntos de reglas.Haga clic en él para ordenar la lista de reglas por la vista previa de la condición y las acciones de una regla.|  
|**Nombre:**|Se usa para escribir el nombre de la regla.|  
|**Prioridad:**|Escriba una prioridad para la regla.La prioridad predeterminada es 0.|  
|**Reevaluación:**|Especifica qué tipo de reevaluación de regla se debe utilizar con la regla.Las opciones disponibles son:<br /><br /> -   **Siempre**, que hace que la regla se reevalúe cuando sea necesario.<br />-   **Nunca**, que hace que la regla no se reevalúe nunca.En este caso una regla se ejecuta sólo una vez.|  
|**Activa**|Se selecciona para hacer que la regla esté activa.|  
|**Condición:**|Escriba una expresión para la condición de la regla.Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|  
|**Acciones Then:**|Escriba una expresión para las acciones Then.Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|  
|**Acciones Else:**|Escriba una expresión para las acciones Else.Para obtener información sobre la sintaxis de las expresiones, vea la sección "Escribir expresiones de condiciones y de acciones" de esta página.|  
|**Aceptar**|Haga clic en Aceptar para guardar el conjunto de reglas en un archivo .rules.|  
  
 Para obtener más información sobre los conjuntos de reglas, vea [Usar la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## Escribir expresiones de condiciones y de acciones  
 Las expresiones para las condiciones y las acciones Then y Else se escriben como texto en sus respectivos cuadros de texto del cuadro de diálogo **Editor de conjunto de reglas**.Puede escribir **this.** en el editor para hacer referencia a los campos, propiedades y métodos utilizados en el flujo de trabajo, mediante un menú tipo IntelliSense.También puede escribir directamente un nombre de miembro del flujo de trabajo.Puede llamar a métodos estáticos en tipos a los que se hace referencia escribiendo el nombre de la clase seguido por el nombre del método.  
  
 Puede agregar operadores lógicos a la condición, por ejemplo AND, OR y NOT.También puede agregar predicados.Un predicado es un operador binario y dos operandos.Los operadores binarios admitidos son \=\=, \>, \<, \>\= y \<\=.Los operandos admitidos son valor constante, función aritmética y miembros con ámbito público.  
  
 Puede especificar el tipo de la comparación y puede comparar con **null** o una cadena vacía.Puede anidar las llamadas a miembros en una variable que contenga un tipo complejo, por ejemplo, `this.Address.State == "WA"`.  
  
 Las expresiones admiten los operadores siguientes:  
  
-   Operadores relacionales: \=\=, \=, \!\=  
  
-   Operaciones de comparación: \<, \<\=, \>, \>\=  
  
-   Operadores aritméticos: \+, \- , \*, \/, MOD  
  
-   Operadores lógicos: AND, &&, OR, &#124;&#124;, NOT, \!  
  
-   Operadores bit a bit: &, &#124;  
  
 La prioridad de los operadores de las expresiones sigue las reglas de prioridad de los operadores de C\#.  
  
 Para obtener más información sobre las condiciones, vea [Using Conditions in Workflows](http://msdn.microsoft.com/es-es/541211f5-d382-4810-894f-71f00b34fa77).  
  
### Funciones Halt y Update  
 Las expresiones de las **acciones Then:** y **acciones Else:** admiten las funciones **Halt** y **Update**.Para usar la función **Halt**, escriba **Halt** en un cuadro de texto de **Acción Then:** o **Acción Else:**.La acción **Halt** hace que la ejecución del conjunto de reglas se detenga inmediatamente y el control vuelve al código de llamada.La función **Update** se usa con el encadenamiento hacia adelante.  
  
 Una instrucción **Update** se puede expresar en el editor de una de dos formas, que se muestran en el ejemplo siguiente:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Para obtener más información sobre cómo usar **Update** con el encadenamiento hacia adelante, vea [Usar la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## Vea también  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Seleccionar conjunto de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Uso de la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Uso de condiciones en flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65009)