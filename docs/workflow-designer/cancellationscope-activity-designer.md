---
title: Diseñador de actividades Diseñador de flujo de trabajo-CancellationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6d1067b529dffec5a4e6a1f21d5489c32311c07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "76112509"
---
# <a name="cancellationscope-activity-designer"></a>Diseñador de actividades CancellationScope

El diseñador de actividades **CancellationScope** se utiliza para crear y configurar una <xref:System.Activities.Statements.CancellationScope> actividad.

## <a name="the-cancellationscope-activity"></a>Actividad CancellationScope

La actividad <xref:System.Activities.Statements.CancellationScope> le permite especificar una actividad para la lógica de ejecución y cancelación de esa actividad.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilizar el diseñador de actividades CancellationScope

El diseñador de actividades **CancellationScope** se puede encontrar en la categoría **transacción** del **cuadro de herramientas**. Para abrir el **cuadro de herramientas**, seleccione la pestaña cuadro de **herramientas** del diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** + **Alt** + **X**.

El diseñador de actividades **CancellationScope** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo cada vez que se colocan las actividades, como en una <xref:System.Activities.Statements.Sequence> . Al quitar el diseñador de actividades **CancellationScope** , se crea una <xref:System.Activities.Statements.CancellationScope> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de CancellationScope. Edite el <xref:System.Activities.Activity.DisplayName%2A> valor en el encabezado del diseñador de actividades **CancellationScope** . También puede editarlo en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-cancellationscope-properties"></a>Propiedades CancellationScope

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CancellationScope> y se describe cómo se utilizan en el diseñador. La <xref:System.Activities.Activity.DisplayName%2A> propiedad se puede editar en la cuadrícula de propiedades, pero las demás propiedades deben editarse en diseñador de flujo de trabajo superficie.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.CancellationScope>. El valor predeterminado es CancellationScope. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Verdadero|Especifica la actividad para la que se proporciona la lógica de cancelación. Para agregar la <xref:System.Activities.Statements.CancellationScope.Body%2A> actividad, coloque una actividad del cuadro de **herramientas** en el cuadro **Body** del diseñador de actividades **CancellationScope** . Agregue el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Verdadero|Especifica la actividad que se ejecuta si hay una cancelación. Para agregar la <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> actividad, coloque una actividad del cuadro de **herramientas** en el cuadro **CancellationHandler** del diseñador de actividad **CancellationScope** . Agregue el texto de la sugerencia "Coloque la actividad aquí".|

## <a name="see-also"></a>Consulte también

- [Transacción](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirmar](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
