---
title: "Diseñador de actividades Interop | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 726bc2fa995d819b0e554e11439c85f9fdf19243
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="interop-activity-designer"></a>Diseñador de actividades Interop
El **interoperabilidad** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.Interop> actividad.  
  
## <a name="the-interop-activity"></a>Actividad Interop  
 La actividad <xref:System.Activities.Statements.Interop> administra la ejecución de tipos que derivan de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> en un flujo de trabajo.  
  
### <a name="using-the-interop-activity-designer"></a>Utilizar el diseñador de actividades Interop  
 El **interoperabilidad** Diseñador de actividad puede encontrarse en el **migración** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**pestaña (o bien, seleccione **cuadro de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El [migración](../workflow-designer/migration-activity-designers.md) categoría que contiene el <xref:System.Activities.Statements.Interop> actividad solo se muestra en el **cuadro de herramientas** si el proyecto tiene como destino el completo [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)].  
  
 Para proyectos de C#, puede volver a destinar el proyecto para que utilice la totalidad [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] haciendo clic en el proyecto en el **el Explorador de soluciones** y seleccionando **propiedades**. En el **aplicación** ficha, seleccione la **.NET Framework 4** opción en el **.NET framework de destino**. Seleccione el **Sí** botón en el **cambio de plataforma de destino** cuadro de diálogo que se muestra para solicitar la confirmación del cambio.  
  
 Para los proyectos VB, puede volver a destinar el proyecto para que utilice la totalidad [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] con el botón secundario en el proyecto en el **el Explorador de soluciones** y seleccionando **propiedades**. En el **compilar** , haga clic en el **opciones de compilación avanzadas** botón. Seleccione **.Net Framework 4** desde el **lista plataforma de destino** y, a continuación, haga clic en **Aceptar**. Haga clic en el **Sí** botón en el **cambio de plataforma de destino** cuadro de diálogo que se muestra para solicitar la confirmación del cambio.  
  
 El **interoperabilidad** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Esto crea una <xref:System.Activities.Statements.Interop> actividad con el valor predeterminado es **DisplayName** de interoperabilidad. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **interoperabilidad** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.  
  
 Haga clic en el **, haga clic para examinar...**  texto en la **ActivityType** cuadro, ya sea en el **interoperabilidad** actividad diseñador o en la cuadrícula de propiedades, para que aparezca el **examinar y seleccionar .net tipo** cuadro de diálogo. Solo se muestran los tipos para actividades de flujo de trabajo 3.0 o de flujo de trabajo 3.5 (es decir, los tipos derivados de <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../test/includes/crabout_md.md)]utilizar este cuadro para especificar un tipo, consulte el [examinar y seleccionar un cuadro de diálogo de tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) tema.  
  
### <a name="the-interop-properties"></a>Propiedades Interop  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Interop> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Interop>. El valor predeterminado es Interop. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Especifica el tipo de la actividad que contiene la actividad <xref:System.Activities.Statements.Interop>. Este tipo especificado debe derivar de <xref:System.Workflow.ComponentModel.Activity>.|  
  
## <a name="see-also"></a>Vea también  
 [Migración](../workflow-designer/migration-activity-designers.md)