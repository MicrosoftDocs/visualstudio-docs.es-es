---
title: "Diseñador de actividades throw | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: f9af95a8aeb509554cb613edb848c2987543f1e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="throw-activity-designer"></a>Diseñador de actividades Throw
El **Throw** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.Throw> actividad.  
  
## <a name="the-throw-activity"></a>Actividad Throw  
 La actividad <xref:System.Activities.Statements.Throw> produce una excepción.  
  
### <a name="using-the-throw-activity-designer"></a>Utilizar el diseñador de actividades Throw  
 El **Throw** Diseñador de actividad puede encontrarse en el **control de errores** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha en el lado izquierdo de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **Throw** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Esto crea una <xref:System.Activities.Statements.Throw> actividad con el valor predeterminado es **DisplayName** de Throw. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado de la **Throw** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades. La propiedad <xref:System.Activities.Statements.Throw.Exception%2A> se debe editar en la cuadrícula de propiedades.  
  
### <a name="the-throw-properties"></a>Propiedades Throw  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Throw> y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Throw>. El valor predeterminado es Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Excepción que se va a producir. Esta excepción debe derivar de <xref:System.Exception>. Para especificar la excepción, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|  
  
## <a name="see-also"></a>Vea también  
 [Colección](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Diseñador de actividades throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)