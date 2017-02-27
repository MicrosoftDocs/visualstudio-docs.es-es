---
title: "Dise&#241;ador de actividades Persist | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Persist.UI"
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Dise&#241;ador de actividades Persist
El diseñador de actividades **Persist** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.Persist>.  
  
## Actividad Persist  
 La actividad <xref:System.Activities.Statements.Persist> guarda un flujo de trabajo en el disco, si es posible.La actividad <xref:System.Activities.Statements.Persist> no se puede ejecutar en una zona que no sea de persistencia como, por ejemplo, dentro de una actividad <xref:System.Activities.Statements.TransactionScope>.Si utiliza una actividad <xref:System.Activities.Statements.Persist> en un ámbito que no sea de persistencia, se produce una excepción en tiempo de ejecución.  
  
### Utilizar el diseñador de actividades Persist  
 El diseñador de actividades **Persist** se puede encontrar en la categoría **Tiempo de ejecución** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas**. \(De forma alternativa, seleccione **Cuadro de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **Persist** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.Esto crea una actividad <xref:System.Activities.Statements.Persist> con un valor **DisplayName** predeterminado de Persist.El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **Persist** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
### Propiedades Persist  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Persist> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo de la actividad <xref:System.Activities.Statements.Persist>.El valor predeterminado es Persist.Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|  
  
## Vea también  
 [Tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)