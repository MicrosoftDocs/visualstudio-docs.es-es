---
title: "Dise&#241;ador actividades Sequence | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Sequence.UI"
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador actividades Sequence
La actividad <xref:System.Activities.Statements.Sequence> contiene una colección ordenada de actividades secundarias que ejecuta por orden.  
  
 Otra manera de ejecutar un conjunto de actividades por orden es utilizar una actividad <xref:System.Activities.Statements.Flowchart>.Considere la posibilidad de usar la actividad [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md) cuando disponga de un programa de bifurcación simple o de bucle que desee modelar en forma de diagrama.  
  
## Utilizar el diseñador de actividades Sequence  
 Para agregar una actividad <xref:System.Activities.Statements.Sequence>, arrastre el diseñador de actividades **Sequence** desde el **Cuadro de herramientas** y colóquelo en la superficie de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Para agregar una actividad secundaria a esta actividad <xref:System.Activities.Statements.Sequence>, arrastre alguna otra actividad desde el **Cuadro de herramientas** y colóquela en el triángulo en el cuadro donde aparece el texto con la sugerencia "Coloque la actividad aquí".  
  
### Propiedades de la actividad Sequence en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las propiedades de <xref:System.Activities.Statements.Sequence> y se describe cómo se usan en el diseñador.Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.Sequence> en el encabezado.El valor predeterminado es Sequence.El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades.<br /><br /> Pese a que la propiedad <xref:System.Activities.Activity.DisplayName%2A> no es obligatoria, se recomienda utilizar una.|  
  
## Vea también  
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)