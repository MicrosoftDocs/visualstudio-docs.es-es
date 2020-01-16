---
title: 'Diseñador de flujo de trabajo: diseñador de actividades TransactionScope'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eef35457b9f28864929ad42919fff4e9afdcb0d5
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114820"
---
# <a name="transactionscope-activity-designer"></a>Diseñador de actividades TransactionScope

El diseñador de actividades **TransactionScope** se usa para crear y configurar una actividad <xref:System.Activities.Statements.TransactionScope>.

## <a name="the-transactionscope-activity"></a>Actividad TransactionScope

La actividad <xref:System.Activities.Statements.TransactionScope> ejecuta la actividad que contiene una transacción única. La transacción se confirma cuando la actividad <xref:System.Activities.Statements.TransactionScope.Body%2A> y el resto de participantes en la transacción hayan finalizado correctamente.

### <a name="using-the-transactionscope-activity-designer"></a>Utilizar el diseñador de actividades TransactionScope

Obtenga acceso al diseñador de actividades **TransactionScope** en la categoría **transacción** del **cuadro de herramientas**. El diseñador de actividades **TransactionScope** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence>. De esta forma se crea una actividad <xref:System.Activities.Statements.TransactionScope> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de TransactionScope. El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **TransactionScope** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-transactionscope-properties"></a>Las propiedades de TransactionScope

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.TransactionScope> y se describe cómo se utilizan en el diseñador. Las propiedades <xref:System.Activities.Activity.DisplayName%2A> y <xref:System.Activities.Statements.TransactionScope.Body%2A> se pueden editar en Diseñador de flujo de trabajo superficie. Pero el resto de propiedades se deben editar en la cuadrícula de propiedades.

|Nombre de la propiedad|Requerido|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.TransactionScope>. El valor predeterminado es TransactionScope. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Verdadero|Especifica la actividad que se va a ejecutar en una transacción única. Para agregar la actividad <xref:System.Activities.Statements.TransactionScope.Body%2A>, coloque una actividad del cuadro de **herramientas** en el cuadro **Body** del diseñador de actividades **TransactionScope** con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Verdadero|Especifica la enumeración <xref:System.Transactions.IsolationLevel> de este objeto <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Falso|Especifica el intervalo de tiempo (con formato 00:00:00, que indica horas:minutos:segundos) del que dispone la transacción para completarse. El valor predeterminado es 1 minuto (00:01:00).|
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|Verdadero|Especifica el valor que indica si se debe anular el flujo de trabajo si se anula la transacción.|

## <a name="see-also"></a>Vea también

- [Transacción](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
