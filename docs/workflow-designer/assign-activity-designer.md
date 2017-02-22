---
title: "Dise&#241;ador de actividades Assign | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Assign.UI"
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades Assign
El diseñador de actividades **Assign** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.Assign>.  
  
## Actividad Assign  
 La actividad <xref:System.Activities.Statements.Assign> asigna un valor a una variable o argumento.  
  
### Utilizar el diseñador de actividades Assign  
 El diseñador de actividades **Assign** se puede encontrar en la categoría **Primitivas** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas**. \(De forma alternativa, seleccione **Cuadro de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **Assign** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.Esto crea una actividad <xref:System.Activities.Statements.Assign> con un valor **DisplayName** predeterminado de Assign.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **Assign** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
### Propiedades Assign  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Assign> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo de la actividad <xref:System.Activities.Statements.Assign>.El valor predeterminado es Assign.Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda utilizar uno.|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|La variable o argumento al que está asignado <xref:System.Activities.Statements.Assign.Value%2A>.Debe ser un identificador de Visual Basic válido.Para establecer la propiedad, escriba una expresión Visual Basic en el cuadro **Para** en el diseñador de actividades **Assign** o en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valor que se asigna a la variable.Para establecer la propiedad <xref:System.Activities.Statements.Assign.Value%2A>, escriba una expresión de Visual Basic en el cuadro de diálogo **Valor** del diseñador de actividades **Assign** o en la cuadrícula de propiedades.|  
  
## Vea también  
 [Primitivas](../workflow-designer/primitives-activity-designers.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)