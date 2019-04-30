---
title: Diseñador de actividades CancellationScope | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6207d1fcd2e920de979a13624e5cf1b442c2703c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977200"
---
# <a name="cancellationscope-activity-designer"></a>Diseñador de actividades CancellationScope
El **CancellationScope** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.CancellationScope> actividad.  
  
## <a name="the-cancellationscope-activity"></a>Actividad CancellationScope  
 La actividad <xref:System.Activities.Statements.CancellationScope> le permite especificar una actividad para la lógica de ejecución y cancelación de esa actividad.  
  
### <a name="using-the-cancellationscope-activity-designer"></a>Utilizar el diseñador de actividades CancellationScope  
 El **CancellationScope** Diseñador de actividad puede encontrarse en el **transacciones** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **cuadro de herramientas**  pestaña de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **CancellationScope** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. De esta forma se crea una actividad <xref:System.Activities.Statements.CancellationScope> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de CancellationScope. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **CancellationScope** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-cancellationscope-properties"></a>Propiedades CancellationScope  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CancellationScope> y se describe cómo se utilizan en el diseñador. La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en cuadrícula de propiedades, pero las otras propiedades se debe editar en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.CancellationScope>. El valor predeterminado es CancellationScope. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Especifica la actividad para la que se proporciona la lógica de cancelación. Para agregar la <xref:System.Activities.Statements.CancellationScope.Body%2A> actividad, coloque una actividad desde la **cuadro de herramientas** en el **cuerpo** cuadro en el **CancellationScope** Diseñador de actividad con el texto de la sugerencia "Drop Actividad aquí".|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Especifica la actividad que se ejecuta en caso de cancelación. Para agregar la <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> actividad, coloque una actividad desde la **cuadro de herramientas** en el **CancellationHandler** cuadro en el **CancellationScope** Diseñador de actividad con la sugerencia texto "Coloque la actividad aquí".|  
  
## <a name="see-also"></a>Vea también  
 [Transacción](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensar](../workflow-designer/compensate-activity-designer.md)   
 [Confirmar](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)