---
title: "Los diseñadores de actividades de mensajería | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2aa2383326682dcedbb0888f5b55d34e3894327c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="messaging-activity-designers"></a>Diseñadores de actividades de mensajería
Los diseñadores de actividades de mensajería se utilizan para crear y configurar actividades de mensajería que envían y reciben mensajes de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] desde una aplicación [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]. [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] presenta cinco actividades de mensajería y [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] proporciona dos nuevos diseñadores de plantillas que le permiten administrar la mensajería desde un flujo de trabajo. Los temas que se incluyen en esta sección y que se enumeran en la siguiente tabla ofrecen orientación sobre cómo utilizar los diseñadores de actividades y de plantillas de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
  
|Actividad de mensaje|Descripción|  
|----------------------|-----------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Crea y configura una actividad de la clase <xref:System.ServiceModel.Activities.CorrelationScope> que ofrece administración implícita de actividades de mensajería secundarias con un objeto <xref:System.ServiceModel.Activities.CorrelationHandle>.|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Crea y configura una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> que se utiliza para inicializar la correlación sin enviar o recibir un mensaje.|  
|[Recepción](../workflow-designer/receive-activity-designer.md)|Crea y configura una actividad <xref:System.ServiceModel.Activities.Receive> que recibe un mensaje desde un servicio.|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Crea un pareja configurada previamente de actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> dentro de una actividad <xref:System.Activities.Statements.Sequence>.|  
|[Enviar](../workflow-designer/send-activity-designer.md)|Crea y configura una actividad <xref:System.ServiceModel.Activities.Send> que envía un mensaje a un servicio.|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Crea un pareja configurada previamente de actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> dentro de una actividad <xref:System.Activities.Statements.Sequence>.|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Crea y configura una actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope> que habilita el flujo de transacciones en un flujo de trabajo.|  
  
## <a name="reference"></a>Referencia  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## <a name="related-sections"></a>Secciones relacionadas  
 Para otros tipos de diseñadores de actividades, vea los siguientes temas.  
  
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)  
  
 [Usar los diseñadores de actividad](../workflow-designer/using-the-activity-designers.md)  
  
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)  
  
 [Tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)  
  
 [Elementos primitivos](../workflow-designer/primitives-activity-designers.md)  
  
 [Transacción](../workflow-designer/transaction-activity-designers.md)  
  
 [Colección](../workflow-designer/collection-activity-designers.md)  
  
 [Control de errores](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>Recursos externos  
 [Usar los diseñadores de actividad](../workflow-designer/using-the-activity-designers.md)