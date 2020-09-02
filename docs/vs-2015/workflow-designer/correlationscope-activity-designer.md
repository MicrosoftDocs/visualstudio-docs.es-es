---
title: Diseñador de actividades CorrelationScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ffcfd63d60ab6f085b5cb2a793e8bf17a50d8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656911"
---
# <a name="correlationscope-activity-designer"></a>Diseñador de actividades CorrelationScope
El diseñador de actividades **CorrelationScope** se utiliza para crear y configurar una <xref:System.ServiceModel.Activities.CorrelationScope> actividad que proporciona administración implícita de actividades de mensajería secundarias mediante un <xref:System.ServiceModel.Activities.CorrelationHandle> objeto.

## <a name="the-correlationscope-activity"></a>Actividad CorrelationScope
 La propiedad <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> especifica la clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para administrar las actividades de mensajería secundarias. Las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.Receive> que se incluyen en la propiedad <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> se configuran para utilizar la propiedad <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de la actividad <xref:System.ServiceModel.Activities.CorrelationScope> que sirve de contenedor para efectuar la correlación.

### <a name="using-the-correlationscope-activity-designer"></a>Utilizar el diseñador de actividades CorrelationScope
 El diseñador de actividades **CorrelationScope** se puede encontrar en la categoría **Mensajería** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** a la izquierda de [!INCLUDE[wfd2](../includes/wfd2-md.md)] . (de forma alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **CorrelationScope** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie. Esto crea una <xref:System.ServiceModel.Activities.CorrelationScope> actividad con un valor **displayName** predeterminado de CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **CorrelationScope** o en el cuadro **displayName** de la ventana **propiedades** .

 Para especificar el <xref:System.ServiceModel.Activities.CorrelationHandle> usado por las actividades de mensajería secundarias, haga clic en el botón de puntos suspensivos junto al campo **CorrelatesWith** en la ventana **propiedades** para mostrar el cuadro de diálogo **Editor de expresiones** . Esta propiedad también se puede establecer en la superficie del diseñador de actividades.

 Las actividades dentro del ámbito de la correlación se especifican colocando sus diseñadores en el cuadro **cuerpo** dentro del diseñador **CorrelationScope** .

### <a name="the-correlationscope-properties"></a>Propiedades CorrelationScope
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.CorrelationScope> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la ventana **propiedades** o en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie del diseñador y, a menudo, en ambos.

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Falso|Especifica la propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para administrar las actividades de mensajería secundarias. Si no se establece esta propiedad, <xref:System.ServiceModel.Activities.CorrelationScope> crea una propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> implícita automáticamente.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Falso|Especifica las actividades dentro del ámbito de la correlación.|

## <a name="see-also"></a>Consulte también
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)