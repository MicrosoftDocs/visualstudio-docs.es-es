---
title: Diseñador de plantillas de ReceiveAndSendReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e853967f73c99aa52958754e9f59f644c2f9497b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672543"
---
# <a name="receiveandsendreply-template-designer"></a>Diseñador de plantillas ReceiveAndSendReply
La plantilla **ReceiveAndSendReply** se usa para crear un par de actividades preconfiguradas <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> dentro de una actividad <xref:System.Activities.Statements.Sequence> que están correlacionadas como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el servidor.

## <a name="the-receiveandsendreply-template"></a>Plantilla ReceiveAndSendReply
 La adición de la plantilla **ReceiveAndSendReply** hace tres cosas además de crear las actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> con una actividad <xref:System.Activities.Statements.Sequence>:

1. Configura las propiedades <xref:System.ServiceModel.Activities.Receive.OperationName%2A> y <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Receive>.

2. Enlaza la propiedad <xref:System.ServiceModel.Activities.SendReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.Receive> para la actividad <xref:System.ServiceModel.Activities.Send>.

3. Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="using-the-receiveandsendreply-template-designer"></a>Utilizar el diseñador de plantillas ReceiveAndSendReply
 El diseñador de actividades **ReceiveAndSendReply** se puede encontrar en la categoría **Mensajería** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** en [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione barra de **herramientas** en la **vista** . o CTRL + ALT + X).

 El diseñador de actividades **ReceiveAndSendReply** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)] siempre que se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> que se puede configurar con el diseñador de actividades **send** y una <xref:System.ServiceModel.Activities.SendReply> correlacionada que se puede configurar con el diseñador SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)] usar el diseñador de **recepción** para configurar la actividad <xref:System.ServiceModel.Activities.Receive>, vea el tema [Receive](../workflow-designer/receive-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] el uso del diseñador **SendReplyToReceive** para configurar la actividad <xref:System.ServiceModel.Activities.SendReply>, consulte la sección siguiente.

### <a name="properties-of-sendreply"></a>Propiedades SendReply
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.SendReply> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                               Nombre de la propiedad                                | Obligatorio |                                                                                                                                                                                                                                                                                                                                                      Uso                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.SendReply>. El valor predeterminado es SendReplyToReceive.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Referencia a la actividad <xref:System.ServiceModel.Activities.Receive> emparejada con esta actividad <xref:System.ServiceModel.Activities.SendReply>. Esta propiedad no debe ser **null**. las actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> se usan juntas en el servidor para modelar un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> a partir de la cual se creó la actividad <xref:System.ServiceModel.Activities.SendReply>. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad haciendo clic en el botón de puntos suspensivos situado junto al campo de **contenido** en la cuadrícula de propiedades o haciendo clic en el botón **definir...** situado junto a la etiqueta de **contenido** en la superficie del diseñador de actividad **Receive** . Ambos muestran el cuadro de diálogo **definición de contenido** . [!INCLUDE[crabout](../includes/crabout-md.md)] cómo usar este cuadro, vea el tema del [cuadro de diálogo Definición de contenido](../workflow-designer/content-definition-dialog-box.md) .                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la propiedad <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> de la cuadrícula de propiedades para abrir el cuadro de diálogo **Agregar inicializadores de correlación** . [!INCLUDE[crabout](../includes/crabout-md.md)] usar este cuadro, vea el tema del [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, el valor predeterminado será:<br /><br /> <strong>espacio de nombres del contrato de https://tempuri.org/{service } nombre del contrato/{nombre del} operación nombre}</strong>                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Especifica si la instancia de flujo de trabajo se debe conservar antes de que se envíe el mensaje de respuesta. El valor predeterminado es **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Vea también
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Recepción](../workflow-designer/receive-activity-designer.md) [Envío](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)