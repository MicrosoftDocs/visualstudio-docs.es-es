---
title: Diseñador de flujo de trabajo - ReceiveAndSendReply Template Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395298"
---
# <a name="receiveandsendreply-template-designer"></a>Diseñador de plantillas ReceiveAndSendReply

La plantilla **ReceiveAndSendReply** se usa para crear <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> un par de actividades y preconfiguradas. Las actividades forman <xref:System.Activities.Statements.Sequence> parte de una actividad y se correlacionan como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el servidor.

## <a name="the-receiveandsendreply-template"></a>La plantilla ReceiveAndSendReply

Agregar una plantilla **ReceiveAndSendReply** hace tres <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> cosas además de crear y actividades con una <xref:System.Activities.Statements.Sequence> actividad:

- Configura las <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> propiedades y <xref:System.ServiceModel.Activities.Receive> las de la actividad.

- Enlaza la propiedad <xref:System.ServiceModel.Activities.SendReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.Receive> para la actividad <xref:System.ServiceModel.Activities.Send>.

- Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="use-the-receiveandsendreply-template-designer"></a>Use el diseñador de plantillas ReceiveAndSendReply

Acceda al diseñador de actividades **ReceiveAndSendReply** en la categoría **Mensajería** del Cuadro de **herramientas**. El **ReceiveAndSendReply** diseñador de actividades se puede arrastrar desde el cuadro de **herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se colocan normalmente las actividades. Al quitar el <xref:System.ServiceModel.Activities.Receive> diseñador de actividades, se crea una actividad <xref:System.ServiceModel.Activities.SendReply> que se puede configurar con el diseñador de actividades **Send** y un correlacionado que se puede configurar con el diseñador SendReplyToReceive.

Para obtener más información sobre el <xref:System.ServiceModel.Activities.Receive> uso del diseñador de **recepción** para configurar la actividad, vea Diseñador de actividades de [recepción](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Propiedades SendReply

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.SendReply> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas se pueden editar en la superficie Diseñador de flujo de trabajo.

| Nombre de propiedad | Obligatorio | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.SendReply>. El valor predeterminado es SendReplyToReceive.<br /><br /> Aunque el uso de un valor <xref:System.Activities.Activity.DisplayName%2A> no predeterminado para el descriptivo no es estrictamente necesario, es mejor usar dicho valor. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Referencia a la actividad <xref:System.ServiceModel.Activities.Receive> emparejada con esta actividad <xref:System.ServiceModel.Activities.SendReply>. Esta propiedad no debe ser **null**. <xref:System.ServiceModel.Activities.Receive>y <xref:System.ServiceModel.Activities.SendReply> las actividades se utilizan juntas en el servidor para modelar un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no puede editar esta propiedad porque <xref:System.ServiceModel.Activities.Send> se enlaza automáticamente <xref:System.ServiceModel.Activities.SendReply> a la actividad desde la que creó la actividad. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad haciendo clic en el botón de puntos suspensivos situado junto al campo **Contenido** de la cuadrícula de propiedades o haciendo clic en el botón **Definir** situado junto a la etiqueta **Contenido** en la superficie del diseñador de actividades **de recepción.** Ambos muestran el cuadro de diálogo **Definición de contenido.** Para obtener más información acerca de cómo usar este cuadro, vea el cuadro de [diálogo Definición](../workflow-designer/content-definition-dialog-box.md) de contenido tema. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> botón de puntos suspensivos situado junto a la propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo Agregar inicializadores de **correlación.** Para obtener más información sobre el uso de este cuadro, vea el [tema Agregar correlationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) cuadro de diálogo. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, su valor predeterminado es:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Especifica si la instancia de flujo de trabajo se debe conservar antes de que se envíe el mensaje de respuesta. El valor predeterminado es **false**. |

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Recibir](../workflow-designer/receive-activity-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)