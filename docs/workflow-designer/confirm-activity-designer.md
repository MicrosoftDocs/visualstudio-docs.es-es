---
title: Diseñador de flujo de trabajo-confirm (diseñador de actividades)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abd7fedd958072baf23b456f9897ab67c864991d
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876143"
---
# <a name="confirm-activity-designer"></a>Diseñador de actividades Confirm

El diseñador de actividades **CONFIRM** se usa para crear y configurar una <xref:System.Activities.Statements.Confirm> actividad.

## <a name="the-confirm-activity"></a>Actividad Confirm
 La actividad <xref:System.Activities.Statements.Confirm> invoca explícitamente a la propiedad <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> para una actividad que se incluye en <xref:System.Activities.Statements.CompensableActivity>. Si la actividad <xref:System.Activities.Statements.Confirm> no se utiliza dentro de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de una clase <xref:System.Activities.Statements.CompensableActivity>, debe especificar la propiedad <xref:System.Activities.Statements.Confirm.Target%2A>.

 La clase <xref:System.Activities.Statements.CompensationToken> que especificó <xref:System.Activities.Statements.Compensate.Target%2A> proporciona un medio para confirmar o compensar explícitamente una clase <xref:System.Activities.Statements.CompensableActivity> una vez que la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> se haya completado correctamente.

### <a name="using-the-confirm-activity-designer"></a>Utilizar el diseñador de actividades Confirm
 El diseñador de actividades **CONFIRM** se puede encontrar en la categoría **transacción** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** en el lado izquierdo del diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** + **Alt** + **X**.

 El diseñador de actividades **CONFIRM** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una actividad <xref:System.Activities.Statements.Confirm> con un valor <xref:System.Activities.Activity.DisplayName%2A> predeterminado de Confirm. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **CONFIRM** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-confirm-properties"></a>Propiedades Confirm
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Confirm> y se describe cómo se utilizan en el diseñador. La <xref:System.Activities.Activity.DisplayName%2A> propiedad se puede editar en la cuadrícula de propiedades o en diseñador de flujo de trabajo superficie, pero la <xref:System.Activities.Statements.Confirm.Target%2A> propiedad se debe editar en la cuadrícula de propiedades.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.CancellationScope>. El valor predeterminado es Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Especifica la clase <xref:System.Activities.InArgument%601> que contiene la clase <xref:System.Activities.Statements.CompensationToken> para esta actividad <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>Vea también

- [Transacción](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)