---
title: Diseñador de plantillas ReceiveAndSendReply | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81edeb04abacedb81ad52da17369759ba9f1f222
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="receiveandsendreply-template-designer"></a>Diseñador de plantillas ReceiveAndSendReply

El **ReceiveAndSendReply** plantilla se usa para crear un par de configuradas previamente <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> actividades dentro de un <xref:System.Activities.Statements.Sequence> actividad que se correlacionan como parte de un intercambio de mensajes de solicitud/respuesta patrón en el servidor.

## <a name="the-receiveandsendreply-template"></a>Plantilla ReceiveAndSendReply
 Agregar **ReceiveAndSendReply** plantilla hace tres cosas además de crear el <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> actividades con un <xref:System.Activities.Statements.Sequence> actividad:

1.  Configura las propiedades <xref:System.ServiceModel.Activities.Receive.OperationName%2A> y <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Receive>.

2.  Enlaza la propiedad <xref:System.ServiceModel.Activities.SendReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.Receive> para la actividad <xref:System.ServiceModel.Activities.Send>.

3.  Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="using-the-receiveandsendreply-template-designer"></a>Utilizar el diseñador de plantillas ReceiveAndSendReply
 El **ReceiveAndSendReply** Diseñador de actividad puede encontrarse en el **mensajería** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en la **cuadro de herramientas**  ficha [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El **ReceiveAndSendReply** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades. Esto crea una <xref:System.ServiceModel.Activities.Receive> actividad que se pueden configurar con el **enviar** Diseñador de actividad y un correlacionados <xref:System.ServiceModel.Activities.SendReply> que se puede configurar con el diseñador SendReplyToReceive.

 Para obtener más información sobre el uso de la **recepción** diseñador para configurar el <xref:System.ServiceModel.Activities.Receive> actividad, consulte la [recepción](../workflow-designer/receive-activity-designer.md) tema.

 Para obtener más información sobre el uso de la **SendReplyToReceive** diseñador para configurar la <xref:System.ServiceModel.Activities.SendReply> actividad, consulte la sección siguiente.

### <a name="properties-of-sendreply"></a>Propiedades SendReply
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.SendReply> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.SendReply>. El valor predeterminado es SendReplyToReceive.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.|
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Referencia a la actividad <xref:System.ServiceModel.Activities.Receive> emparejada con esta actividad <xref:System.ServiceModel.Activities.SendReply>. Esta propiedad no debe ser **null**. Las actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> se usan juntas en el lado de servidor para crear un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> a partir de la cual se creó la actividad <xref:System.ServiceModel.Activities.SendReply>.|
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Editar esta propiedad, haga clic en el botón de puntos suspensivos junto a la **contenido** campo en la cuadrícula de propiedades o haga clic en el **definir...**  situado junto a la **contenido** etiqueta en el **recepción** superficie del Diseñador de actividad. Ambos muestran el **definición de contenido** cuadro de diálogo. Para obtener más información acerca de cómo usar este cuadro, consulte la [cuadro de diálogo de definición de contenido](../workflow-designer/content-definition-dialog-box.md) tema.|
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> propiedad en la cuadrícula de propiedades para abrir el **agregar inicializadores de correlación** cuadro de diálogo. Para obtener más información sobre el uso de este cuadro, consulte la [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) tema.|
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, el valor predeterminado será:<br /><br /> **https://tempuri.org/{service espacio de nombres de contrato} / {nombre del contrato de servicio} / {nombre de la operación}**|
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Especifica si la instancia de flujo de trabajo se debe conservar antes de que se envíe el mensaje de respuesta. El valor predeterminado es **false**.|

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Recepción](../workflow-designer/receive-activity-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)