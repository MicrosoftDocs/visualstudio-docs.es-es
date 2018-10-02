---
title: Diseñador de actividades Assign | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0b4f62b8eb542dcc077915d5914e5d178dd4fc96
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567713"
---
# <a name="assign-activity-designer"></a>Diseñador de actividades Assign
El **asignar** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Assign> actividad.  
  
## <a name="the-assign-activity"></a>Actividad Assign  
 La actividad <xref:System.Activities.Statements.Assign> asigna un valor a una variable o argumento.  
  
### <a name="using-the-assign-activity-designer"></a>Utilizar el diseñador de actividades Assign  
 El **asignar** Diseñador de actividad puede encontrarse en el **primitivas** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha (como alternativa, seleccione **cuadro de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **asignar** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Esto crea un <xref:System.Activities.Statements.Assign> actividad con un valor predeterminado **DisplayName** de Assign. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **asignar** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-assign-properties"></a>Propiedades Assign  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Assign> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Assign>. El valor predeterminado es Assign. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|La variable o argumento al que está asignado <xref:System.Activities.Statements.Assign.Value%2A>. Debe ser un identificador de Visual Basic válido. Para establecer la propiedad, escriba una expresión de Visual Basic en el **a** cuadro en el **asignar** actividad diseñador o en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valor que se asigna a la variable. Para establecer el <xref:System.Activities.Statements.Assign.Value%2A>, escriba una expresión de Visual Basic en el **valor** cuadro en el **asignar** actividad diseñador o en la cuadrícula de propiedades.|  
  
## <a name="see-also"></a>Vea también  
 [Tipos primitivos](../workflow-designer/primitives-activity-designers.md)   
 [Retraso](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)