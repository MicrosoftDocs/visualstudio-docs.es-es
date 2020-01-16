---
title: Diseñador de flujo de trabajo el diseñador de actividades Persist
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75236d7955cba6b8c62b9a4504f02c66cebe4062
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114771"
---
# <a name="persist-activity-designer"></a>Diseñador de actividades Persist

El diseñador de actividades **Persist** se usa para crear y configurar una actividad <xref:System.Activities.Statements.Persist>.

## <a name="the-persist-activity"></a>Actividad Persist

La actividad <xref:System.Activities.Statements.Persist> guarda un flujo de trabajo en el disco, si es posible. La actividad <xref:System.Activities.Statements.Persist> no se puede ejecutar en una zona que no sea de persistencia como, por ejemplo, dentro de una actividad <xref:System.Activities.Statements.TransactionScope>. Si usa una actividad <xref:System.Activities.Statements.Persist> en un ámbito que no es de persistencia, se produce una excepción en tiempo de ejecución.

### <a name="using-the-persist-activity-designer"></a>Utilizar el diseñador de actividades Persist

El diseñador de actividades **Persist** se puede encontrar en la categoría **tiempo de ejecución** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** . (de forma alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o Ctrl + Alt + X).

El diseñador de actividades **Persist** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence>. Esto crea una actividad <xref:System.Activities.Statements.Persist> con un valor **displayName** predeterminado de Persist. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **Persist** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-persist-properties"></a>Propiedades Persist

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Persist> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas se pueden editar en Diseñador de flujo de trabajo superficie.

|Nombre de la propiedad|Requerido|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Persist>. El valor predeterminado es Persist. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|

## <a name="see-also"></a>Vea también

- [Tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
