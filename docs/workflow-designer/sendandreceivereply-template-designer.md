---
title: "Dise&#241;ador de plantillas SendAndReceiveReply | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.SendAndReceiveReply.UI"
  - "System.ServiceModel.Activities.ReceiveReply.UI"
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de plantillas SendAndReceiveReply
La plantilla **SendAndReceiveReply** se utiliza para crear una pareja con las actividades <xref:System.ServiceModel.Activities.ReceiveReply> y <xref:System.ServiceModel.Activities.Send> configuradas previamente dentro de una actividad <xref:System.Activities.Statements.Sequence> y que se correlacionan como parte de un modelo de intercambio de mensajes solicitud\/respuesta en el cliente.  
  
## Plantilla SendAndReceiveReply  
 Cuando se agrega una plantilla **SendAndReceiveReply**, ocurren tres cosas además de la creación de las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> dentro de una actividad <xref:System.Activities.Statements.Sequence>:  
  
1.  Configura las propiedades <xref:System.ServiceModel.Activities.Send.OperationName%2A> y <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Send>.  
  
2.  Enlaza la propiedad <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.ReceiveReply> con la actividad <xref:System.ServiceModel.Activities.Send>.  
  
3.  Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.  
  
### Utilizar el diseñador de plantillas SendAndReceiveReply  
 El diseñador de actividades **SendAndReceiveReply** se puede encontrar en la categoría **Mensajería** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **SendAndReceiveReply** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades.Esto crea una actividad <xref:System.ServiceModel.Activities.Send> que se puede configurar con el diseñador de actividades **Send** y una clase <xref:System.ServiceModel.Activities.ReceiveReply> correlacionada que se puede configurar con el diseñador **ReceiveReplyForSend**.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] sobre cómo se utiliza el diseñador **Send** para configurar la actividad <xref:System.ServiceModel.Activities.Send>, vea el tema [Enviar](../workflow-designer/send-activity-designer.md).  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] sobre cómo utilizar el diseñador **ReceiveReplyForSend** para configurar la actividad <xref:System.ServiceModel.Activities.ReceiveReply>, vea la siguiente sección.  
  
### Propiedades ReceiveReply  
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.ReceiveReply> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre opcional descriptivo de la actividad <xref:System.ServiceModel.Activities.ReceiveReply>.El valor predeterminado es ReceiveReplyForSend.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|Referencia a la actividad <xref:System.ServiceModel.Activities.Send> emparejada con esta actividad <xref:System.ServiceModel.Activities.ReceiveReply>.Esta propiedad no debe ser **null**.Las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> se usan juntas en el lado de cliente para crear un modelo de mensajería de solicitud\/respuesta.Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja.En el diseñador, no puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> a partir de la cual se creó la actividad <xref:System.ServiceModel.Activities.ReceiveReply>.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Especifica el mensaje o contenido del parámetro que se va a recibir.Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>.Modifique esta propiedad, para ello haga clic en el botón de puntos suspensivos junto al campo **Contenido** en la cuadrícula de propiedades o haga clic en el botón **Definir...** junto a la etiqueta **Contenido** en la superficie del diseñador de actividades **Receive**.Ambos muestran el cuadro de diálogo **Definición de contenido**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] cómo usar este cuadro, vea el tema [Definición de contenido \(cuadro de diálogo\)](../workflow-designer/content-definition-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo.Haga clic en el botón de puntos suspensivos junto a la propiedad <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> en la cuadrícula de propiedades para abrir el cuadro de diálogo **Agregar inicializadores de correlación**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] cómo usar este cuadro, vea el tema [Agregar CorrelationInitializers \(cuadro de diálogo\)](../workflow-designer/add-correlationinitializers-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Especifica el encabezado de acción del mensaje.Si no se establece explícitamente, el valor predeterminado será:<br /><br /> **https:\/\/tempuri.org\/{espacio de nombres del contrato de servicio}\/{nombre del contrato de servicio}\/{nombre de la operación}.**|  
  
## Vea también  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Enviar](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)