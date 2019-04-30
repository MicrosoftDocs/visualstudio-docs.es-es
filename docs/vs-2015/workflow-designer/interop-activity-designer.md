---
title: Diseñador de actividades Interop | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55829e85b17bcdc70e419a8496d4756d0acb4a56
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952053"
---
# <a name="interop-activity-designer"></a>Diseñador de actividades Interop
El **interoperabilidad** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Interop> actividad.  
  
## <a name="the-interop-activity"></a>Actividad Interop  
 La actividad <xref:System.Activities.Statements.Interop> administra la ejecución de tipos que derivan de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> en un flujo de trabajo.  
  
### <a name="using-the-interop-activity-designer"></a>Utilizar el diseñador de actividades Interop  
 El **interoperabilidad** Diseñador de actividad puede encontrarse en el **migración** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha (como alternativa, seleccione **cuadro de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El [migración](../workflow-designer/migration-activity-designers.md) categoría que contiene el <xref:System.Activities.Statements.Interop> actividad solo se muestra en el **cuadro de herramientas** si el proyecto está destinando [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)].  
  
 Para proyectos de C#, puede volver a destinar el proyecto para que utilice la totalidad [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] haciendo clic con el proyecto en el **el Explorador de soluciones** y seleccionando **propiedades**. En el **aplicación** ficha, seleccione el **.NET Framework 4** opción el **.NET framework de destino**. Seleccione el **Sí** situado en la **cambio de plataforma de destino** cuadro de diálogo que muestra que le pide que confirme este cambio.  
  
 Para los proyectos de VB, puede volver a destinar el proyecto para que utilice la totalidad [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] con el botón secundario en el proyecto en el **el Explorador de soluciones** y seleccionando **propiedades**. En el **compilar** pestaña, haga clic en el **Advanced Compile Options** botón. Seleccione **.Net Framework 4** desde el **lista plataforma de destino** y, a continuación, haga clic en **Aceptar**. Haga clic en el **Sí** situado en la **cambio de plataforma de destino** cuadro de diálogo que muestra que le pide que confirme este cambio.  
  
 El **interoperabilidad** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Esto crea un <xref:System.Activities.Statements.Interop> actividad con un valor predeterminado **DisplayName** de interoperabilidad. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **interoperabilidad** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.  
  
 Haga clic en el **haga clic aquí para examinar...** texto en el **ActivityType** cuadro, ya sea en el **interoperabilidad** actividad diseñador o en la cuadrícula de propiedades, para que aparezca el **examinar y seleccionar .net tipo** cuadro de diálogo. Solo se muestran los tipos para actividades de flujo de trabajo 3.0 o de flujo de trabajo 3.5 (es decir, los tipos derivados de <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] mediante este cuadro para especificar un tipo, consulte el [examinar y seleccionar un cuadro de diálogo de tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) tema.  
  
### <a name="the-interop-properties"></a>Propiedades Interop  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Interop> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Interop>. El valor predeterminado es Interop. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Especifica el tipo de la actividad que contiene la actividad <xref:System.Activities.Statements.Interop>. Este tipo especificado debe derivar de <xref:System.Workflow.ComponentModel.Activity>.|  
  
## <a name="see-also"></a>Vea también  
 [Migración](../workflow-designer/migration-activity-designers.md)