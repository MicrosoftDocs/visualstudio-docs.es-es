---
title: Diseñador de actividades Diseñador de flujo de trabajo-TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf5a52a6a806d72632bf31a7c73e41677e9ddaf9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654291"
---
# <a name="transactedreceivescope-activity-designer"></a>Diseñador de actividades TransactedReceiveScope

El diseñador **TransactedReceiveScope** se utiliza para crear y configurar una actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

## <a name="the-transactedreceivescope-activity"></a>Actividad TransactedReceiveScope

La actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope> hace posible pasar una transacción a las transacciones del servidor que ha creado un flujo de trabajo o un distribuidor.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilizar el diseñador de actividades TransactedReceiveScope

Acceda al diseñador de actividades **TransactedReceiveScope** en la categoría **Mensajería** del **cuadro de herramientas**. El diseñador de actividades **TransactedReceiveScope** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo siempre que se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope> con un valor **displayName** predeterminado de TransactedReceiveScope. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **TransactedReceiveScope** o en el cuadro **displayName** de la cuadrícula de propiedades.

El diseñador **TransactedReceiveScope** contiene cuadros de **solicitud** y **cuerpo** . Estos se utilizan para configurar la propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, que especifica una actividad <xref:System.ServiceModel.Activities.Receive> y una propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, la cual especifica alguna otra clase <xref:System.Activities.Activity>. La propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transacción. Posteriormente, la transacción se prepara para el ámbito de la propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> de forma que cualquier actividad en este ámbito se ejecute dentro de esta transacción.

### <a name="the-transactedreceivescope-properties"></a>Propiedades TransactedReceiveScope

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.TransactedReceiveScope> y se describe cómo se utilizan en el diseñador. Estas <xref:System.Activities.Activity.DisplayName%2A> propiedad se pueden editar en la cuadrícula de propiedades o en la superficie de Diseñador de flujo de trabajo, pero las demás se deben editar en la superficie de diseño.

|Nombre de la propiedad|Requerido|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.TransactedReceiveScope>. El valor predeterminado es TransactedReceiveScope.<br /><br /> Aunque el nombre <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar un nombre para mostrar.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Quita una actividad <xref:System.ServiceModel.Activities.Receive> en el bloque de **solicitud** en la superficie del diseñador de actividad.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Quita un <xref:System.Activities.Activity> en el bloque de **cuerpo** en la superficie del diseñador de actividad.|

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)