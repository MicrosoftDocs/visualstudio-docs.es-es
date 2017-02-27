---
title: "Dise&#241;ador de actividades CancellationScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CancellationScope.UI"
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Dise&#241;ador de actividades CancellationScope
El diseñador de actividades **CancellationScope** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.CancellationScope>.  
  
## Actividad CancellationScope  
 La actividad <xref:System.Activities.Statements.CancellationScope> le permite especificar una actividad para la lógica de ejecución y cancelación de esa actividad.  
  
### Utilizar el diseñador de actividades CancellationScope  
 El diseñador de actividades **CancellationScope** se puede encontrar en la categoría **Transacción** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **CancellationScope** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente, como en una clase <xref:System.Activities.Statements.Sequence>.De esta forma se crea una actividad <xref:System.Activities.Statements.CancellationScope> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de CancellationScope.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **CancellationScope** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
### Propiedades CancellationScope  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CancellationScope> y se describe cómo se utilizan en el diseñador.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en cuadrícula de propiedades, pero las otras propiedades se debe editar en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.CancellationScope>.El valor predeterminado es CancellationScope.Pese a que el valor de <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda utilizar uno.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Especifica la actividad para la que se proporciona la lógica de cancelación.Para agregar la actividad <xref:System.Activities.Statements.CancellationScope.Body%2A>, coloque una actividad del **Cuadro de herramientas** en el cuadro **Body** del diseñador de actividades **CancellationScope** que tenga el texto con la sugerencia "Coloque la actividad aquí".|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Especifica la actividad que se ejecuta en caso de cancelación.Para agregar la actividad <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, coloque una actividad del **Cuadro de herramientas** en el cuadro **CancellationHandler** del diseñador de actividades **CancellationScope** que tenga el texto con la sugerencia "Coloque la actividad aquí".|  
  
## Vea también  
 [Transacción](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)