---
title: Diseñador de actividades Persist | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f87997178f98e9e632b756b5a4440c19544b5c86
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971256"
---
# <a name="persist-activity-designer"></a>Diseñador de actividades Persist
El **Persist** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Persist> actividad.  
  
## <a name="the-persist-activity"></a>Actividad Persist  
 La actividad <xref:System.Activities.Statements.Persist> guarda un flujo de trabajo en el disco, si es posible. La actividad <xref:System.Activities.Statements.Persist> no se puede ejecutar en una zona que no sea de persistencia como, por ejemplo, dentro de una actividad <xref:System.Activities.Statements.TransactionScope>. Si utiliza una actividad <xref:System.Activities.Statements.Persist> en un ámbito que no sea de persistencia, se produce una excepción en tiempo de ejecución.  
  
### <a name="using-the-persist-activity-designer"></a>Utilizar el diseñador de actividades Persist  
 El **Persist** Diseñador de actividad puede encontrarse en el **en tiempo de ejecución** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **cuadro de herramientas** ficha (como alternativa, seleccione **cuadro de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **Persist** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Esto crea un <xref:System.Activities.Statements.Persist> actividad con un valor predeterminado **DisplayName** de Persist. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **Persist** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-persist-properties"></a>Propiedades Persist  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Persist> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Persist>. El valor predeterminado es Persist. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|  
  
## <a name="see-also"></a>Vea también  
 [En tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)