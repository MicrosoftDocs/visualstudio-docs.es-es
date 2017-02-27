---
title: "Dise&#241;ador de plantillas ReceiveAndSendReply | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.ReceiveAndSendReply.UI"
  - "System.ServiceModel.Activities.SendReply.UI"
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Dise&#241;ador de plantillas ReceiveAndSendReply
La plantilla **ReceiveAndSendReply** se utiliza para crear una pareja con las actividades <xref:System.ServiceModel.Activities.SendReply> y <xref:System.ServiceModel.Activities.Receive> configuradas previamente dentro de una actividad <xref:System.Activities.Statements.Sequence> y que se correlacionan como parte de un modelo de intercambio de mensajes solicitud\/respuesta en el servidor.  
  
## Plantilla ReceiveAndSendReply  
 Cuando se agrega una plantilla **ReceiveAndSendReply**, ocurren tres cosas además de la creación de las actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> con una actividad <xref:System.Activities.Statements.Sequence>:  
  
1.  Configura las propiedades <xref:System.ServiceModel.Activities.Receive.OperationName%2A> y <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Receive>.  
  
2.  Enlaza la propiedad <xref:System.ServiceModel.Activities.SendReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.Receive> para la actividad <xref:System.ServiceModel.Activities.Send>.  
  
3.  Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.  
  
### Utilizar el diseñador de plantillas ReceiveAndSendReply  
 El diseñador de actividades **ReceiveAndSendReply** se puede encontrar en la categoría **Mensajería** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **ReceiveAndSendReply** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades.Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> que se puede configurar con el diseñador de actividades **Send** y una clase <xref:System.ServiceModel.Activities.SendReply> correlacionada que se puede configurar con el diseñador SendReplyToReceive.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] sobre cómo se utiliza el diseñador **Receive** para configurar la actividad <xref:System.ServiceModel.Activities.Receive>, vea el tema [Receive](../workflow-designer/receive-activity-designer.md).  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] sobre cómo utilizar el diseñador **SendReplyToReceive** para configurar la actividad <xref:System.ServiceModel.Activities.SendReply>, vea la siguiente sección.  
  
### Propiedades SendReply  
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.SendReply> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre opcional descriptivo de la actividad <xref:System.ServiceModel.Activities.SendReply>.El valor predeterminado es SendReplyToReceive.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.|  
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Referencia a la actividad <xref:System.ServiceModel.Activities.Receive> emparejada con esta actividad <xref:System.ServiceModel.Activities.SendReply>.Esta propiedad no debe ser **null**.Las actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> se usan juntas en el servidor para modelar un mensaje de mensajería de solicitud\/respuesta.Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja.En el diseñador, no puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> a partir de la cual se creó la actividad <xref:System.ServiceModel.Activities.SendReply>.|  
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Especifica el mensaje o contenido del parámetro que se va a recibir.Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>.Modifique esta propiedad, para ello haga clic en el botón de puntos suspensivos junto al campo **Contenido** en la cuadrícula de propiedades o haga clic en el botón **Definir...** junto a la etiqueta **Contenido** en la superficie del diseñador de actividades **Receive**.Ambos muestran el cuadro de diálogo **Definición de contenido**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] cómo usar este cuadro, vea el tema [Definición de contenido \(cuadro de diálogo\)](../workflow-designer/content-definition-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo.Haga clic en el botón de puntos suspensivos junto a la propiedad <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> en la cuadrícula de propiedades para abrir el cuadro de diálogo **Agregar inicializadores de correlación**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] cómo usar este cuadro, vea el tema [Agregar CorrelationInitializers \(cuadro de diálogo\)](../workflow-designer/add-correlationinitializers-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Especifica el encabezado de acción del mensaje.Si no se establece explícitamente, el valor predeterminado será:<br /><br /> **https:\/\/tempuri.org\/{espacio de nombres del contrato de servicio}\/{nombre del contrato de servicio}\/{nombre de la operación}**|  
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Especifica si la instancia de flujo de trabajo se debe conservar antes de que se envíe el mensaje de respuesta.El valor predeterminado es **false**.|  
  
## Vea también  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [Enviar](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)