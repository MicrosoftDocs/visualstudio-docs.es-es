---
title: Diseñador de actividades Diseñador de flujo de trabajo-CorrelationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d65e481342f7b7e86b3ce073b7d6a15254ae72d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650583"
---
# <a name="correlationscope-activity-designer"></a>Diseñador de actividades CorrelationScope

El diseñador de actividades **CorrelationScope** se utiliza para crear y configurar una actividad <xref:System.ServiceModel.Activities.CorrelationScope> que proporciona administración implícita de actividades de mensajería secundarias mediante un objeto <xref:System.ServiceModel.Activities.CorrelationHandle>.

## <a name="the-correlationscope-activity"></a>La actividad CorrelationScope

La propiedad <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> especifica la clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para administrar las actividades de mensajería secundarias. Las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.Receive> que se incluyen en la propiedad <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> se configuran para utilizar la propiedad <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de la actividad <xref:System.ServiceModel.Activities.CorrelationScope> que sirve de contenedor para efectuar la correlación.

### <a name="use-the-correlationscope-activity-designer"></a>Usar el diseñador de actividades CorrelationScope

El diseñador de actividades **CorrelationScope** se puede encontrar en la categoría **Mensajería** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** en el lado izquierdo del diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** +**Alt** +**X**.

El diseñador de actividades **CorrelationScope** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo. Esto crea una actividad <xref:System.ServiceModel.Activities.CorrelationScope> con un valor **displayName** predeterminado de CorrelationScope. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **CorrelationScope** o en el cuadro **displayName** de la ventana **propiedades** .

Para especificar el <xref:System.ServiceModel.Activities.CorrelationHandle> que usan las actividades de mensajería secundarias, seleccione el botón de puntos suspensivos junto al campo **CorrelatesWith** en la ventana **propiedades** para mostrar el cuadro de diálogo **Editor de expresiones** . Esta propiedad también se puede establecer en la superficie del diseñador de actividades.

Las actividades dentro del ámbito de la correlación se especifican colocando sus diseñadores en el cuadro **cuerpo** dentro del diseñador **CorrelationScope** .

### <a name="the-correlationscope-properties"></a>Propiedades de CorrelationScope

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.CorrelationScope> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la ventana **propiedades** o en la superficie diseñador de flujo de trabajo y, a menudo, en ambos.

|Nombre de la propiedad|Requerido|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Especifica la propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para administrar las actividades de mensajería secundarias. Si no se establece esta propiedad, <xref:System.ServiceModel.Activities.CorrelationScope> crea una propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> implícita automáticamente.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Especifica las actividades dentro del ámbito de la correlación.|

## <a name="see-also"></a>Vea también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)