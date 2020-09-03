---
title: Diseñador de actividad Interop | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659033"
---
# <a name="interop-activity-designer"></a>Diseñador de actividades Interop
El diseñador de actividades **Interop** se usa para crear y configurar una <xref:System.Activities.Statements.Interop> actividad.

## <a name="the-interop-activity"></a>Actividad Interop
 La actividad <xref:System.Activities.Statements.Interop> administra la ejecución de tipos que derivan de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> en un flujo de trabajo.

### <a name="using-the-interop-activity-designer"></a>Utilizar el diseñador de actividades Interop
 El diseñador de actividades **Interop** se puede encontrar en la categoría **migración** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** . (de forma alternativa, seleccione cuadro de **herramientas** en el menú **Ver** o Ctrl + Alt + X).

 La categoría de [migración](../workflow-designer/migration-activity-designers.md) que contiene la <xref:System.Activities.Statements.Interop> actividad solo se muestra en el **cuadro de herramientas** si el proyecto tiene como destino el completo [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] .

 En el caso de los proyectos de C#, puede redirigir el proyecto para que use el completo haciendo [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccionando **propiedades**. En la pestaña **aplicación** , seleccione la opción **.NET Framework 4** en la versión de **.NET Framework de destino**. Seleccione el botón **sí** en el cuadro de diálogo de cambio de la versión de **.NET Framework de destino** que se muestra para solicitar la confirmación de este cambio.

 En el caso de los proyectos de VB, puede redirigir el proyecto para usar el completo haciendo [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccionando **propiedades**. En la pestaña **compilar** , haga clic en el botón **Opciones de compilación avanzadas** . Seleccione **.NET Framework 4** en la **lista** versión de .NET Framework de destino y, a continuación, haga clic en **Aceptar**. Haga clic en el botón **sí** en el cuadro de diálogo de cambio de la versión de **.NET Framework de destino** que se muestra pidiéndole que confirme este cambio.

 El diseñador de actividades **Interop** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie de, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una <xref:System.Activities.Statements.Interop> actividad con un valor **displayName** predeterminado de Interop. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **Interop** o en el cuadro **displayName** de la cuadrícula de propiedades.

 Haga clic en el botón **para examinar...** texto del cuadro **ActivityType** , ya sea en el diseñador de actividades **Interop**  o en la cuadrícula de propiedades, para abrir el cuadro de diálogo **examinar y seleccionar un tipo .net** . Solo se muestran los tipos para actividades de flujo de trabajo 3.0 o de flujo de trabajo 3.5 (es decir, los tipos derivados de <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] Use este cuadro para especificar un tipo, vea el tema [examinar y seleccionar un tipo de .net](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) .

### <a name="the-interop-properties"></a>Propiedades Interop
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Interop> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Interop>. El valor predeterminado es Interop. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Verdadero|Especifica el tipo de la actividad que contiene la actividad <xref:System.Activities.Statements.Interop>. Este tipo especificado debe derivar de <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Consulte también
 [Migración](../workflow-designer/migration-activity-designers.md)