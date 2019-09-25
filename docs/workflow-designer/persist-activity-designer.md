---
title: Diseñador de flujo de trabajo el diseñador de actividades Persist
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7be70d18b1fc8ff12e2d1fb177b41775954334ed
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254845"
---
# <a name="persist-activity-designer"></a>Diseñador de actividades Persist

El diseñador de actividades **Persist** se usa para crear y configurar <xref:System.Activities.Statements.Persist> una actividad.

## <a name="the-persist-activity"></a>Actividad Persist

La actividad <xref:System.Activities.Statements.Persist> guarda un flujo de trabajo en el disco, si es posible. La actividad <xref:System.Activities.Statements.Persist> no se puede ejecutar en una zona que no sea de persistencia como, por ejemplo, dentro de una actividad <xref:System.Activities.Statements.TransactionScope>. Si utiliza una <xref:System.Activities.Statements.Persist> actividad en un ámbito de no persistencia, se produce una excepción en tiempo de ejecución.

### <a name="using-the-persist-activity-designer"></a>Utilizar el diseñador de actividades Persist

El diseñador de actividades **Persist** se puede encontrar en la categoría **tiempo de ejecución** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** . (de forma alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o Ctrl + Alt + X).

El diseñador de actividades **Persist** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades <xref:System.Activities.Statements.Sequence>, como en una. Esto crea una <xref:System.Activities.Statements.Persist> actividad con un valor **displayName** predeterminado de Persist. Se puede editar en el encabezado del diseñador de actividades Persist o en el cuadro **displayName** de la cuadrícula de propiedades. <xref:System.Activities.Activity.DisplayName%2A>

### <a name="the-persist-properties"></a>Propiedades Persist

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Persist> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas se pueden editar en Diseñador de flujo de trabajo superficie.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Persist>. El valor predeterminado es Persist. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|

## <a name="see-also"></a>Vea también

- [Tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)