---
title: Diseñador de flujo de trabajo - Diseñador de actividades TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a103b0db53ced447e16d269d747fa3355aeb00c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921216"
---
# <a name="transactedreceivescope-activity-designer"></a>Diseñador de actividades TransactedReceiveScope

El **TransactedReceiveScope** diseñador se utiliza para crear y configurar un <xref:System.ServiceModel.Activities.TransactedReceiveScope> actividad.

## <a name="the-transactedreceivescope-activity"></a>Actividad TransactedReceiveScope

La actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope> hace posible pasar una transacción a las transacciones del servidor que ha creado un flujo de trabajo o un distribuidor.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilizar el diseñador de actividades TransactedReceiveScope

Acceso a la **TransactedReceiveScope** Diseñador de actividad en el **mensajería** categoría de la **cuadro de herramientas**. El **TransactedReceiveScope** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades. Esto crea un <xref:System.ServiceModel.Activities.TransactedReceiveScope> actividad con un valor predeterminado **DisplayName** de TransactedReceiveScope. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **TransactedReceiveScope** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.

El **TransactedReceiveScope** diseñador contiene **solicitar** y **cuerpo** cuadros. Estos se utilizan para configurar la propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, que especifica una actividad <xref:System.ServiceModel.Activities.Receive> y una propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, la cual especifica alguna otra clase <xref:System.Activities.Activity>. La propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transacción. Posteriormente, la transacción se prepara para el ámbito de la propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> de forma que cualquier actividad en este ámbito se ejecute dentro de esta transacción.

### <a name="the-transactedreceivescope-properties"></a>Propiedades TransactedReceiveScope

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.TransactedReceiveScope> y se describe cómo se utilizan en el diseñador. Estos <xref:System.Activities.Activity.DisplayName%2A> propiedad se puede editar en cuadrícula de propiedades o en la superficie del Diseñador de flujo de trabajo, pero los otros se deben editar en la superficie de diseño.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.TransactedReceiveScope>. El valor predeterminado es TransactedReceiveScope.<br /><br /> Aunque el nombre <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar un nombre para mostrar.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Quita un <xref:System.ServiceModel.Activities.Receive> actividad en el **solicitar** bloque en la superficie del Diseñador de actividad.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Quita un <xref:System.Activities.Activity> en el **cuerpo** bloque en la superficie del Diseñador de actividad.|

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)