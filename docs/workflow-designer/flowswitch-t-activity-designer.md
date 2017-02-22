---
title: "Dise&#241;ador de actividades FlowSwitch&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Core.Presentation.FlowSwitchLink.UI"
  - "System.Activities.Statements.FlowSwitch`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLink`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI"
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades FlowSwitch&lt;T&gt;
La actividad <xref:System.Activities.Statements.FlowSwitch%601> es un nodo condicional que proporciona capacidad de bifurcación para el flujo de control según criterios de coincidencia cuando se necesitan más de dos bifurcaciones alternativas.Si la bifurcación del flujo requiere dos rutas de acceso, utilice la actividad <xref:System.Activities.Statements.FlowDecision> en su lugar.  
  
## Actividad FlowSwitch\<T\>  
 La actividad <xref:System.Activities.Statements.FlowSwitch%601> contiene una propiedad <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> que devuelve un valor de tipo *T* \(que especifica el parámetro genérico\) cuando se evalúa.La actividad también contiene un conjunto de propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, que especifica una asignación única de posibles resultados de esta evaluación para un conjunto de objetos <xref:System.Activities.Statements.FlowNode>.La propiedad <xref:System.Activities.Statements.FlowNode> que se ejecutó tiene un objeto de tipo *T* que coincide con el valor de propiedad <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> que se ha evaluado.Se puede proporcionar \(opcionalmente\) un caso <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> para el caso en el que no se obtuvo ninguna coincidencia.  
  
### Utilizar el diseñador de actividades FlowSwitch\<T\>  
 El diseñador de actividades **FlowSwitch\<T\>** se puede encontrar en la categoría **Flujo de control** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** a la izquierda de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **FlowSwitch\<T\>** se puede arrastrar desde el **Cuadro de herramientas** y colocar en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] en un diseñador de actividades **Flowchart**.Utilice la ventana **Seleccionar tipos** que se muestra para especificar el tipo \(asociado en código a la clase <xref:System.Activities.Statements.FlowSwitch%601> por su parámetro genérico\) que se obtuvo al evaluar la propiedad <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>.Este procedimiento crea una actividad <xref:System.Activities.Statements.FlowSwitch%601> con la etiqueta **Switch** dentro de la actividad <xref:System.Activities.Statements.Flowchart>.<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> puede aparecer en el cuadro **Expresión** de la ventana **Propiedades** si hace clic donde aparece el texto con la sugerencia "Escriba una expresión de VB".  
  
 Pase el mouse sobre el diseñador de actividad **FlowSwitch\<T\>** para que aparezcan alrededor de los bordes los identificadores cuadrados que se usan para vincular la propiedad <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.Tras arrastras el diseñador de actividades **FlowSwitch\<T\>** y otros diseñadores de actividades al **Diagrama de flujo**, los objetos <xref:System.Activities.Activity> que representan estará listos para vincularse entre sí con el fin de especificar el orden de ejecución.Para crear una de las propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> asociadas a <xref:System.Activities.Statements.FlowSwitch%601>, haga clic en uno de los identificadores de caso de forma cuadrada en el perímetro del diseñador de actividades **FlowSwitch\<T\>** y arrástrelo \(mantenga, para ello, presionado el botón del mouse\) hacia uno de los identificadores que aparece de manera similar en torno a la actividad de destino cuando se mantiene el mouse sobre su diseñador.Suelte el botón del mouse y aparecerá una flecha desde el diseñador de clases **FlowSwitch\<T\>** hasta el diseñador de destino, que representa este caso.El valor predeterminado para este caso se muestra en la flecha y se puede editar en el cuadro **Caso** de la ventana **Propiedades**.  
  
### Propiedades FlowSwitch\<T\>  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.FlowSwitch%601> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Especifica la expresión que se evalúa para determinar cuál de las propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> se va intercambiar en la ruta de acceso de ejecución.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Especifica una asignación única de los posibles resultados que se obtienen al evaluar la propiedad <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> para un conjunto de objetos <xref:System.Activities.Statements.FlowNode>.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Especifica la asignación cuando la evaluación de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> no coincide con uno de los valores que contiene el objeto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|  
  
## Vea también  
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)   
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)