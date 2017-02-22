---
title: "Dise&#241;adores de actividades de mensajer&#237;a | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;adores de actividades de mensajer&#237;a
Los diseñadores de actividades de mensajería se utilizan para crear y configurar actividades de mensajería que envían y reciben mensajes de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] desde una aplicación [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)].[!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] presenta cinco actividades de mensajería y [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] proporciona dos nuevos diseñadores de plantillas que le permiten administrar la mensajería desde un flujo de trabajo.Los temas que se incluyen en esta sección y que se enumeran en la siguiente tabla ofrecen indicaciones sobre cómo usar los diseñadores de actividades y de plantillas del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
## En esta sección  
  
|Actividad de mensaje|Descripción|  
|--------------------------|-----------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Crea y configura una actividad de la clase <xref:System.ServiceModel.Activities.CorrelationScope> que ofrece administración implícita de actividades de mensajería secundarias con un objeto <xref:System.ServiceModel.Activities.CorrelationHandle>.|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Crea y configura una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> que se utiliza para inicializar la correlación sin enviar o recibir un mensaje.|  
|[Receive](../workflow-designer/receive-activity-designer.md)|Crea y configura una actividad <xref:System.ServiceModel.Activities.Receive> que recibe un mensaje desde un servicio.|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Crea una pareja configurada previamente de actividades <xref:System.ServiceModel.Activities.ReceiveReply> y <xref:System.ServiceModel.Activities.Send> dentro de una actividad <xref:System.Activities.Statements.Sequence>.|  
|[Enviar](../workflow-designer/send-activity-designer.md)|Crea y configura una actividad <xref:System.ServiceModel.Activities.Send> que envía un mensaje a un servicio.|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Crea un pareja configurada previamente de actividades <xref:System.ServiceModel.Activities.SendReply> y <xref:System.ServiceModel.Activities.Receive> dentro de una actividad <xref:System.Activities.Statements.Sequence>.|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Crea y configura una actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope> que habilita el flujo de transacciones en un flujo de trabajo.|  
  
## Referencia  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## Secciones relacionadas  
 Para otros tipos de diseñadores de actividades, vea los siguientes temas.  
  
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)  
  
 [Utilizar los diseñadores de actividades](../workflow-designer/using-the-activity-designers.md)  
  
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)  
  
 [Tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)  
  
 [Primitivas](../workflow-designer/primitives-activity-designers.md)  
  
 [Transacción](../workflow-designer/transaction-activity-designers.md)  
  
 [Colección](../workflow-designer/collection-activity-designers.md)  
  
 [Control de errores](../workflow-designer/error-handling-activity-designers.md)  
  
## Recursos externos  
 [Utilizar los diseñadores de actividades](../workflow-designer/using-the-activity-designers.md)