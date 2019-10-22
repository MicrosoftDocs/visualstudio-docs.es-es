---
title: Diseñador de plantillas Diseñador de flujo de trabajo SendAndReceiveReply
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
ms.openlocfilehash: d7c552e8bb94ed9035f25bdd40b7944458e61a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649960"
---
# <a name="sendandreceivereply-template-designer"></a>Diseñador de plantillas SendAndReceiveReply

La plantilla **SendAndReceiveReply** se usa para crear un par de actividades preconfiguradas <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply>. Las actividades forman parte de una actividad <xref:System.Activities.Statements.Sequence> y se correlacionan como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el cliente.

## <a name="the-sendandreceivereply-template"></a>La plantilla SendAndReceiveReply

Agregar la plantilla **SendAndReceiveReply** hace tres cosas además de crear las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> dentro de una actividad <xref:System.Activities.Statements.Sequence>:

- Configura las propiedades <xref:System.ServiceModel.Activities.Send.OperationName%2A> y <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Send>.

- Enlaza la propiedad <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.ReceiveReply> para la actividad <xref:System.ServiceModel.Activities.Send>.

- Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="use-the-sendandreceivereply-template-designer"></a>Usar el diseñador de plantillas SendAndReceiveReply

Acceda al diseñador de actividades **SendAndReceiveReply** en la categoría **Mensajería** del **cuadro de herramientas**. El diseñador de actividades **SendAndReceiveReply** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo siempre que se coloquen normalmente las actividades. Al quitar el diseñador de actividad, se crea una actividad <xref:System.ServiceModel.Activities.Send> que se puede configurar con el diseñador de actividades **send** y una <xref:System.ServiceModel.Activities.ReceiveReply> correlacionada que se puede configurar con el diseñador **ReceiveReplyForSend** .

Para obtener más información sobre cómo usar el diseñador de **envío** para configurar la actividad <xref:System.ServiceModel.Activities.Send>, consulte [envío](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propiedades ReceiveReply

En la tabla siguiente se muestran las propiedades de <xref:System.ServiceModel.Activities.ReceiveReply> y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas se pueden editar en la superficie de Diseñador de flujo de trabajo.

| Nombre de la propiedad | Requerido | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.ReceiveReply>. El valor predeterminado es ReceiveReplyForSend.<br /><br /> Aunque el uso de un valor no predeterminado para el <xref:System.Activities.Activity.DisplayName%2A> descriptivo no es estrictamente necesario, es mejor usar este tipo de valor. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Referencia a la actividad <xref:System.ServiceModel.Activities.Send> emparejada con esta actividad <xref:System.ServiceModel.Activities.ReceiveReply>. Esta propiedad no debe ser **null**. Las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> se usan juntas en el lado de cliente para crear un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no se puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> desde la que se creó la actividad <xref:System.ServiceModel.Activities.ReceiveReply>. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad haciendo clic en el botón de puntos suspensivos situado junto al campo de **contenido** en la cuadrícula de propiedades, o haciendo clic en el botón **definir** situado junto a la etiqueta de **contenido** en la superficie del diseñador de actividad **Receive** . Ambos muestran el cuadro de diálogo **definición de contenido** . Para obtener más información sobre cómo usar este cuadro, vea [Content Definition (cuadro de diálogo)](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la propiedad <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> de la cuadrícula de propiedades para abrir el cuadro de diálogo **Agregar inicializadores de correlación** . Para obtener más información sobre el uso de este cuadro, vea [Agregar CorrelationInitializers cuadro de diálogo](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, su valor predeterminado es:<br /><br /> <strong>https://tempuri.org/{service contrato espacio de nombres} nombre del contrato/{nombre del} operación nombre}.</strong> |

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)