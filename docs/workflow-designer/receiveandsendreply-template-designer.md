---
title: Diseñador de plantillas Diseñador de flujo de trabajo ReceiveAndSendReply
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
ms.openlocfilehash: a816013f4eceb390a16e76a06814043aa0adaeb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650023"
---
# <a name="receiveandsendreply-template-designer"></a>Diseñador de plantillas ReceiveAndSendReply

La plantilla **ReceiveAndSendReply** se usa para crear un par de actividades preconfiguradas <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply>. Las actividades forman parte de una actividad <xref:System.Activities.Statements.Sequence> y se correlacionan como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el servidor.

## <a name="the-receiveandsendreply-template"></a>La plantilla ReceiveAndSendReply

La adición de una plantilla **ReceiveAndSendReply** hace tres cosas además de crear las actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> con una actividad <xref:System.Activities.Statements.Sequence>:

- Configura las propiedades <xref:System.ServiceModel.Activities.Receive.OperationName%2A> y <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Receive>.

- Enlaza la propiedad <xref:System.ServiceModel.Activities.SendReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.Receive> para la actividad <xref:System.ServiceModel.Activities.Send>.

- Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="use-the-receiveandsendreply-template-designer"></a>Usar el diseñador de plantillas ReceiveAndSendReply

Acceda al diseñador de actividades **ReceiveAndSendReply** en la categoría **Mensajería** del **cuadro de herramientas**. El diseñador de actividades **ReceiveAndSendReply** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo siempre que se coloquen normalmente las actividades. Al quitar el diseñador de actividad, se crea una actividad <xref:System.ServiceModel.Activities.Receive> que se puede configurar con el diseñador de actividades **send** y una <xref:System.ServiceModel.Activities.SendReply> correlacionada que se puede configurar con el diseñador SendReplyToReceive.

Para obtener más información sobre cómo usar el diseñador de **recepción** para configurar la actividad <xref:System.ServiceModel.Activities.Receive>, vea el [Diseñador de actividad Receive](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Propiedades SendReply

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.SendReply> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas se pueden editar en la superficie Diseñador de flujo de trabajo.

| Nombre de la propiedad | Requerido | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.SendReply>. El valor predeterminado es SendReplyToReceive.<br /><br /> Aunque el uso de un valor no predeterminado para el <xref:System.Activities.Activity.DisplayName%2A> descriptivo no es estrictamente necesario, es mejor usar este tipo de valor. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Referencia a la actividad <xref:System.ServiceModel.Activities.Receive> emparejada con esta actividad <xref:System.ServiceModel.Activities.SendReply>. Esta propiedad no debe ser **null**. Las actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> se usan juntas en el lado de servidor para crear un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no se puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> desde la que se creó la actividad <xref:System.ServiceModel.Activities.SendReply>. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad haciendo clic en el botón de puntos suspensivos situado junto al campo de **contenido** en la cuadrícula de propiedades, o haciendo clic en el botón **definir** situado junto a la etiqueta de **contenido** en la superficie del diseñador de actividad **Receive** . Ambos muestran el cuadro de diálogo **definición de contenido** . Para obtener más información acerca de cómo usar este cuadro, vea el tema del [cuadro de diálogo Definición de contenido](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la propiedad <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> de la cuadrícula de propiedades para abrir el cuadro de diálogo **Agregar inicializadores de correlación** . Para obtener más información sobre el uso de este cuadro, vea el tema del [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, su valor predeterminado es:<br /><br /> <strong>espacio de nombres del contrato de https://tempuri.org/{service } nombre del contrato/{nombre del} operación nombre}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Especifica si la instancia de flujo de trabajo se debe conservar antes de que se envíe el mensaje de respuesta. El valor predeterminado es **false**. |

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)