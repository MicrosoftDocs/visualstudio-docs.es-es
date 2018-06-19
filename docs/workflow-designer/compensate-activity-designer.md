---
title: Diseñador de flujo de trabajo - Diseñador de actividades Compensate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8278066a12df0d195770391d0b2f3144ba16487d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31972272"
---
# <a name="compensate-activity-designer"></a>Diseñador de actividades Compensate

El **compensar** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.Compensate> actividad.

## <a name="the-compensate-activity"></a>Actividad Compensate
 La actividad <xref:System.Activities.Statements.Compensate> invoca explícitamente a la propiedad <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> para una actividad que se incluye en <xref:System.Activities.Statements.CompensableActivity>. Si la actividad <xref:System.Activities.Statements.Compensate> no se utiliza dentro de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de una clase <xref:System.Activities.Statements.CompensableActivity>, debe especificar la propiedad <xref:System.Activities.Statements.Compensate.Target%2A>.

 La clase <xref:System.Activities.Statements.CompensationToken> que especificó <xref:System.Activities.Statements.Compensate.Target%2A> proporciona un medio para confirmar o compensar explícitamente una clase <xref:System.Activities.Statements.CompensableActivity> una vez que la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> se haya completado correctamente.

### <a name="using-the-compensate-activity-designer"></a>Utilizar el diseñador de actividades Compensate
 El **compensar** Diseñador de actividad puede encontrarse en el **transacciones** categoría de la **cuadro de herramientas**. Para abrir **cuadro de herramientas**, seleccione la **cuadro de herramientas** ficha en el lado izquierdo del Diseñador de flujo de trabajo (como alternativa, seleccione **barra de herramientas** desde el **vista**menú o CTRL + ALT + X.)

 El **compensar** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Al colocar el Diseñador de actividad se crea un <xref:System.Activities.Statements.Compensate> actividad con el valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de compensar. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado de la **compensar** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-compensate-properties"></a>Propiedades Compensate
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CancellationScope> y se describe cómo se utilizan en el diseñador. El <xref:System.Activities.Activity.DisplayName%2A> propiedad se puede editar en cuadrícula de propiedades o en la superficie del Diseñador de flujo de trabajo. Editar el <xref:System.Activities.Statements.Compensate.Target%2A> propiedad en la cuadrícula de propiedades.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Compensate>. El valor predeterminado es Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Especifica la clase <xref:System.Activities.InArgument%601> que contiene la clase <xref:System.Activities.Statements.CompensationToken> para esta actividad <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Vea también

- [Transacción](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Diseñador de actividad Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirmar](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)