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
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395384"
---
# <a name="receiveandsendreply-template-designer"></a>Diseñador de plantillas ReceiveAndSendReply
La plantilla **ReceiveAndSendReply** se usa para crear un par de actividades y configuradas previamente <xref:System.ServiceModel.Activities.Receive> dentro de <xref:System.ServiceModel.Activities.SendReply> una <xref:System.Activities.Statements.Sequence> actividad que se correlacionan como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el servidor.

## <a name="the-receiveandsendreply-template"></a>Plantilla ReceiveAndSendReply
 La adición de la plantilla **ReceiveAndSendReply** hace tres cosas además de crear las <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> actividades y con una <xref:System.Activities.Statements.Sequence> actividad:

1. Configura las propiedades <xref:System.ServiceModel.Activities.Receive.OperationName%2A> y <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Receive>.

2. Enlaza la propiedad <xref:System.ServiceModel.Activities.SendReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.Receive> para la actividad <xref:System.ServiceModel.Activities.Send>.

3. Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="using-the-receiveandsendreply-template-designer"></a>Utilizar el diseñador de plantillas ReceiveAndSendReply
 El diseñador de actividades **ReceiveAndSendReply** se puede encontrar en la categoría **Mensajería** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** de. (de forma [!INCLUDE[wfd2](../includes/wfd2-md.md)] alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **ReceiveAndSendReply** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie de, donde se coloquen normalmente las actividades. Esto crea una <xref:System.ServiceModel.Activities.Receive> actividad que se puede configurar con el diseñador de actividades **send** y un correlacionado <xref:System.ServiceModel.Activities.SendReply> que se puede configurar con el diseñador SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)] usar el diseñador de **recepción** para configurar la <xref:System.ServiceModel.Activities.Receive> actividad, vea el tema [Receive](../workflow-designer/receive-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] Cómo usar el diseñador **SendReplyToReceive** para configurar la <xref:System.ServiceModel.Activities.SendReply> actividad, consulte la sección siguiente.

### <a name="properties-of-sendreply"></a>Propiedades SendReply
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.SendReply> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                               Nombre de propiedad                                | Obligatorio |                                                                                                                                                                                                                                                                                                                                                      Uso                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  Falso   |                                                                                                                                                                                            El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.SendReply>. El valor predeterminado es SendReplyToReceive.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   Verdadero   | Referencia a la actividad <xref:System.ServiceModel.Activities.Receive> emparejada con esta actividad <xref:System.ServiceModel.Activities.SendReply>. Esta propiedad no debe ser **null**. <xref:System.ServiceModel.Activities.Receive><xref:System.ServiceModel.Activities.SendReply>las actividades y se usan juntas en el servidor para modelar un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> a partir de la cual se creó la actividad <xref:System.ServiceModel.Activities.SendReply>. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  Falso   |                       Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad haciendo clic en el botón de puntos suspensivos situado junto al campo de **contenido** en la cuadrícula de propiedades o haciendo clic en el botón **definir...** situado junto a la etiqueta de **contenido** en la superficie del diseñador de actividad **Receive** . Ambos muestran el cuadro de diálogo **definición de contenido** . [!INCLUDE[crabout](../includes/crabout-md.md)] Cómo usar este cuadro, vea el tema del [cuadro de diálogo Definición de contenido](../workflow-designer/content-definition-dialog-box.md) .                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  Falso   |            Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo **Agregar inicializadores de correlación** . [!INCLUDE[crabout](../includes/crabout-md.md)] con este cuadro, vea el tema del [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  Falso   |                                                                                                                                                                                                                                              Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, el valor predeterminado será:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  Falso   |                                                                                                                                                                                                                                                                                          Especifica si la instancia de flujo de trabajo se debe conservar antes de que se envíe el mensaje de respuesta. El valor predeterminado es **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Consulte también
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)