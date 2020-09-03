---
title: Diseñador de plantillas de SendAndReceiveReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395339"
---
# <a name="sendandreceivereply-template-designer"></a>Diseñador de plantillas SendAndReceiveReply
La plantilla **SendAndReceiveReply** se usa para crear un par de actividades y configuradas previamente <xref:System.ServiceModel.Activities.Send> dentro de <xref:System.ServiceModel.Activities.ReceiveReply> una <xref:System.Activities.Statements.Sequence> actividad que se correlacionan como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el cliente.

## <a name="the-sendandreceivereply-template"></a>Plantilla SendAndReceiveReply
 La adición de la plantilla **SendAndReceiveReply** hace tres cosas además de la creación de las <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> actividades y dentro de una <xref:System.Activities.Statements.Sequence> actividad:

1. Configura las propiedades <xref:System.ServiceModel.Activities.Send.OperationName%2A> y <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Send>.

2. Enlaza la propiedad <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.ReceiveReply> para la actividad <xref:System.ServiceModel.Activities.Send>.

3. Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="using-the-sendandreceivereply-template-designer"></a>Utilizar el diseñador de plantillas SendAndReceiveReply
 El diseñador de actividades **SendAndReceiveReply** se puede encontrar en la categoría **Mensajería** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** de. (de forma [!INCLUDE[wfd2](../includes/wfd2-md.md)] alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **SendAndReceiveReply** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie de, donde se coloquen normalmente las actividades. Esto crea una <xref:System.ServiceModel.Activities.Send> actividad que se puede configurar con el diseñador de actividades **send** y un correlacionado <xref:System.ServiceModel.Activities.ReceiveReply> que se puede configurar con el diseñador **ReceiveReplyForSend** .

 [!INCLUDE[crabout](../includes/crabout-md.md)] usar el diseñador de **envío** para configurar la <xref:System.ServiceModel.Activities.Send> actividad, vea el tema [envío](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] Cómo usar el diseñador **ReceiveReplyForSend** para configurar la <xref:System.ServiceModel.Activities.ReceiveReply> actividad, consulte la sección siguiente.

### <a name="properties-of-receivereply"></a>Propiedades ReceiveReply
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.ReceiveReply> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                                 Nombre de propiedad                                 | Obligatorio |                                                                                                                                                                                                                                                                                                                                                        Uso                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.ReceiveReply>. El valor predeterminado es ReceiveReplyForSend.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Referencia a la actividad <xref:System.ServiceModel.Activities.Send> emparejada con esta actividad <xref:System.ServiceModel.Activities.ReceiveReply>. Esta propiedad no debe ser **null**. <xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply>las actividades y se usan juntas en el cliente para modelar un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> a partir de la cual se creó la actividad <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad haciendo clic en el botón de puntos suspensivos situado junto al campo de **contenido** en la cuadrícula de propiedades o haciendo clic en el botón **definir...** situado junto a la etiqueta de **contenido** en la superficie del diseñador de actividad **Receive** . Ambos muestran el cuadro de diálogo **definición de contenido** . [!INCLUDE[crabout](../includes/crabout-md.md)] Cómo usar este cuadro, vea el tema del [cuadro de diálogo Definición de contenido](../workflow-designer/content-definition-dialog-box.md) .                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo **Agregar inicializadores de correlación** . [!INCLUDE[crabout](../includes/crabout-md.md)] con este cuadro, vea el tema del [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, el valor predeterminado será:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Consulte también
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)