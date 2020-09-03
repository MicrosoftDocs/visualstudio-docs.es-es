---
title: Diseñador de actividades Diseñador de flujo de trabajo-CorrelationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 135acfbbaf9fdcbbf219fd50a504cf9262fe4d24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876104"
---
# <a name="correlationscope-activity-designer"></a>Diseñador de actividades CorrelationScope

El diseñador de actividades **CorrelationScope** se utiliza para crear y configurar una <xref:System.ServiceModel.Activities.CorrelationScope> actividad que proporciona administración implícita de actividades de mensajería secundarias mediante un <xref:System.ServiceModel.Activities.CorrelationHandle> objeto.

## <a name="the-correlationscope-activity"></a>La actividad CorrelationScope

La propiedad <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> especifica la clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para administrar las actividades de mensajería secundarias. Las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.Receive> que se incluyen en la propiedad <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> se configuran para utilizar la propiedad <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de la actividad <xref:System.ServiceModel.Activities.CorrelationScope> que sirve de contenedor para efectuar la correlación.

### <a name="use-the-correlationscope-activity-designer"></a>Usar el diseñador de actividades CorrelationScope

El diseñador de actividades **CorrelationScope** se puede encontrar en la categoría **Mensajería** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** en el lado izquierdo del diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** + **Alt** + **X**.

El diseñador de actividades **CorrelationScope** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo. Esto crea una <xref:System.ServiceModel.Activities.CorrelationScope> actividad con un valor **displayName** predeterminado de CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **CorrelationScope** o en el cuadro **displayName** de la ventana **propiedades** .

Para especificar el <xref:System.ServiceModel.Activities.CorrelationHandle> usado por las actividades de mensajería secundarias, seleccione el botón de puntos suspensivos junto al campo **CorrelatesWith** en la ventana **propiedades** para mostrar el cuadro de diálogo **Editor de expresiones** . Esta propiedad también se puede establecer en la superficie del diseñador de actividades.

Las actividades dentro del ámbito de la correlación se especifican colocando sus diseñadores en el cuadro **cuerpo** dentro del diseñador **CorrelationScope** .

### <a name="the-correlationscope-properties"></a>Propiedades de CorrelationScope

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.CorrelationScope> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la ventana **propiedades** o en la superficie diseñador de flujo de trabajo y, a menudo, en ambos.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Falso|Especifica la propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para administrar las actividades de mensajería secundarias. Si no se establece esta propiedad, <xref:System.ServiceModel.Activities.CorrelationScope> crea una propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> implícita automáticamente.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Falso|Especifica las actividades dentro del ámbito de la correlación.|

## <a name="see-also"></a>Consulte también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Aparecen](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)