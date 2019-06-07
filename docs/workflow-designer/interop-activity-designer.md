---
title: Diseñador de flujo de trabajo - Diseñador de actividades Interop
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688ef92fae5bd0cbaa5ddc653bbaab5692f4827f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747133"
---
# <a name="interop-activity-designer"></a>Diseñador de actividades Interop

El **interoperabilidad** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Interop> actividad.

## <a name="the-interop-activity"></a>Actividad Interop

La actividad <xref:System.Activities.Statements.Interop> administra la ejecución de tipos que derivan de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> en un flujo de trabajo.

### <a name="use-the-interop-activity-designer"></a>Utilice el Diseñador de actividades Interop

El **interoperabilidad** Diseñador de actividad puede encontrarse en el **migración** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha. Como alternativa, seleccione **cuadro de herramientas** desde el **vista** menús o presione **Ctrl**+**Alt** + **X**.

El [migración](../workflow-designer/migration-activity-designers.md) categoría que contiene el <xref:System.Activities.Statements.Interop> actividad aparece sólo en **cuadro de herramientas** si el proyecto tiene como destino .NET Framework 4 (completa) o una versión posterior. Si es necesario, puede cambiar la versión de framework que el proyecto está destinado.

El **interoperabilidad** Diseñador de actividad se puede arrastrar desde **cuadro de herramientas** y se coloca en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Quitar el **interoperabilidad** Diseñador de actividad se crea un <xref:System.Activities.Statements.Interop> actividad con un valor predeterminado **DisplayName** de interoperabilidad. Puede editar el <xref:System.Activities.Activity.DisplayName%2A> en el encabezado de la **interoperabilidad** Diseñador de actividad, o en el **DisplayName** cuadro de la cuadrícula de propiedades.

Haga clic en el **haga clic aquí para examinar** texto en el **ActivityType** cuadro, ya sea en el **interoperabilidad** actividad diseñador o en la cuadrícula de propiedades para abrir el **examinar y Seleccione .net tipo** cuadro de diálogo. Se muestran solo los tipos de flujo de trabajo 3.0 o las actividades de flujo de trabajo 3.5. Es decir, solo los tipos derivan de <xref:System.Workflow.ComponentModel.Activity> se muestran. Para obtener más información sobre el uso de este cuadro para especificar un tipo, consulte [examinar y seleccionar un cuadro de diálogo de tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Propiedades Interop

La tabla siguiente muestra la <xref:System.Activities.Statements.Interop> propiedades y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en cuadrícula de propiedades o en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Interop>. El valor predeterminado es **interoperabilidad**. Aunque el nombre para mostrar no es necesario, se recomienda para proporcionar uno.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Especifica el tipo de la actividad que contiene la actividad <xref:System.Activities.Statements.Interop>. Este tipo especificado debe derivar de <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Vea también

- [Migración](../workflow-designer/migration-activity-designers.md)