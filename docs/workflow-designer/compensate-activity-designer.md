---
title: 'Diseñador de flujo de trabajo: diseñador de actividades Compensate'
description: Obtenga información sobre el diseñador de actividades Compensate y cómo puede utilizar el diseñador de actividades Compensate para crear y configurar una actividad Compensate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 36ab20854adb952d098f71904cdd3cb092e27ac9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955689"
---
# <a name="compensate-activity-designer"></a>Diseñador de actividades Compensate

El diseñador de actividades **Compensate** se usa para crear y configurar una <xref:System.Activities.Statements.Compensate> actividad.

## <a name="the-compensate-activity"></a>Actividad Compensate

La actividad <xref:System.Activities.Statements.Compensate> invoca explícitamente a la propiedad <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> para una actividad que se incluye en <xref:System.Activities.Statements.CompensableActivity>. Si la actividad <xref:System.Activities.Statements.Compensate> no se utiliza dentro de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de una clase <xref:System.Activities.Statements.CompensableActivity>, debe especificar la propiedad <xref:System.Activities.Statements.Compensate.Target%2A>.

La clase <xref:System.Activities.Statements.CompensationToken> que especificó <xref:System.Activities.Statements.Compensate.Target%2A> proporciona un medio para confirmar o compensar explícitamente una clase <xref:System.Activities.Statements.CompensableActivity> una vez que la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> se haya completado correctamente.

### <a name="using-the-compensate-activity-designer"></a>Utilizar el diseñador de actividades Compensate

El diseñador de actividades **Compensate** se puede encontrar en la categoría **transacción** del **cuadro de herramientas**. Para abrir el **cuadro de herramientas**, seleccione la pestaña cuadro de **herramientas** en el lado izquierdo del diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** + **Alt** + **X**.

El diseñador de actividades **Compensate** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo dondequiera que se coloquen las actividades, como en una <xref:System.Activities.Statements.Sequence> . Al quitar el diseñador de actividad, se crea una <xref:System.Activities.Statements.Compensate> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de compensar. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **Compensate** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-compensate-properties"></a>Propiedades Compensate

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CancellationScope> y se describe cómo se utilizan en el diseñador. La <xref:System.Activities.Activity.DisplayName%2A> propiedad se puede editar en la cuadrícula de propiedades o en diseñador de flujo de trabajo superficie. Edite la <xref:System.Activities.Statements.Compensate.Target%2A> propiedad en la cuadrícula de propiedades.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Compensate>. El valor predeterminado es Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Especifica la clase <xref:System.Activities.InArgument%601> que contiene la clase <xref:System.Activities.Statements.CompensationToken> para esta actividad <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Vea también

- [Transacción](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Diseñador de actividad Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)