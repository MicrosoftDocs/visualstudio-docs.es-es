---
title: Diseñador de flujo de trabajo - Diseñador de plantillas SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 469e8ca3c325b04684e9481957c2e6bf9e14cffb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940419"
---
# <a name="sendandreceivereply-template-designer"></a>Diseñador de plantillas SendAndReceiveReply

El **SendAndReceiveReply** plantilla se usa para crear una pareja configurada previamente <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> actividades. Las actividades forman parte de un <xref:System.Activities.Statements.Sequence> actividad y se correlacionan como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el cliente.

## <a name="the-sendandreceivereply-template"></a>La plantilla SendAndReceiveReply

Agregar el **SendAndReceiveReply** plantilla hace tres cosas además de crear el <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> actividades dentro de un <xref:System.Activities.Statements.Sequence> actividad:

- Configura el <xref:System.ServiceModel.Activities.Send.OperationName%2A> y <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> propiedades de la <xref:System.ServiceModel.Activities.Send> actividad.

- Enlaza la propiedad <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.ReceiveReply> para la actividad <xref:System.ServiceModel.Activities.Send>.

- Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="use-the-sendandreceivereply-template-designer"></a>Use el Diseñador de plantillas SendAndReceiveReply

Acceso a la **SendAndReceiveReply** Diseñador de actividad en el **mensajería** categoría de la **cuadro de herramientas**. El **SendAndReceiveReply** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades. Al colocar el Diseñador de actividad se crea un <xref:System.ServiceModel.Activities.Send> actividad que se puede configurar con el **enviar** Diseñador de actividad y un correlacionadas <xref:System.ServiceModel.Activities.ReceiveReply> que pueden configurarse con la **ReceiveReplyForSend** diseñador.

Para obtener más información sobre el uso de la **enviar** diseñador para configurar el <xref:System.ServiceModel.Activities.Send> actividad, consulte [enviar](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propiedades ReceiveReply

La tabla siguiente muestra la <xref:System.ServiceModel.Activities.ReceiveReply> propiedades y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en cuadrícula de propiedades y algunas de ellas en la superficie del Diseñador de flujo de trabajo.


| Nombre de la propiedad | Obligatorio | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.ReceiveReply>. El valor predeterminado es ReceiveReplyForSend.<br /><br /> Aunque el uso de un valor no predeterminado para el sencillo <xref:System.Activities.Activity.DisplayName%2A> no es estrictamente necesaria, es mejor usar dicho valor. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Referencia a la actividad <xref:System.ServiceModel.Activities.Send> emparejada con esta actividad <xref:System.ServiceModel.Activities.ReceiveReply>. Esta propiedad no debe ser **null**. Las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply> se usan juntas en el lado de cliente para crear un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no se puede editar esta propiedad porque se enlaza automáticamente a la <xref:System.ServiceModel.Activities.Send> actividad desde el que creó el <xref:System.ServiceModel.Activities.ReceiveReply> actividad. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Editar esta propiedad, haga clic en el botón de puntos suspensivos junto a la **contenido** campo en la cuadrícula de propiedades, o haga clic en el **definir** situado junto a la **contenido** etiquetar en el **Recepción** superficie del Diseñador de actividad. Ambos muestran el **definición de contenido** cuadro de diálogo. Para obtener más información sobre cómo usar este cuadro, vea [cuadro de diálogo de definición de contenido](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propiedad en la cuadrícula de propiedades para abrir el **agregar inicializadores de correlación** cuadro de diálogo. Para obtener más información sobre el uso de este cuadro, vea [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si se establece explícitamente no, su valor predeterminado es:<br /><br /> <strong>https://tempuri.org/{service espacio de nombres de contrato} / {nombre de contrato de servicio} / {nombre de la operación}.</strong> |

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)