---
title: "Diseñador de actividades TransactedReceiveScope | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 20dce7d4b3dc306c7bcd4f83a1f4e8fea10c6a94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="transactedreceivescope-activity-designer"></a>Diseñador de actividades TransactedReceiveScope
El **TransactedReceiveScope** diseñador se utiliza para crear y configurar un <xref:System.ServiceModel.Activities.TransactedReceiveScope> actividad.  
  
## <a name="the-transactedreceivescope-activity"></a>Actividad TransactedReceiveScope  
 La actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope> hace posible pasar una transacción a las transacciones del servidor que ha creado un flujo de trabajo o un distribuidor.  
  
### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilizar el diseñador de actividades TransactedReceiveScope  
 El **TransactedReceiveScope** Diseñador de actividad puede encontrarse en el **mensajería** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en la **cuadro de herramientas**  ficha [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **TransactedReceiveScope** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades. Esto crea una <xref:System.ServiceModel.Activities.TransactedReceiveScope> actividad con el valor predeterminado es **DisplayName** de TransactedReceiveScope. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **TransactedReceiveScope** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.  
  
 El **TransactedReceiveScope** diseñador contiene **solicitar** y **cuerpo** cuadros. Estos se utilizan para configurar la propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, que especifica una actividad <xref:System.ServiceModel.Activities.Receive> y una propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, la cual especifica alguna otra clase <xref:System.Activities.Activity>. La propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transacción. Posteriormente, la transacción se prepara para el ámbito de la propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> de forma que cualquier actividad en este ámbito se ejecute dentro de esta transacción.  
  
### <a name="the-transactedreceivescope-properties"></a>Propiedades TransactedReceiveScope  
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.TransactedReceiveScope> y se describe cómo se utilizan en el diseñador. Estas propiedades <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en cuadrícula de propiedades o en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], pero el resto se deben editar en la superficie de diseño.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.TransactedReceiveScope>. El valor predeterminado es TransactedReceiveScope.<br /><br /> Aunque el nombre <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar un nombre para mostrar.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Quita un <xref:System.ServiceModel.Activities.Receive> actividad en el **solicitar** bloque en la superficie del Diseñador de actividad.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Quita un <xref:System.Activities.Activity> en el **cuerpo** bloque en la superficie del Diseñador de actividad.|  
  
## <a name="see-also"></a>Vea también  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Recepción](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Enviar](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)