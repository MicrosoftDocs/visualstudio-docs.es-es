---
title: Diseñador de flujo de trabajo - Diseñador de plantillas ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c6b5a12b37509e6e5113c704ef2c3ff931ea32e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886414"
---
# <a name="receiveandsendreply-template-designer"></a>Diseñador de plantillas ReceiveAndSendReply

El **ReceiveAndSendReply** plantilla se usa para crear una pareja configurada previamente <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> actividades. Las actividades forman parte de un <xref:System.Activities.Statements.Sequence> actividad y se correlacionan como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el servidor.

## <a name="the-receiveandsendreply-template"></a>La plantilla ReceiveAndSendReply

Agregar un **ReceiveAndSendReply** plantilla hace tres cosas además de crear el <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> actividades con un <xref:System.Activities.Statements.Sequence> actividad:

- Configura el <xref:System.ServiceModel.Activities.Receive.OperationName%2A> y <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> propiedades de la <xref:System.ServiceModel.Activities.Receive> actividad.

- Enlaza la propiedad <xref:System.ServiceModel.Activities.SendReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.Receive> para la actividad <xref:System.ServiceModel.Activities.Send>.

- Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="use-the-receiveandsendreply-template-designer"></a>Utilice el Diseñador de plantillas ReceiveAndSendReply

Acceso a la **ReceiveAndSendReply** Diseñador de actividad en el **mensajería** categoría de la **cuadro de herramientas**. El **ReceiveAndSendReply** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades. Al colocar el Diseñador de actividad se crea un <xref:System.ServiceModel.Activities.Receive> actividad que se puede configurar con el **enviar** Diseñador de actividad y un correlacionadas <xref:System.ServiceModel.Activities.SendReply> que pueden configurarse con el diseñador SendReplyToReceive.

Para obtener más información sobre el uso de la **recepción** diseñador para configurar el <xref:System.ServiceModel.Activities.Receive> actividad, consulte [Diseñador de actividad de recepción](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Propiedades SendReply

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.SendReply> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del Diseñador de flujo de trabajo.


| Nombre de la propiedad | Obligatorio | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.SendReply>. El valor predeterminado es SendReplyToReceive.<br /><br /> Aunque el uso de un valor no predeterminado para el sencillo <xref:System.Activities.Activity.DisplayName%2A> no es estrictamente necesaria, es mejor usar dicho valor. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Referencia a la actividad <xref:System.ServiceModel.Activities.Receive> emparejada con esta actividad <xref:System.ServiceModel.Activities.SendReply>. Esta propiedad no debe ser **null**. Las actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> se usan juntas en el lado de servidor para crear un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no se puede editar esta propiedad porque se enlaza automáticamente a la <xref:System.ServiceModel.Activities.Send> actividad desde el que creó el <xref:System.ServiceModel.Activities.SendReply> actividad. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Editar esta propiedad, haga clic en el botón de puntos suspensivos junto a la **contenido** campo en la cuadrícula de propiedades, o haga clic en el **definir** situado junto a la **contenido** etiqueta en el  **Recibir** superficie del Diseñador de actividad. Ambos muestran el **definición de contenido** cuadro de diálogo. Para obtener más información sobre cómo usar este cuadro, vea el [cuadro de diálogo de definición de contenido](../workflow-designer/content-definition-dialog-box.md) tema. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> propiedad en la cuadrícula de propiedades para abrir el **agregar inicializadores de correlación** cuadro de diálogo. Para obtener más información sobre el uso de este cuadro, vea el [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) tema. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si se establece explícitamente no, su valor predeterminado es:<br /><br /> <strong>https://tempuri.org/{service espacio de nombres de contrato} / {nombre de contrato de servicio} / {nombre de la operación}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Especifica si la instancia de flujo de trabajo se debe conservar antes de que se envíe el mensaje de respuesta. El valor predeterminado es **false**. |

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)