---
title: Diseñador de plantillas Diseñador de flujo de trabajo SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17512337b58fb394352ccaab153ca72badbb4652
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875909"
---
# <a name="sendandreceivereply-template-designer"></a>Diseñador de plantillas SendAndReceiveReply

La plantilla **SendAndReceiveReply** se usa para crear un par de actividades y configuradas previamente <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> . Las actividades forman parte de una <xref:System.Activities.Statements.Sequence> actividad y se correlacionan como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el cliente.

## <a name="the-sendandreceivereply-template"></a>La plantilla SendAndReceiveReply

Agregar la plantilla **SendAndReceiveReply** hace tres cosas además de crear <xref:System.ServiceModel.Activities.Send> las <xref:System.ServiceModel.Activities.ReceiveReply> actividades y dentro de una <xref:System.Activities.Statements.Sequence> actividad:

- Configura las <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> propiedades y de la <xref:System.ServiceModel.Activities.Send> actividad.

- Enlaza la propiedad <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.ReceiveReply> para la actividad <xref:System.ServiceModel.Activities.Send>.

- Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="use-the-sendandreceivereply-template-designer"></a>Usar el diseñador de plantillas SendAndReceiveReply

Acceda al diseñador de actividades **SendAndReceiveReply** en la categoría **Mensajería** del **cuadro de herramientas**. El diseñador de actividades **SendAndReceiveReply** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo siempre que se coloquen normalmente las actividades. Al quitar el diseñador de actividad <xref:System.ServiceModel.Activities.Send> , se crea una actividad que se puede configurar con el diseñador de actividades **send** y un correlacionado <xref:System.ServiceModel.Activities.ReceiveReply> que se puede configurar con el diseñador **ReceiveReplyForSend** .

Para obtener más información sobre cómo usar el diseñador de **envío** para configurar la <xref:System.ServiceModel.Activities.Send> actividad, vea [envío](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propiedades ReceiveReply

En la tabla siguiente se muestran las <xref:System.ServiceModel.Activities.ReceiveReply> propiedades y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas se pueden editar en la superficie de Diseñador de flujo de trabajo.

| Nombre de propiedad | Obligatorio | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.ReceiveReply>. El valor predeterminado es ReceiveReplyForSend.<br /><br /> Aunque no es estrictamente necesario el uso de un valor no predeterminado para el descriptivo <xref:System.Activities.Activity.DisplayName%2A> , es mejor usar este tipo de valor. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Referencia a la actividad <xref:System.ServiceModel.Activities.Send> emparejada con esta actividad <xref:System.ServiceModel.Activities.ReceiveReply>. Esta propiedad no debe ser **null**. <xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply>las actividades y se usan juntas en el cliente para modelar un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no se puede editar esta propiedad porque se enlaza automáticamente a la <xref:System.ServiceModel.Activities.Send> actividad desde la que se creó la <xref:System.ServiceModel.Activities.ReceiveReply> actividad. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad haciendo clic en el botón de puntos suspensivos situado junto al campo de **contenido** en la cuadrícula de propiedades, o haciendo clic en el botón **definir** situado junto a la etiqueta de **contenido** en la superficie del diseñador de actividad **Receive** . Ambos muestran el cuadro de diálogo **definición de contenido** . Para obtener más información sobre cómo usar este cuadro, vea [Content Definition (cuadro de diálogo)](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo **Agregar inicializadores de correlación** . Para obtener más información sobre el uso de este cuadro, vea [Agregar CorrelationInitializers cuadro de diálogo](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, su valor predeterminado es:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Aparecen](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)