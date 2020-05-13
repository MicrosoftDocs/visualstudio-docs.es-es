---
title: Diseñador de plantillas SendAndReceiveReply ? Microsoft Docs
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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395339"
---
# <a name="sendandreceivereply-template-designer"></a>Diseñador de plantillas SendAndReceiveReply
La plantilla **SendAndReceiveReply** se usa para crear <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> un par <xref:System.Activities.Statements.Sequence> de actividades preconfiguradas y dentro de una actividad que están correlacionadas como parte de un patrón de intercambio de mensajes de solicitud/respuesta en el cliente.

## <a name="the-sendandreceivereply-template"></a>Plantilla SendAndReceiveReply
 Agregar la plantilla **SendAndReceiveReply** hace <xref:System.ServiceModel.Activities.Send> tres <xref:System.ServiceModel.Activities.ReceiveReply> cosas <xref:System.Activities.Statements.Sequence> además de crear y actividades dentro de una actividad:

1. Configura las propiedades <xref:System.ServiceModel.Activities.Send.OperationName%2A> y <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de la actividad <xref:System.ServiceModel.Activities.Send>.

2. Enlaza la propiedad <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de la actividad <xref:System.ServiceModel.Activities.ReceiveReply> para la actividad <xref:System.ServiceModel.Activities.Send>.

3. Crea una clase <xref:System.ServiceModel.Activities.CorrelationHandle> como una variable de la actividad primaria.

### <a name="using-the-sendandreceivereply-template-designer"></a>Utilizar el diseñador de plantillas SendAndReceiveReply
 El Diseñador de actividades **SendAndReceiveReply** se puede encontrar en la categoría **Mensajería** del [!INCLUDE[wfd2](../includes/wfd2-md.md)] Cuadro de **herramientas**, a la que se tiene acceso haciendo clic en la pestaña **Cuadro** de herramientas (Alternativamente, seleccione Barra de **herramientas** en el menú **Ver** o CTRL+ALT+X.)

 El Diseñador de actividades **SendAndReceiveReply** se puede arrastrar [!INCLUDE[wfd2](../includes/wfd2-md.md)] desde el cuadro de **herramientas** y colocar en la superficie donde se suelen colocar las actividades. Esto crea <xref:System.ServiceModel.Activities.Send> una actividad que se puede configurar con <xref:System.ServiceModel.Activities.ReceiveReply> el diseñador de actividad **Send** y un correlated que se puede configurar con el **ReceiveReplyForSend** diseñador.

 [!INCLUDE[crabout](../includes/crabout-md.md)]mediante el diseñador de <xref:System.ServiceModel.Activities.Send> **envíos** para configurar la actividad, vea el tema [Enviar.](../workflow-designer/send-activity-designer.md)

 [!INCLUDE[crabout](../includes/crabout-md.md)]mediante el **ReceiveReplyForSend** diseñador <xref:System.ServiceModel.Activities.ReceiveReply> para configurar la actividad, vea la sección siguiente.

### <a name="properties-of-receivereply"></a>Propiedades ReceiveReply
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.ReceiveReply> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                                 Nombre de propiedad                                 | Obligatorio |                                                                                                                                                                                                                                                                                                                                                        Uso                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.ReceiveReply>. El valor predeterminado es ReceiveReplyForSend.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Referencia a la actividad <xref:System.ServiceModel.Activities.Send> emparejada con esta actividad <xref:System.ServiceModel.Activities.ReceiveReply>. Esta propiedad no debe ser **null**. <xref:System.ServiceModel.Activities.Send>y <xref:System.ServiceModel.Activities.ReceiveReply> las actividades se utilizan juntas en el cliente para modelar un patrón de mensajería de solicitud/respuesta. Esta propiedad especifica qué actividad <xref:System.ServiceModel.Activities.Send> se usará para formar la pareja. En el diseñador, no puede editar esta propiedad porque se enlaza automáticamente a la actividad <xref:System.ServiceModel.Activities.Send> a partir de la cual se creó la actividad <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad haciendo clic en el botón de elipse junto al campo **Contenido** de la cuadrícula de propiedades o haciendo clic en **Definir...** botón situado junto a la etiqueta **Contenido** en la superficie del diseñador de actividades **de recepción.** Ambos muestran el cuadro de diálogo **Definición de contenido.** [!INCLUDE[crabout](../includes/crabout-md.md)]cómo usar este cuadro, vea el cuadro de [diálogo Definición](../workflow-designer/content-definition-dialog-box.md) de contenido tema.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> botón de puntos suspensivos situado junto a la propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo Agregar inicializadores de **correlación.** [!INCLUDE[crabout](../includes/crabout-md.md)]con este cuadro, vea el tema Agregar cuadro de [diálogo CorrelationInitializers.](../workflow-designer/add-correlationinitializers-dialog-box.md)               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, el valor predeterminado será:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Vea también
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)