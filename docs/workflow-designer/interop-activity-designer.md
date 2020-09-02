---
title: Diseñador de actividades Diseñador de flujo de trabajo-Interop
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8047df3787c0871e369b6079e4f0cc80f6d93949
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650208"
---
# <a name="interop-activity-designer"></a>Diseñador de actividades Interop

El diseñador de actividades **Interop** se usa para crear y configurar una <xref:System.Activities.Statements.Interop> actividad.

## <a name="the-interop-activity"></a>Actividad Interop

La actividad <xref:System.Activities.Statements.Interop> administra la ejecución de tipos que derivan de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> en un flujo de trabajo.

### <a name="use-the-interop-activity-designer"></a>Usar el diseñador de actividades Interop

El diseñador de actividades **Interop** se puede encontrar en la categoría **migración** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** . Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** + **Alt** + **X**.

La categoría [migración](../workflow-designer/migration-activity-designers.md) que contiene la <xref:System.Activities.Statements.Interop> actividad solo aparece en el **cuadro de herramientas** si su proyecto tiene como destino .NET Framework 4 (Full) o posterior. Si es necesario, puede cambiar la versión de .NET Framework de destino del proyecto.

El diseñador de actividades **Interop** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Al quitar el diseñador de actividades **Interop** se crea una <xref:System.Activities.Statements.Interop> actividad con un valor **displayName** predeterminado de Interop. Puede editar <xref:System.Activities.Activity.DisplayName%2A> en el encabezado del diseñador de actividades **Interop** o en el cuadro **displayName** de la cuadrícula de propiedades.

Haga clic en el texto **haga clic para examinar** el texto del cuadro **ActivityType** , ya sea en el diseñador de actividades **Interop**  o en la cuadrícula de propiedades, para abrir el cuadro de diálogo **examinar y seleccionar un tipo .net** . Solo se muestran los tipos para las actividades de flujo de trabajo 3,0 o 3,5. Es decir, solo se muestran los tipos derivados de <xref:System.Workflow.ComponentModel.Activity> . Para obtener más información sobre el uso de este cuadro para especificar un tipo, vea [examinar y seleccionar un cuadro de diálogo de tipo .net](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Propiedades Interop

En la tabla siguiente se muestran las <xref:System.Activities.Statements.Interop> propiedades y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie de Diseñador de flujo de trabajo.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Interop>. El valor predeterminado es **Interop**. Aunque el nombre para mostrar no es necesario, se recomienda proporcionar uno.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Verdadero|Especifica el tipo de la actividad que contiene la actividad <xref:System.Activities.Statements.Interop>. Este tipo especificado debe derivar de <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Consulte también

- [Migración](../workflow-designer/migration-activity-designers.md)