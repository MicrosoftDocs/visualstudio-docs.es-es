---
title: Diseñador de actividades TransactedReceiveScope
description: En Diseñador de flujo de trabajo, obtenga información sobre cómo puede usar el diseñador de TransactedReceiveScope para crear y configurar una actividad TransactedReceiveScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eceb0776fd1cb5e850dab2b97ab6e7e56a684ebd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838027"
---
# <a name="transactedreceivescope-activity-designer"></a>Diseñador de actividades TransactedReceiveScope

El diseñador de **TransactedReceiveScope** se usa para crear y configurar una <xref:System.ServiceModel.Activities.TransactedReceiveScope> actividad.

## <a name="the-transactedreceivescope-activity"></a>Actividad TransactedReceiveScope

La actividad <xref:System.ServiceModel.Activities.TransactedReceiveScope> hace posible pasar una transacción a las transacciones del servidor que ha creado un flujo de trabajo o un distribuidor.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilizar el diseñador de actividades TransactedReceiveScope

Acceda al diseñador de actividades **TransactedReceiveScope** en la categoría **Mensajería** del **cuadro de herramientas**. El diseñador de actividades **TransactedReceiveScope** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo siempre que se coloquen normalmente las actividades. Esto crea una <xref:System.ServiceModel.Activities.TransactedReceiveScope> actividad con un valor **displayName** predeterminado de TransactedReceiveScope. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **TransactedReceiveScope** o en el cuadro **displayName** de la cuadrícula de propiedades.

El diseñador **TransactedReceiveScope** contiene cuadros de **solicitud** y **cuerpo** . Estos se utilizan para configurar la propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, que especifica una actividad <xref:System.ServiceModel.Activities.Receive> y una propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, la cual especifica alguna otra clase <xref:System.Activities.Activity>. La propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transacción. Posteriormente, la transacción se prepara para el ámbito de la propiedad <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> de forma que cualquier actividad en este ámbito se ejecute dentro de esta transacción.

### <a name="the-transactedreceivescope-properties"></a>Propiedades TransactedReceiveScope

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.TransactedReceiveScope> y se describe cómo se utilizan en el diseñador. Estas <xref:System.Activities.Activity.DisplayName%2A> propiedades se pueden editar en la cuadrícula de propiedades o en la superficie de diseñador de flujo de trabajo, pero las demás se deben editar en la superficie de diseño.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.TransactedReceiveScope>. El valor predeterminado es TransactedReceiveScope.<br /><br /> Aunque el nombre <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar un nombre para mostrar.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Quita una <xref:System.ServiceModel.Activities.Receive> actividad en el bloque de **solicitud** en la superficie del diseñador de actividad.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Coloca un <xref:System.Activities.Activity> en el bloque de **cuerpo** en la superficie del diseñador de actividad.|

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Aparecen](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Envío](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)