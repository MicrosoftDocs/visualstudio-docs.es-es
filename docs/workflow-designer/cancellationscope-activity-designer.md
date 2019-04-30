---
title: Diseñador de flujo de trabajo - Diseñador de actividades CancellationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43a818be208c7e07ef74a8f35923f3042bb8fad5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009795"
---
# <a name="cancellationscope-activity-designer"></a>Diseñador de actividades CancellationScope

El **CancellationScope** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.CancellationScope> actividad.

## <a name="the-cancellationscope-activity"></a>Actividad CancellationScope

La actividad <xref:System.Activities.Statements.CancellationScope> le permite especificar una actividad para la lógica de ejecución y cancelación de esa actividad.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilizar el diseñador de actividades CancellationScope

El **CancellationScope** Diseñador de actividad puede encontrarse en el **transacciones** categoría de **cuadro de herramientas**. Para abrir **cuadro de herramientas**, seleccione el **cuadro de herramientas** ficha del Diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** desde el **vista** menús o presione **Ctrl**+**Alt** + **X**.

El **CancellationScope** Diseñador de actividad se puede arrastrar desde **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Quitar el **CancellationScope** Diseñador de actividad se crea un <xref:System.Activities.Statements.CancellationScope> actividad su valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de CancellationScope. Editar el <xref:System.Activities.Activity.DisplayName%2A> valor en el encabezado de la **CancellationScope** Diseñador de actividad. También puede editar en el **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-cancellationscope-properties"></a>Propiedades CancellationScope

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CancellationScope> y se describe cómo se utilizan en el diseñador. El <xref:System.Activities.Activity.DisplayName%2A> propiedad se puede editar en cuadrícula de propiedades, pero las demás propiedades se deben editar en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.CancellationScope>. El valor predeterminado es CancellationScope. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Especifica la actividad para la que se proporciona la lógica de cancelación. Para agregar la <xref:System.Activities.Statements.CancellationScope.Body%2A> actividad, coloque una actividad **cuadro de herramientas** en el **cuerpo** cuadro en el **CancellationScope** Diseñador de actividad. Agregue el texto de sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Especifica la actividad que se ejecuta si se produce una cancelación. Para agregar la <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> actividad, coloque una actividad **cuadro de herramientas** en el **CancellationHandler** cuadro en el **CancellationScope** Diseñador de actividad. Agregue el texto de sugerencia "Coloque la actividad aquí".|

## <a name="see-also"></a>Vea también

- [Transacción](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)