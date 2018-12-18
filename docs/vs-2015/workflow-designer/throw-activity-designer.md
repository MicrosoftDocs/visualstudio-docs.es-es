---
title: Diseñador de actividad throw | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 335601a40b21400e77aad5c493788db6e7146acd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49275683"
---
# <a name="throw-activity-designer"></a>Diseñador de actividades Throw
El **Throw** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Throw> actividad.  
  
## <a name="the-throw-activity"></a>Actividad Throw  
 La actividad <xref:System.Activities.Statements.Throw> produce una excepción.  
  
### <a name="using-the-throw-activity-designer"></a>Utilizar el diseñador de actividades Throw  
 El **Throw** Diseñador de actividad puede encontrarse en el **Error Handling** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha en el lado izquierdo de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **Throw** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Esto crea un <xref:System.Activities.Statements.Throw> actividad con un valor predeterminado **DisplayName** de Throw. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **Throw** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades. La propiedad <xref:System.Activities.Statements.Throw.Exception%2A> se debe editar en la cuadrícula de propiedades.  
  
### <a name="the-throw-properties"></a>Propiedades Throw  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Throw> y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Throw>. El valor predeterminado es Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Excepción que se va a producir. Esta excepción debe derivar de <xref:System.Exception>. Para especificar la excepción, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|  
  
## <a name="see-also"></a>Vea también  
 [colección](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Diseñador de actividad throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)