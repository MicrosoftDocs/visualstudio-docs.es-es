---
title: "Dise&#241;ador de actividades TransactedReceiveScope | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.TransactedReceiveScope.UI"
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades TransactedReceiveScope
El diseñador **TransactedReceiveScope** se utiliza para crear y configurar una actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
## Actividad TransactedReceiveScope  
 La actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope> hace posible pasar una transacción a las transacciones del servidor que ha creado un flujo de trabajo o un distribuidor.  
  
### Utilizar el diseñador de actividades TransactedReceiveScope  
 El diseñador de actividades **TransactedReceiveScope** se puede encontrar en la categoría **Mensajería** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **TransactedReceiveScope** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades.De esta forma se crea una actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope> con un valor **DisplayName** predeterminado de TransactedReceiveScope.El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **TransactedReceiveScope** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
 El diseñador **TransactedReceiveScope** contiene los cuadros **Solicitar** y **Cuerpo**.Estos se utilizan para configurar la propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, que especifica una actividad <xref:System.ServiceModel.Activities.Receive> y una propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, la cual especifica alguna otra clase <xref:System.Activities.Activity>.La propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transacción.Posteriormente, la transacción se prepara para el ámbito de la propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> de forma que cualquier actividad en este ámbito se ejecute dentro de esta transacción.  
  
### Propiedades TransactedReceiveScope  
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.TransactedReceiveScope> y se describe cómo se utilizan en el diseñador.Estas propiedades <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en cuadrícula de propiedades o en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], pero el resto se deben editar en la superficie de diseño.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre opcional descriptivo de la actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope>.El valor predeterminado es TransactedReceiveScope.<br /><br /> Aunque el nombre <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar un nombre para mostrar.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Coloca una actividad <xref:System.ServiceModel.Activities.Receive> en el bloque **Solicitar** en la superficie del diseñador de actividades.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Coloca una clase <xref:System.Activities.Activity> en el bloque **Cuerpo** en la superficie del diseñador de actividades.|  
  
## Vea también  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Enviar](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)