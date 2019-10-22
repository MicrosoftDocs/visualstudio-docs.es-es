---
title: Diseñador de actividades TransactionScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5a1d38ea37896cedcd2166c42f37ce037a1c4cd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670174"
---
# <a name="transactionscope-activity-designer"></a>Diseñador de actividades TransactionScope
El diseñador de actividades **TransactionScope** se usa para crear y configurar una actividad <xref:System.Activities.Statements.TransactionScope>.

## <a name="the-transactionscope-activity"></a>Actividad TransactionScope
 La actividad <xref:System.Activities.Statements.TransactionScope> ejecuta la actividad que contiene una transacción única. La transacción se confirma cuando la actividad <xref:System.Activities.Statements.TransactionScope.Body%2A> y el resto de participantes en la transacción hayan finalizado correctamente.

### <a name="using-the-transactionscope-activity-designer"></a>Utilizar el diseñador de actividades TransactionScope
 El diseñador de actividades **TransactionScope** se puede encontrar en la categoría **transacción** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** de [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione barra de **herramientas** en la **vista** . menú o CTRL + ALT + X).

 El diseñador de actividades **TransactionScope** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie [!INCLUDE[wfd2](../includes/wfd2-md.md)], donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence>. De esta forma se crea una actividad <xref:System.Activities.Statements.TransactionScope> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de TransactionScope. El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **TransactionScope** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-transactionscope-properties"></a>Las propiedades de TransactionScope
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.TransactionScope> y se describe cómo se utilizan en el diseñador. Las propiedades <xref:System.Activities.Activity.DisplayName%2A> y <xref:System.Activities.Statements.TransactionScope.Body%2A> se pueden editar en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Pero el resto de propiedades se deben editar en la cuadrícula de propiedades.

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.TransactionScope>. El valor predeterminado es TransactionScope. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Especifica la actividad que se va a ejecutar en una transacción única. Para agregar la actividad <xref:System.Activities.Statements.TransactionScope.Body%2A>, coloque una actividad del cuadro de **herramientas** en el cuadro **Body** del diseñador de actividades **TransactionScope** con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Especifica la enumeración <xref:System.Transactions.IsolationLevel> de este objeto <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Especifica el intervalo de tiempo (con formato 00:00:00, que indica horas:minutos:segundos) del que dispone la transacción para completarse. El valor predeterminado es 1 minuto (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|True|Especifica el valor que indica si se debe anular el flujo de trabajo si se anula la transacción.|

## <a name="see-also"></a>Vea también
 [Confirmación](../workflow-designer/confirm-activity-designer.md) de [compensación](../workflow-designer/compensate-activity-designer.md) de [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) de [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) de [transacciones](../workflow-designer/transaction-activity-designers.md)