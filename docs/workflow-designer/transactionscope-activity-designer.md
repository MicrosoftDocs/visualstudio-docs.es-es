---
title: "Dise&#241;ador de actividades TransactionScope | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TransactionScope.UI"
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades TransactionScope
El diseñador de actividades **TransactionScope** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.TransactionScope>.  
  
## Actividad TransactionScope  
 La actividad <xref:System.Activities.Statements.TransactionScope> ejecuta la actividad que contiene una transacción única.La transacción se confirma cuando la actividad <xref:System.Activities.Statements.TransactionScope.Body%2A> y el resto de participantes en la transacción hayan finalizado correctamente.  
  
### Utilizar el diseñador de actividades TransactionScope  
 El diseñador de actividades **TransactionScope** se puede encontrar en la categoría **Transacción** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **TransactionScope** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.De esta forma se crea una actividad <xref:System.Activities.Statements.TransactionScope> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de TransactionScope.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **TransactionScope** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
### Las propiedades de TransactionScope  
 En la tabla siguiente se muestran las propiedades de <xref:System.Activities.Statements.TransactionScope> y se describe cómo se usan en el diseñador.Las propiedades <xref:System.Activities.Activity.DisplayName%2A> y <xref:System.Activities.Statements.TransactionScope.Body%2A> se pueden editar en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Pero el resto de propiedades se deben editar en la cuadrícula de propiedades.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.TransactionScope>.El valor predeterminado es TransactionScope.Pese a que el valor de <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda utilizar uno.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Especifica la actividad que se va a ejecutar en una transacción única.Para agregar la actividad <xref:System.Activities.Statements.TransactionScope.Body%2A>, coloque una actividad del **Cuadro de herramientas** en el cuadro **Body** del diseñador de actividades **TransactionScope** que tenga el texto con la sugerencia "Coloque la actividad aquí".|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Especifica la enumeración <xref:System.Transactions.IsolationLevel> de este objeto <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Especifica el intervalo de tiempo \(con formato 00:00:00, que indica horas:minutos:segundos\) del que dispone la transacción para completarse.El valor predeterminado es 1 minuto \(00:01:00\).|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A>|True|Especifica el valor que indica si se debe anular el flujo de trabajo si se anula la transacción.|  
  
## Vea también  
 [Transacción](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)