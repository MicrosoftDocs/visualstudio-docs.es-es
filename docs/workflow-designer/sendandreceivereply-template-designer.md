---
title: "Diseñador de plantillas SendAndReceiveReply | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 314ff5252b426610b9a50327fe6754b2a953908c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sendandreceivereply-template-designer"></a>Diseñador de plantillas SendAndReceiveReply
El **SendAndReceiveReply** plantilla se usa para crear un par de configuradas previamente <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> actividades dentro de un <xref:System.Activities.Statements.Sequence> actividad que se correlacionan como parte de un intercambio de mensajes de solicitud/respuesta modelo en el cliente.  
  
## <a name="the-sendandreceivereply-template"></a>Plantilla SendAndReceiveReply  
 Agregar **SendAndReceiveReply** plantilla hace tres cosas además de crear el <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> actividades dentro de un <xref:System.Activities.Statements.Sequence> actividad:  
  
1.  Configura las propiedades <xref:System.ServiceModel.Activities.Send.OperationName%2A> y <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Send>.  
  
2.  Enlaza la propiedad <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.ReceiveReply> para la actividad <xref:System.ServiceModel.Activities.Send>.  
  
3.  Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.  
  
### <a name="using-the-sendandreceivereply-template-designer"></a>Utilizar el diseñador de plantillas SendAndReceiveReply  
 El **SendAndReceiveReply** Diseñador de actividad puede encontrarse en el **mensajería** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en la **cuadro de herramientas**  ficha [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **SendAndReceiveReply** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades. Esto crea una <xref:System.ServiceModel.Activities.Send> actividad que se pueden configurar con el **enviar** Diseñador de actividad y un correlacionados <xref:System.ServiceModel.Activities.ReceiveReply> que pueden configurarse con la **ReceiveReplyForSend** diseñador.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]mediante el **enviar** diseñador para configurar el <xref:System.ServiceModel.Activities.Send> actividad, consulte la [enviar](../workflow-designer/send-activity-designer.md) tema.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]mediante el **ReceiveReplyForSend** diseñador para configurar la <xref:System.ServiceModel.Activities.ReceiveReply> actividad, consulte la sección siguiente.  
  
### <a name="properties-of-receivereply"></a>Propiedades ReceiveReply  
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.ReceiveReply> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.ReceiveReply>. El valor predeterminado es ReceiveReplyForSend.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|Referencia a la actividad <xref:System.ServiceModel.Activities.Send> emparejada con esta actividad <xref:System.ServiceModel.Activities.ReceiveReply>. Esta propiedad no debe ser **null**. Las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> se usan juntas en el lado de cliente para crear un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> a partir de la cual se creó la actividad <xref:System.ServiceModel.Activities.ReceiveReply>.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Editar esta propiedad, haga clic en el botón de puntos suspensivos junto a la **contenido** campo en la cuadrícula de propiedades o haga clic en el **definir...**  situado junto a la **contenido** etiqueta en el **recepción** superficie del Diseñador de actividad. Ambos muestran el **definición de contenido** cuadro de diálogo. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Utilice este cuadro, consulte la [cuadro de diálogo de definición de contenido](../workflow-designer/content-definition-dialog-box.md) tema.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propiedad en la cuadrícula de propiedades para abrir el **agregar inicializadores de correlación** cuadro de diálogo. [!INCLUDE[crabout](../test/includes/crabout_md.md)]uso de este cuadro, consulte la [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) tema.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, el valor predeterminado será:<br /><br /> **https://tempuri.org/ {espacio de nombres de contrato de servicio} / {nombre del contrato de servicio} / {nombre de la operación}.**|  
  
## <a name="see-also"></a>Vea también  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Recepción](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Enviar](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)