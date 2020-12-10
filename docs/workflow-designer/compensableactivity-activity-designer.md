---
title: Diseñador de actividad CompensableActivity Activity
description: Obtenga información sobre cómo puede usar el diseñador de actividades CompensableActivity en Diseñador de flujo de trabajo para crear y configurar una actividad CompensableActivity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d05809b1e370fee2505470be1c06366f76bf9ca
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996232"
---
# <a name="compensableactivity-activity-designer"></a>Diseñador de actividad CompensableActivity Activity

El diseñador de actividades **CompensableActivity** se utiliza para crear y configurar una <xref:System.Activities.Statements.CompensableActivity> actividad.

## <a name="the-compensableactivity-activity"></a>La actividad CompensableActivity
 La clase <xref:System.Activities.Statements.CompensableActivity> define una unidad de trabajo que se puede confirmar o compensar después de que se haya completado correctamente.

### <a name="using-the-compensableactivity-activity-designer"></a>Usar el diseñador de actividad CompensableActivity
 El diseñador de actividades **CompensableActivity** se puede encontrar en la categoría **transacción** del **cuadro de herramientas**. Para abrir el **cuadro de herramientas**, seleccione la pestaña cuadro de **herramientas** en el lado izquierdo del diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** + **Alt** + **X**.

 El diseñador de actividades **CompensableActivity** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo. Podría quitar el diseñador de actividad dentro de un <xref:System.Activities.Statements.Sequence> . Al quitar el diseñador de actividad, se crea una <xref:System.Activities.Statements.CompensableActivity> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de CompensableActivity. Edite el <xref:System.Activities.Activity.DisplayName%2A> valor en el encabezado del diseñador de actividades **CompensableActivity** . También se puede editar en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-compensableactivity-properties"></a>Las propiedades de CompensableActivity
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CompensableActivity> y se describe cómo se utilizan en el diseñador. La <xref:System.Activities.Activity.DisplayName%2A> <xref:System.Activities.Activity%601.Result%2A> propiedad y se puede editar en la cuadrícula de propiedades, pero las demás propiedades se deben editar en la superficie diseñador de flujo de trabajo.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.CompensableActivity>. El valor predeterminado es CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Especifica el valor devuelto de la clase <xref:System.Activities.Statements.CompensableActivity>. Esta propiedad se debe editar en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Verdadero|Especifica la actividad para la que se proporciona la lógica de compensación, cancelación y confirmación. Para agregar la <xref:System.Activities.Statements.CompensableActivity.Body%2A> actividad, coloque una actividad del cuadro de **herramientas** en el cuadro **Body** del diseñador de actividades **CompensableActivity** . Agregue el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Falso|Especifica la actividad que se ejecuta cuando hay una cancelación. Para agregar la actividad, coloque su diseñador desde el cuadro de **herramientas** en el cuadro **CancellationHandler** del diseñador de actividad **CompensableActivity** . Agregue el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Falso|Especifica la actividad que se va a ejecutar al realizar la compensación para la actividad de la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Este controlador se puede invocar explícitamente mediante la actividad <xref:System.Activities.Statements.Compensate>.<br /><br /> Para agregar la actividad, coloque su diseñador de actividad del cuadro de **herramientas** en el cuadro **CompensationHandler** del diseñador de actividad **CompensableActivity** . Agregue el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Falso|Especifica la actividad que se va a ejecutar al confirmar la actividad de la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Este controlador se puede invocar explícitamente mediante la actividad <xref:System.Activities.Statements.Confirm>.<br /><br /> Para agregar la actividad, coloque su diseñador de actividad del cuadro de **herramientas** en el cuadro **ConfirmationHandler** del diseñador de actividad **CompensableActivity** . Agregue el texto de la sugerencia "Coloque la actividad aquí".|

## <a name="see-also"></a>Consulte también

- [Transacción](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
