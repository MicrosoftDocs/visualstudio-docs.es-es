---
title: Diseñador de flujo de trabajo - Diseñador de plantillas SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2067ee92883d0c4ad3003f23032a88f5da3fa710
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395245"
---
# <a name="sendandreceivereply-template-designer"></a>Diseñador de plantillas SendAndReceiveReply

La plantilla **SendAndReceiveReply** se usa para crear <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> un par de actividades y preconfiguradas. Las actividades forman <xref:System.Activities.Statements.Sequence> parte de una actividad y se correlacionan como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el cliente.

## <a name="the-sendandreceivereply-template"></a>La plantilla SendAndReceiveReply

Agregar la plantilla **SendAndReceiveReply** hace tres <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> cosas además de crear y actividades dentro de una <xref:System.Activities.Statements.Sequence> actividad:

- Configura las <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> propiedades y <xref:System.ServiceModel.Activities.Send> las de la actividad.

- Enlaza la propiedad <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.ReceiveReply> para la actividad <xref:System.ServiceModel.Activities.Send>.

- Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="use-the-sendandreceivereply-template-designer"></a>Use el Diseñador de plantillas SendAndReceiveReply

Acceda al diseñador de actividades **SendAndReceiveReply** en la categoría **Mensajería** del Cuadro de **herramientas**. El Diseñador de actividades **SendAndReceiveReply** se puede arrastrar desde el cuadro de **herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se suelen colocar las actividades. Al quitar el <xref:System.ServiceModel.Activities.Send> diseñador de actividades, se crea una actividad <xref:System.ServiceModel.Activities.ReceiveReply> que se puede configurar con el diseñador de actividades **Send** y un correlacionado que se puede configurar con el diseñador **ReceiveReplyForSend.**

Para obtener más información sobre el <xref:System.ServiceModel.Activities.Send> uso del diseñador de **envíos** para configurar la actividad, vea [Enviar](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propiedades ReceiveReply

En la tabla <xref:System.ServiceModel.Activities.ReceiveReply> siguiente se muestran las propiedades y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas se pueden editar en la superficie Del Diseñador de flujo de trabajo.

| Nombre de propiedad | Obligatorio | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.ReceiveReply>. El valor predeterminado es ReceiveReplyForSend.<br /><br /> Aunque el uso de un valor <xref:System.Activities.Activity.DisplayName%2A> no predeterminado para el descriptivo no es estrictamente necesario, es mejor usar dicho valor. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Referencia a la actividad <xref:System.ServiceModel.Activities.Send> emparejada con esta actividad <xref:System.ServiceModel.Activities.ReceiveReply>. Esta propiedad no debe ser **null**. <xref:System.ServiceModel.Activities.Send>y <xref:System.ServiceModel.Activities.ReceiveReply> las actividades se utilizan juntas en el cliente para modelar un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no puede editar esta propiedad porque <xref:System.ServiceModel.Activities.Send> se enlaza automáticamente <xref:System.ServiceModel.Activities.ReceiveReply> a la actividad desde la que creó la actividad. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad haciendo clic en el botón de puntos suspensivos situado junto al campo **Contenido** de la cuadrícula de propiedades o haciendo clic en el botón **Definir** situado junto a la etiqueta **Contenido** en la superficie del diseñador de actividades **de recepción.** Ambos muestran el cuadro de diálogo **Definición de contenido.** Para obtener más información sobre cómo utilizar este cuadro, vea Cuadro de [diálogo Definición](../workflow-designer/content-definition-dialog-box.md)de contenido . |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> botón de puntos suspensivos situado junto a la propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo Agregar inicializadores de **correlación.** Para obtener más información sobre el uso de este cuadro, vea [Agregar correlaciónInitializers Cuadro](../workflow-designer/add-correlationinitializers-dialog-box.md)de diálogo . |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, su valor predeterminado es:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Recibir](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)