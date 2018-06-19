---
title: Diseñador de flujo de trabajo - Diseñador de actividades Interop
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb9eb5e8b2dbca57d28f9d350b769b5eaa90e2b2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979080"
---
# <a name="interop-activity-designer"></a>Diseñador de actividades Interop

El **interoperabilidad** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.Interop> actividad.

## <a name="the-interop-activity"></a>Actividad Interop
 La actividad <xref:System.Activities.Statements.Interop> administra la ejecución de tipos que derivan de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> en un flujo de trabajo.

### <a name="using-the-interop-activity-designer"></a>Utilizar el diseñador de actividades Interop
 El **interoperabilidad** Diseñador de actividad puede encontrarse en el **migración** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**pestaña (o bien, seleccione **cuadro de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El [migración](../workflow-designer/migration-activity-designers.md) categoría que contiene el <xref:System.Activities.Statements.Interop> actividad solo se muestra en el **cuadro de herramientas** si el proyecto tiene como destino la versión completa de .NET Framework 4.

 Para proyectos de C#, puede volver a destinar el proyecto para utilizar la versión completa de .NET Framework 4 haciendo clic en el proyecto en el **el Explorador de soluciones** y seleccionando **propiedades**. En el **aplicación** ficha, seleccione la **.NET Framework 4** opción en el **.NET framework de destino**. Seleccione el **Sí** botón en el **cambio de plataforma de destino** cuadro de diálogo que se muestra para solicitar la confirmación del cambio.

 Para los proyectos VB, puede volver a destinar el proyecto para utilizar la versión completa de .NET Framework 4 con el botón secundario en el proyecto en el **el Explorador de soluciones** y seleccionando **propiedades**. En el **compilar** , haga clic en el **opciones de compilación avanzadas** botón. Seleccione **.Net Framework 4** desde el **lista plataforma de destino** y, a continuación, haga clic en **Aceptar**. Haga clic en el **Sí** botón en el **cambio de plataforma de destino** cuadro de diálogo que se muestra para solicitar la confirmación del cambio.

 El **interoperabilidad** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Esto crea una <xref:System.Activities.Statements.Interop> actividad con el valor predeterminado es **DisplayName** de interoperabilidad. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **interoperabilidad** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.

 Haga clic en el **, haga clic para examinar...**  texto en la **ActivityType** cuadro, ya sea en el **interoperabilidad** actividad diseñador o en la cuadrícula de propiedades, para que aparezca el **examinar y seleccionar .net tipo** cuadro de diálogo. Solo se muestran los tipos para actividades de flujo de trabajo 3.0 o de flujo de trabajo 3.5 (es decir, los tipos derivados de <xref:System.Workflow.ComponentModel.Activity>). Para obtener más información acerca de cómo utilizar este cuadro para especificar un tipo, consulte el [examinar y seleccionar un cuadro de diálogo de tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) tema.

### <a name="the-interop-properties"></a>Propiedades Interop
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Interop> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en cuadrícula de propiedades o en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Interop>. El valor predeterminado es Interop. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Especifica el tipo de la actividad que contiene la actividad <xref:System.Activities.Statements.Interop>. Este tipo especificado debe derivar de <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Vea también

- [Migración](../workflow-designer/migration-activity-designers.md)