---
title: "Diseñador de actividad CompensableActivity | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: f7523327fe63bfd00fb5bc5ce4f98aeef61a2567
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="compensableactivity-activity-designer"></a>Diseñador de actividad CompensableActivity Activity
El **CompensableActivity** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.CompensableActivity> actividad.  
  
## <a name="the-compensableactivity-activity"></a>La actividad CompensableActivity  
 La clase <xref:System.Activities.Statements.CompensableActivity> define una unidad de trabajo que se puede confirmar o compensar después de que se haya completado correctamente.  
  
### <a name="using-the-compensableactivity-activity-designer"></a>Usar el diseñador de actividad CompensableActivity  
 El **CompensableActivity** Diseñador de actividad puede encontrarse en el **transacciones** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en la **cuadro de herramientas**  ficha en el lado izquierdo de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **CompensableActivity** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. De esta forma, se crea una actividad de la clase <xref:System.Activities.Statements.CompensableActivity> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de CompensableActivity. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado de la **CompensableActivity** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-compensableactivity-properties"></a>Las propiedades de CompensableActivity  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CompensableActivity> y se describe cómo se utilizan en el diseñador. Las propiedades <xref:System.Activities.Activity.DisplayName%2A> y <xref:System.Activities.Activity%601.Result%2A> se pueden editar en la cuadrícula de propiedades, pero el resto de propiedades se deben editar en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.CompensableActivity>. El valor predeterminado es CompensableActivity.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Especifica el valor devuelto de la clase <xref:System.Activities.Statements.CompensableActivity>. Esta propiedad se debe editar en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Especifica la actividad para la que se proporciona la lógica de compensación, cancelación y confirmación. Para agregar el <xref:System.Activities.Statements.CompensableActivity.Body%2A> actividad, coloque una actividad desde la **cuadro de herramientas** en el **cuerpo** cuadro en el **CompensableActivity** Diseñador de actividad con el texto de la sugerencia "colocar actividad aquí".|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Especifica la actividad que se ejecuta en caso de cancelación. Para agregar la actividad, coloque su diseñador de la **cuadro de herramientas** en el **CancellationHandler** cuadro en el **CompensableActivity** Diseñador de actividad con el texto de la sugerencia "colocar Actividad aquí".|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Especifica la actividad que se va a ejecutar al realizar la compensación para la actividad de la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Este controlador se puede invocar explícitamente mediante la actividad <xref:System.Activities.Statements.Compensate>.<br /><br /> Para agregar la actividad, coloque su diseñador de actividad de la **cuadro de herramientas** en el **CompensationHandler** cuadro en el **CompensableActivity** Diseñador de actividad con el texto de la sugerencia " Coloque la actividad aquí".|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Especifica la actividad que se va a ejecutar al confirmar la actividad de la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Este controlador se puede invocar explícitamente mediante la actividad <xref:System.Activities.Statements.Confirm>.<br /><br /> Para agregar la actividad, coloque su diseñador de actividad de la **cuadro de herramientas** en el **ConfirmationHandler** cuadro en el **CompensableActivity** Diseñador de actividad con el texto de la sugerencia " Coloque la actividad aquí".|  
  
## <a name="see-also"></a>Vea también  
 [Transacción](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [Compensar](../workflow-designer/compensate-activity-designer.md)   
 [Confirmar](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)