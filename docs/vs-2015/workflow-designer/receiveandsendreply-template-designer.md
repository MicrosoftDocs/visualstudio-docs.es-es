---
title: Diseñador de plantillas ReceiveAndSendReply ? Microsoft Docs
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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395384"
---
# <a name="receiveandsendreply-template-designer"></a>Diseñador de plantillas ReceiveAndSendReply
La plantilla **ReceiveAndSendReply** se usa para crear <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> un par <xref:System.Activities.Statements.Sequence> de actividades preconfiguradas y dentro de una actividad que están correlacionadas como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el servidor.

## <a name="the-receiveandsendreply-template"></a>Plantilla ReceiveAndSendReply
 Agregar la plantilla **ReceiveAndSendReply** hace <xref:System.ServiceModel.Activities.Receive> tres <xref:System.ServiceModel.Activities.SendReply> cosas <xref:System.Activities.Statements.Sequence> además de crear y actividades con una actividad:

1. Configura las propiedades <xref:System.ServiceModel.Activities.Receive.OperationName%2A> y <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Receive>.

2. Enlaza la propiedad <xref:System.ServiceModel.Activities.SendReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.Receive> para la actividad <xref:System.ServiceModel.Activities.Send>.

3. Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="using-the-receiveandsendreply-template-designer"></a>Utilizar el diseñador de plantillas ReceiveAndSendReply
 El Diseñador de actividades **ReceiveAndSendReply** se puede encontrar en la categoría **Mensajería** del [!INCLUDE[wfd2](../includes/wfd2-md.md)] Cuadro de **herramientas**, a la que se tiene acceso haciendo clic en la pestaña **Cuadro** de herramientas (Alternativamente, seleccione Barra de **herramientas** en el menú **Ver** o CTRL+ALT+X.)

 El **ReceiveAndSendReply** diseñador de actividades se puede arrastrar [!INCLUDE[wfd2](../includes/wfd2-md.md)] desde el cuadro de **herramientas** y colocar en la superficie donde se colocan normalmente las actividades. Esto crea <xref:System.ServiceModel.Activities.Receive> una actividad que se puede configurar con <xref:System.ServiceModel.Activities.SendReply> el diseñador de actividad **Send** y un correlated que se puede configurar con el Diseñador SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)]usar el diseñador de <xref:System.ServiceModel.Activities.Receive> **recepción** para configurar la actividad, vea el tema [Recibir.](../workflow-designer/receive-activity-designer.md)

 [!INCLUDE[crabout](../includes/crabout-md.md)]mediante el diseñador **SendReplyToReceive** para configurar la <xref:System.ServiceModel.Activities.SendReply> actividad, vea la sección siguiente.

### <a name="properties-of-sendreply"></a>Propiedades SendReply
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.SendReply> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                               Nombre de propiedad                                | Obligatorio |                                                                                                                                                                                                                                                                                                                                                      Uso                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.SendReply>. El valor predeterminado es SendReplyToReceive.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Referencia a la actividad <xref:System.ServiceModel.Activities.Receive> emparejada con esta actividad <xref:System.ServiceModel.Activities.SendReply>. Esta propiedad no debe ser **null**. <xref:System.ServiceModel.Activities.Receive>y <xref:System.ServiceModel.Activities.SendReply> las actividades se utilizan juntas en el servidor para modelar un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> a partir de la cual se creó la actividad <xref:System.ServiceModel.Activities.SendReply>. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad haciendo clic en el botón de elipse junto al campo **Contenido** de la cuadrícula de propiedades o haciendo clic en **Definir...** botón situado junto a la etiqueta **Contenido** en la superficie del diseñador de actividades **de recepción.** Ambos muestran el cuadro de diálogo **Definición de contenido.** [!INCLUDE[crabout](../includes/crabout-md.md)]cómo usar este cuadro, vea el cuadro de [diálogo Definición](../workflow-designer/content-definition-dialog-box.md) de contenido tema.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> botón de puntos suspensivos situado junto a la propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo Agregar inicializadores de **correlación.** [!INCLUDE[crabout](../includes/crabout-md.md)]con este cuadro, vea el tema Agregar cuadro de [diálogo CorrelationInitializers.](../workflow-designer/add-correlationinitializers-dialog-box.md)            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, el valor predeterminado será:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Especifica si la instancia de flujo de trabajo se debe conservar antes de que se envíe el mensaje de respuesta. El valor predeterminado es **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Vea también
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)