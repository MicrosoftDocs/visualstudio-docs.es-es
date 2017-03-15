---
title: "Dise&#241;ador actividades TerminateWorkflow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TerminateWorkflow.UI"
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Dise&#241;ador actividades TerminateWorkflow
El diseñador de actividades **TerminateWorkflow** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.TerminateWorkflow>.  
  
## Actividad TerminateWorkflow  
 La actividad <xref:System.Activities.Statements.TerminateWorkflow> finaliza la ejecución de un flujo de trabajo.  
  
### Utilizar el diseñador de actividades TerminateWorkflow  
 El diseñador de actividades **TerminateWorkflow** se puede encontrar en la categoría **Tiempo de ejecución** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas**. \(De forma alternativa, seleccione **Cuadro de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **TerminateWorkflow** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.De esta forma se crea una actividad <xref:System.Activities.Statements.TerminateWorkflow> con una propiedad **DisplayName** predeterminada de TerminateWorkflow.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **TerminateWorkflow** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
### Propiedades TerminateWorkflow  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.TerminateWorkflow> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.TerminateWorkflow>.El valor predeterminado es TerminateWorkflow.Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|La excepción que se va a producir cuando se finaliza el flujo de trabajo.Establezca esta propiedad en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|La razón que explica por qué finalizó el flujo de trabajo.Establezca esta propiedad en la cuadrícula de propiedades.|  
  
## Vea también  
 [Tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)