---
title: "Dise&#241;ador de actividades WriteLine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.WriteLine.UI"
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Dise&#241;ador de actividades WriteLine
El diseñador de actividades **WriteLine** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.WriteLine>.  
  
## Actividad WriteLine  
 La actividad <xref:System.Activities.Statements.Writeline> escribe texto en un objeto <xref:System.IO.TextWriter> especificado.Si no se especifica un objeto <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.Writeline> escribe el texto en la consola.  
  
### Utilizar el diseñador de actividades WriteLine  
 El diseñador de actividades **WriteLine** se puede encontrar en la categoría **Primitivas** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **WriteLine** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.Esto crea una actividad <xref:System.Activities.Statements.WriteLine> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de WriteLine.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **WriteLine** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
### Propiedades WriteLine  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.WriteLine> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo de la actividad <xref:System.Activities.Statements.WriteLine>.El valor predeterminado es WriteLine.Pese a que la propiedad <xref:System.Activities.Activity.DisplayName%2A> no es obligatoria, se recomienda utilizar una.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Texto que se va a escribir.Para establecer la propiedad, escriba una expresión Visual Basic en el cuadro **Texto** en el diseñador de actividades **WriteLine** o en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|El objeto <xref:System.IO.TextWriter> en el que <xref:System.Activities.Statements.WriteLine> escribe la propiedad <xref:System.Activities.Statements.WriteLine.Text%2A>.El valor predeterminado es la consola.|  
  
## Vea también  
 [Primitivas](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)