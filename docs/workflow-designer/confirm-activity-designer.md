---
title: "Dise&#241;ador de actividades Confirm | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Confirm.UI"
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades Confirm
El diseñador de actividades **Confirm** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.Confirm>.  
  
## Actividad Confirm  
 La actividad <xref:System.Activities.Statements.Confirm> invoca explícitamente a la propiedad <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> para una actividad que se incluye en <xref:System.Activities.Statements.CompensableActivity>.Si la actividad <xref:System.Activities.Statements.Confirm> no se utiliza dentro de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de una clase <xref:System.Activities.Statements.CompensableActivity>, debe especificar la propiedad <xref:System.Activities.Statements.Confirm.Target%2A>.  
  
 La clase <xref:System.Activities.Statements.CompensationToken> que especificó <xref:System.Activities.Statements.Compensate.Target%2A> proporciona un medio para confirmar o compensar explícitamente una clase <xref:System.Activities.Statements.CompensableActivity> una vez que la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> se haya completado correctamente.  
  
### Utilizar el diseñador de actividades Confirm  
 El diseñador de actividades **Confirm** se puede encontrar en la categoría **Transacción** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** a la izquierda de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **Confirm** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.Esto crea una actividad <xref:System.Activities.Statements.Confirm> con un valor <xref:System.Activities.Activity.DisplayName%2A> predeterminado de Confirm.El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **Confirm** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
### Propiedades Confirm  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Confirm> y se describe cómo se utilizan en el diseñador.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en cuadrícula de propiedades o en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], pero la propiedad <xref:System.Activities.Statements.Confirm.Target%2A> se debe editar en la cuadrícula de propiedades.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.CancellationScope>.El valor predeterminado es Confirm.|  
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Especifica la clase <xref:System.Activities.InArgument%601> que contiene la clase <xref:System.Activities.Statements.CompensationToken> para esta actividad <xref:System.Activities.Statements.Confirm>.|  
  
## Vea también  
 [Transacción](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)