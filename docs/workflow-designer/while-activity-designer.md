---
title: "Dise&#241;ador de actividades While | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.While.UI"
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades While
La actividad <xref:System.Activities.Statements.While> ejecuta la actividad que se encuentra en su propiedad <xref:System.Activities.Statements.While.Body%2A> mientras la propiedad <xref:System.Activities.Statements.Condition%2A> especificada se evalúa con el valor **true**.La actividad contenida nunca se puede ejecutar.Si desea ejecutar la actividad contenida al menos una vez, utilice la actividad <xref:System.Activities.Statements.DoWhile> en su lugar.  
  
## Propiedades While en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.While> más útiles y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.While> en el encabezado.El valor predeterminado es While.El valor se puede editar en la ventana **Propiedades** o directamente en el encabezado del diseñador de actividades.<br /><br /> Pese a que la propiedad <xref:System.Activities.Activity.DisplayName%2A> no es obligatoria, se recomienda utilizar una.|  
|<xref:System.Activities.Statements.While.Body%2A>|False|Contiene la actividad que se va ejecutar mientras que <xref:System.Activities.Statements.Condition%2A> se evalúe con el valor **true**.|  
|<xref:System.Activities.Statements.Condition%2A>|True|Contiene la expresión de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] que se evalúa para determinar si se va a ejecutar la actividad en la propiedad <xref:System.Activities.Statements.While.Body%2A>.|  
  
## Vea también  
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)