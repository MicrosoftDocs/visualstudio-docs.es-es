---
title: Diseñador de flujo de trabajo - Diseñador de actividades CancellationScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0f9a40434821294384154ddcbbfebbd0a7885eb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975346"
---
# <a name="cancellationscope-activity-designer"></a>Diseñador de actividades CancellationScope

El **CancellationScope** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.CancellationScope> actividad.

## <a name="the-cancellationscope-activity"></a>Actividad CancellationScope
 La actividad <xref:System.Activities.Statements.CancellationScope> le permite especificar una actividad para la lógica de ejecución y cancelación de esa actividad.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilizar el diseñador de actividades CancellationScope
 El **CancellationScope** Diseñador de actividad puede encontrarse en el **transacciones** categoría de **cuadro de herramientas**. Para abrir **cuadro de herramientas**, seleccione la **cuadro de herramientas** ficha del Diseñador de flujo de trabajo. Como alternativa, seleccione **barra de herramientas** desde el **vista** menú o presione CTRL + ALT + X.

 El **CancellationScope** Diseñador de actividad se puede arrastrar desde **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Quitar el **CancellationScope** Diseñador de actividad crea una <xref:System.Activities.Statements.CancellationScope> actividad con el valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de CancellationScope. Editar la <xref:System.Activities.Activity.DisplayName%2A> valor en el encabezado de la **CancellationScope** Diseñador de actividad. También puede editar en el **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-cancellationscope-properties"></a>Propiedades CancellationScope
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CancellationScope> y se describe cómo se utilizan en el diseñador. El <xref:System.Activities.Activity.DisplayName%2A> propiedad se puede editar en cuadrícula de propiedades, pero las otras propiedades deben editarse en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.CancellationScope>. El valor predeterminado es CancellationScope. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Especifica la actividad para la que se proporciona la lógica de cancelación. Para agregar el <xref:System.Activities.Statements.CancellationScope.Body%2A> actividad, coloque una actividad **cuadro de herramientas** en el **cuerpo** cuadro en el **CancellationScope** Diseñador de actividad. Agregue el texto de sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Especifica la actividad que se ejecuta si se produce una cancelación. Para agregar el <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> actividad, coloque una actividad **cuadro de herramientas** en el **CancellationHandler** cuadro en el **CancellationScope** Diseñador de actividad. Agregue el texto de sugerencia "Coloque la actividad aquí".|

## <a name="see-also"></a>Vea también

- [Transacción](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensar](../workflow-designer/compensate-activity-designer.md)
- [Confirmar](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)