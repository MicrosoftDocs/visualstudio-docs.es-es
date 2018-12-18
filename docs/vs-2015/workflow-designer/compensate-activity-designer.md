---
title: Diseñador de actividades compensate | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ae01f59e6d1b1c9d9e0baa4214a693b3e6d390d8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245939"
---
# <a name="compensate-activity-designer"></a>Diseñador de actividades Compensate
El **compensar** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Compensate> actividad.  
  
## <a name="the-compensate-activity"></a>Actividad Compensate  
 La actividad <xref:System.Activities.Statements.Compensate> invoca explícitamente a la propiedad <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> para una actividad que se incluye en <xref:System.Activities.Statements.CompensableActivity>. Si la actividad <xref:System.Activities.Statements.Compensate> no se utiliza dentro de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de una clase <xref:System.Activities.Statements.CompensableActivity>, debe especificar la propiedad <xref:System.Activities.Statements.Compensate.Target%2A>.  
  
 La clase <xref:System.Activities.Statements.CompensationToken> que especificó <xref:System.Activities.Statements.Compensate.Target%2A> proporciona un medio para confirmar o compensar explícitamente una clase <xref:System.Activities.Statements.CompensableActivity> una vez que la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> se haya completado correctamente.  
  
### <a name="using-the-compensate-activity-designer"></a>Utilizar el diseñador de actividades Compensate  
 El **compensar** Diseñador de actividad puede encontrarse en el **transacciones** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas** ficha en el lado izquierdo de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **compensar** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. De esta forma se crea una actividad <xref:System.Activities.Statements.Compensate> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Compensate. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **compensar** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-compensate-properties"></a>Propiedades Compensate  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CancellationScope> y se describe cómo se utilizan en el diseñador. La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en cuadrícula de propiedades o en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)], pero la propiedad <xref:System.Activities.Statements.Compensate.Target%2A> se debe editar en la cuadrícula de propiedades.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Compensate>. El valor predeterminado es Compensate.|  
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Especifica la clase <xref:System.Activities.InArgument%601> que contiene la clase <xref:System.Activities.Statements.CompensationToken> para esta actividad <xref:System.Activities.Statements.Compensate>.|  
  
## <a name="see-also"></a>Vea también  
 [Transacción](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Diseñador de actividades compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirmar](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)