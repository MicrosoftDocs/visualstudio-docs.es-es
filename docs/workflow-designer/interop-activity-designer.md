---
title: "Dise&#241;ador de actividades Interop | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Interop.UI"
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades Interop
El diseñador de actividades **Interop** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.Interop>.  
  
## Actividad Interop  
 La actividad <xref:System.Activities.Statements.Interop> administra la ejecución de tipos que derivan de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> en un flujo de trabajo.  
  
### Utilizar el diseñador de actividades Interop  
 El diseñador de actividades **Interop** se puede encontrar en la categoría **Migración** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas**. \(De forma alternativa, seleccione **Cuadro de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 La categoría [Migración](../workflow-designer/migration-activity-designers.md) que contiene la actividad <xref:System.Activities.Statements.Interop> solo aparece en el **Cuadro de herramientas** si el proyecto está destinando a [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] en su integridad.  
  
 Para los proyectos C\#, puede volver a determinar el destino para que utilice la totalidad de [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], si hace clic con el botón secundario en el **Explorador de soluciones** y selecciona **Propiedades**.En la pestaña **Aplicación**, seleccione la opción **.NET Framework 4** en la **versión de .NET Framework de destino**.Seleccione el botón **Sí** en el cuadro de diálogo **Cambio de versión de .NET Framework de destino** que se muestra para solicitar la confirmación del cambio.  
  
 Para los proyectos de VB, puede volver a determinar el destino para que utilice la totalidad de [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], si hace clic con el botón secundario en el **Explorador de soluciones** y selecciona **Propiedades**.En la pestaña **Compilación**, haga clic en el botón **Opciones de compilación** avanzadas.Seleccione **.Net Framework 4** en la lista **Versión de .NET Framework de destino** y, a continuación, haga clic en **Aceptar**.Haga clic en el botón **Sí** en el cuadro de diálogo **Cambio de versión de .NET Framework de destino** que se muestra para solicitar la confirmación del cambio.  
  
 El diseñador de actividades **Interop** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.Esto crea una actividad <xref:System.Activities.Statements.Interop> con un valor **DisplayName** predeterminado de Interop.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividad **Interop** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
 Haga clic en el texto **Haga clic para examinar** del cuadro **ActivityType**, o en el diseñador de actividades **Interop** o en la cuadrícula de propiedades para que aparezca el cuadro de diálogo **Examinar y seleccionar un tipo .NET**.Solo se muestran los tipos para actividades de flujo de trabajo 3.0 o de flujo de trabajo 3.5 \(es decir, los tipos derivados de <xref:System.Workflow.ComponentModel.Activity>\).[!INCLUDE[crabout](../test/includes/crabout_md.md)] cómo usar este cuadro para especificar un tipo, vea el tema [Examinar y seleccionar un cuadro de diálogo de tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).  
  
### Propiedades Interop  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Interop> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo de la actividad <xref:System.Activities.Statements.Interop>.El valor predeterminado es Interop.Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Especifica el tipo de la actividad que contiene la actividad <xref:System.Activities.Statements.Interop>.Este tipo especificado debe derivar de <xref:System.Workflow.ComponentModel.Activity>.|  
  
## Vea también  
 [Migración](../workflow-designer/migration-activity-designers.md)