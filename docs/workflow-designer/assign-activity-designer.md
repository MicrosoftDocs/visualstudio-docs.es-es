---
title: Diseñador de flujo de trabajo - Diseñador de actividades Assign
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 600f38d7bcd387915ba61fc148805705e8609431
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905263"
---
# <a name="assign-activity-designer"></a>Diseñador de actividades Assign

El **asignar** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Assign> actividad.

## <a name="the-assign-activity"></a>Actividad Assign

La actividad <xref:System.Activities.Statements.Assign> asigna un valor a una variable o argumento.

### <a name="using-the-assign-activity-designer"></a>Utilizar el diseñador de actividades Assign

El **asignar** Diseñador de actividad puede encontrarse en el **primitivas** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha (como alternativa, seleccione **cuadro de herramientas** desde el **vista** menú o CTRL + ALT + X.)

El **asignar** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo, donde cada vez que se coloquen las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Quitar el **asignar** Diseñador de actividad se crea un <xref:System.Activities.Statements.Assign> actividad con un valor predeterminado **DisplayName** de Assign. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **asignar** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-assign-properties"></a>Propiedades Assign

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Assign> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en cuadrícula de propiedades y algunas de ellas se pueden editar en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Assign>. El valor predeterminado es Assign. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|La variable o argumento al que está asignado <xref:System.Activities.Statements.Assign.Value%2A>. El valor debe ser un identificador válido de Visual Basic. Para establecer la propiedad, escriba una expresión de Visual Basic en el **a** cuadro en el **asignar** actividad diseñador o en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valor que se asigna a la variable. Para establecer el <xref:System.Activities.Statements.Assign.Value%2A>, escriba una expresión de Visual Basic en el **valor** cuadro en el **asignar** actividad diseñador o en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Elementos primitivos](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)