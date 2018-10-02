---
title: Diseñador de actividades Rethrow | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: fa9d9ccd4e3e355a872d1dcf8a7767f0a1a618cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577973"
---
# <a name="rethrow-activity-designer"></a>Diseñador de actividades Rethrow
El **Rethrow** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Rethrow> actividad.  
  
## <a name="the-rethrow-activity"></a>Actividad Rethrow  
 La actividad <xref:System.Activities.Statements.Rethrow> produce un excepción que ya se había producido anteriormente. Esta actividad solo se puede utilizar en un controlador <xref:System.Activities.Statements.Catch> en la actividad <xref:System.Activities.Statements.TryCatch>.  
  
### <a name="using-the-rethrow-activity-designer"></a>Utilizar el diseñador de actividades ReThrow  
 El **Rethrow** Diseñador de actividad puede encontrarse en el **Error Handling** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha en el lado izquierdo de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **Rethrow** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Esto crea un <xref:System.Activities.Statements.Rethrow> actividad con un valor predeterminado **DisplayName** de Throw. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **Rethrow** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-rethrow-properties"></a>Propiedades Rethrow  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Rethrow> y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Rethrow>. El valor predeterminado es Rethrow.|  
  
## <a name="see-also"></a>Vea también  
 [colección](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)