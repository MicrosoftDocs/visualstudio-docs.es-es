---
title: Using the Legacy Workflow Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2fa11cd0b29f3b8ee6008b8c0b3369b16812f0e5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302781"
---
# <a name="using-the-legacy-workflow-designer"></a>Usar el Diseñador de flujo de trabajo heredado
El [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)] se puede usar para tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 It is accessed by selecting either the **.NET Framework 3.0** option or the **.NET Framework 3.5** option in the drop down list at the top of the **New Project** window. The default option in [!INCLUDE[vs2010](../includes/vs2010-md.md)] is **.NET Framework 4** which is used to create [!INCLUDE[wf](../includes/wf-md.md)] applications that target the [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] proporciona una manera de crear gráficamente aplicaciones de [!INCLUDE[wf](../includes/wf-md.md)] mediante la conocida interfaz de usuario de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. [!INCLUDE[wf](../includes/wf-md.md)] las aplicaciones de flujo de trabajo están formadas por pasos de proceso de flujo de trabajo denominados actividades. To create a workflow, compose activities on the design surface by dragging their respective activity designers from **Toolbox** onto the design surface.

 En la siguiente tabla se enumeran las características clave de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para Windows Workflow Foundation.

|Característica|Descripción|
|-------------|-----------------|
|Arrastrar y colocar actividad|Drag activities from the **Toolbox** onto the design surface to create a workflow.|
|Examinador de propiedades|The standard **Properties** window in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] is used to configure the properties of an activity.|
|Zoom|The binoculars **Zoom Level** icon is located below the vertical scroll bar on the right side of the design surface. Click the binoculars and select a zoom percentage to cause the workflow graphic to zoom in or out. You can also use the **Pan** icon magnifying glass cursor options to zoom in and out.|
|Movimiento panorámico|The **Pan** icon, a circle that contains four crossed arrows pointing in four directions, is located below the vertical scroll bar on the right side of the design surface just below the binoculars zoom icon. Si hace clic en el icono de panorámica, aparece un menú emergente con las opciones de cursor siguientes:<br /><br /> -   The **Zoom In** magnifying glass cursor lets you zoom in by clicking the design surface.<br />-   The **Zoom Out** magnifying glass cursor lets you zoom out by clicking the design surface.<br />-   The **Navigation Tool** hand cursor lets you "grab" and shift the view of a workflow in the design surface.<br />-   The **Default** arrow cursor lets you switch from the other cursors back to the default arrow cursor.|
|Desplazamiento automático|Si tiene un flujo de trabajo grande, podría desear colocar una actividad más allá de la presentación visible del área de superficie de diseño. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] le permite arrastrar una actividad hacia el borde de la superficie de diseño más cercano al lugar donde desea colocar la actividad. La vista de superficie de diseño se desplaza automáticamente en esa dirección.|
|Etiquetas inteligentes|Las actividades que no se configuran totalmente o cuya configuración no sea válida se marcan con un icono de signo de exclamación. Puede hacer clic en el icono y ver una lista desplegable con las necesidades de configuración de la actividad. You can then use the **Properties** window to configure the activity appropriately. Cuando todas las propiedades son válidas para la actividad, el icono de signo de exclamación desaparece.|

## <a name="in-this-section"></a>En esta sección
 [Ventanas de flujo de trabajo de Visual Studio (heredado)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)

 [Vistas de flujos de trabajo secuenciales (heredado)](../workflow-designer/sequential-workflow-views-legacy.md)

 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)

 [Usar temas en los flujos de trabajo (heredado)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [Usar el diseñador de flujo de trabajo de máquina de estados heredado](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [Usar el diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md)

 [Ayuda de la interfaz de usuario del diseñador heredado para Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>Vea también
 [Developing Workflows](https://go.microsoft.com/fwlink?LinkID=65010)