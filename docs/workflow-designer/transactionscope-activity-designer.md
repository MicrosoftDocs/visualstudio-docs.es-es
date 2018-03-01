---
title: "Diseñador de actividades TransactionScope | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 9c9b9ab609825a68edc4e2862d64bdd7cb830202
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="transactionscope-activity-designer"></a>Diseñador de actividades TransactionScope
El **TransactionScope** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.TransactionScope> actividad.  
  
## <a name="the-transactionscope-activity"></a>Actividad TransactionScope  
 La actividad <xref:System.Activities.Statements.TransactionScope> ejecuta la actividad que contiene una transacción única. La transacción se confirma cuando la actividad <xref:System.Activities.Statements.TransactionScope.Body%2A> y el resto de participantes en la transacción hayan finalizado correctamente.  
  
### <a name="using-the-transactionscope-activity-designer"></a>Utilizar el diseñador de actividades TransactionScope  
 El **TransactionScope** Diseñador de actividad puede encontrarse en el **transacciones** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en la **cuadro de herramientas**  ficha de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **TransactionScope** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. De esta forma se crea una actividad <xref:System.Activities.Statements.TransactionScope> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de TransactionScope. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado de la **TransactionScope** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-transactionscope-properties"></a>Las propiedades de TransactionScope  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.TransactionScope> y se describe cómo se utilizan en el diseñador. Las propiedades <xref:System.Activities.Activity.DisplayName%2A> y <xref:System.Activities.Statements.TransactionScope.Body%2A> se pueden editar en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Pero el resto de propiedades se deben editar en la cuadrícula de propiedades.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.TransactionScope>. El valor predeterminado es TransactionScope. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Especifica la actividad que se va a ejecutar en una transacción única. Para agregar el <xref:System.Activities.Statements.TransactionScope.Body%2A> actividad, coloque una actividad desde la **cuadro de herramientas** en el **cuerpo** cuadro en el **TransactionScope** Diseñador de actividad con el texto de la sugerencia "Coloque la actividad aquí".|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Especifica la enumeración <xref:System.Transactions.IsolationLevel> de este objeto <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Especifica el intervalo de tiempo (con formato 00:00:00, que indica horas:minutos:segundos) del que dispone la transacción para completarse. El valor predeterminado es 1 minuto (00:01:00).|  
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|True|Especifica el valor que indica si se debe anular el flujo de trabajo si se anula la transacción.|  
  
## <a name="see-also"></a>Vea también  
 [Transacción](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensar](../workflow-designer/compensate-activity-designer.md)   
 [Confirmar](../workflow-designer/confirm-activity-designer.md)