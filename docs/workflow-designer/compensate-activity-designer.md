---
title: Diseñador de flujo de trabajo - Diseñador de actividades Compensate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c55ecd8e3402d927b11cc00d18d6d134a5b25681
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911603"
---
# <a name="compensate-activity-designer"></a>Diseñador de actividades Compensate

El **compensar** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Compensate> actividad.

## <a name="the-compensate-activity"></a>Actividad Compensate

La actividad <xref:System.Activities.Statements.Compensate> invoca explícitamente a la propiedad <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> para una actividad que se incluye en <xref:System.Activities.Statements.CompensableActivity>. Si la actividad <xref:System.Activities.Statements.Compensate> no se utiliza dentro de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de una clase <xref:System.Activities.Statements.CompensableActivity>, debe especificar la propiedad <xref:System.Activities.Statements.Compensate.Target%2A>.

La clase <xref:System.Activities.Statements.CompensationToken> que especificó <xref:System.Activities.Statements.Compensate.Target%2A> proporciona un medio para confirmar o compensar explícitamente una clase <xref:System.Activities.Statements.CompensableActivity> una vez que la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> se haya completado correctamente.

### <a name="using-the-compensate-activity-designer"></a>Utilizar el diseñador de actividades Compensate

El **compensar** Diseñador de actividad puede encontrarse en el **transacciones** categoría de la **cuadro de herramientas**. Para abrir **cuadro de herramientas**, seleccione el **cuadro de herramientas** ficha en el lado izquierdo del Diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** desde el **vista** menús o presione **Ctrl**+**Alt** + **X**.

El **compensar** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Al colocar el Diseñador de actividad se crea un <xref:System.Activities.Statements.Compensate> actividad su valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de compensación. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **compensar** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-compensate-properties"></a>Propiedades Compensate

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CancellationScope> y se describe cómo se utilizan en el diseñador. El <xref:System.Activities.Activity.DisplayName%2A> propiedad se puede editar en cuadrícula de propiedades o en la superficie del Diseñador de flujo de trabajo. Editar el <xref:System.Activities.Statements.Compensate.Target%2A> propiedad en la cuadrícula de propiedades.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Compensate>. El valor predeterminado es Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Especifica la clase <xref:System.Activities.InArgument%601> que contiene la clase <xref:System.Activities.Statements.CompensationToken> para esta actividad <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Vea también

- [Transacción](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Diseñador de actividad Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)