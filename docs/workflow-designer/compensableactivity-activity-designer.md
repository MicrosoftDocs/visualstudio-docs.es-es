---
title: Diseñador de flujo de trabajo - Diseñador de actividad CompensableActivity
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cfe5a207136b44e61beff77bec8c8c7b869568b6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942367"
---
# <a name="compensableactivity-activity-designer"></a>Diseñador de actividad CompensableActivity Activity

El **CompensableActivity** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.CompensableActivity> actividad.

## <a name="the-compensableactivity-activity"></a>La actividad CompensableActivity
 La clase <xref:System.Activities.Statements.CompensableActivity> define una unidad de trabajo que se puede confirmar o compensar después de que se haya completado correctamente.

### <a name="using-the-compensableactivity-activity-designer"></a>Usar el diseñador de actividad CompensableActivity
 El **CompensableActivity** Diseñador de actividad puede encontrarse en el **transacciones** categoría de **cuadro de herramientas**. Para abrir **cuadro de herramientas**, seleccione el **cuadro de herramientas** ficha en el lado izquierdo del Diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** desde el **vista** menús o presione **Ctrl**+**Alt** + **X**.

 El **CompensableActivity** Diseñador de actividad se puede arrastrar desde **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo. Se pudo quitar el Diseñador de actividades dentro de un <xref:System.Activities.Statements.Sequence>. Al colocar el Diseñador de actividad se crea un <xref:System.Activities.Statements.CompensableActivity> actividad su valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de CompensableActivity. Editar el <xref:System.Activities.Activity.DisplayName%2A> valor en el encabezado de la **CompensableActivity** Diseñador de actividad. También se pueden editar en el **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-compensableactivity-properties"></a>Las propiedades de CompensableActivity
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CompensableActivity> y se describe cómo se utilizan en el diseñador. El <xref:System.Activities.Activity.DisplayName%2A> y <xref:System.Activities.Activity%601.Result%2A> propiedad se puede editar en cuadrícula de propiedades, pero las demás propiedades se deben editar en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.CompensableActivity>. El valor predeterminado es CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Especifica el valor devuelto de la clase <xref:System.Activities.Statements.CompensableActivity>. Esta propiedad se debe editar en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Especifica la actividad para la que se proporciona la lógica de compensación, cancelación y confirmación. Para agregar la <xref:System.Activities.Statements.CompensableActivity.Body%2A> actividad, coloque una actividad **cuadro de herramientas** en el **cuerpo** cuadro en el **CompensableActivity** Diseñador de actividad. Agregue el texto de sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Especifica la actividad que se ejecuta cuando hay una cancelación. Para agregar la actividad, arrastre su diseñador desde **cuadro de herramientas** en el **CancellationHandler** cuadro en el **CompensableActivity** Diseñador de actividad. Agregar texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Especifica la actividad que se va a ejecutar al realizar la compensación para la actividad de la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Este controlador se puede invocar explícitamente mediante la actividad <xref:System.Activities.Statements.Compensate>.<br /><br /> Para agregar la actividad, coloque su diseñador de actividad del **cuadro de herramientas** en el **CompensationHandler** cuadro en el **CompensableActivity** Diseñador de actividad. Agregar texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Especifica la actividad que se va a ejecutar al confirmar la actividad de la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Este controlador se puede invocar explícitamente mediante la actividad <xref:System.Activities.Statements.Confirm>.<br /><br /> Para agregar la actividad, coloque su diseñador de actividad del **cuadro de herramientas** en el **ConfirmationHandler** cuadro en el **CompensableActivity** Diseñador de actividad. Agregar texto de la sugerencia "Coloque la actividad aquí".|

## <a name="see-also"></a>Vea también

- [Transacción](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)