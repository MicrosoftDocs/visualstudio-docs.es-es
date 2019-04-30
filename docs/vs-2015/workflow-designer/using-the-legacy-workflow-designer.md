---
title: Usar el Diseñador de flujo de trabajo heredado | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 899f0b81055f67c323c2efb60a07280368dad321
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855844"
---
# <a name="using-the-legacy-workflow-designer"></a>Usar el Diseñador de flujo de trabajo heredado
El [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)] se puede usar para tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Se tiene acceso seleccionando el **.NET Framework 3.0** opción o el **.NET Framework 3.5** opción en la lista desplegable situada en la parte superior de la **nuevo proyecto** ventana. La opción predeterminada de [!INCLUDE[vs2010](../includes/vs2010-md.md)] es **.NET Framework 4** que se usa para crear [!INCLUDE[wf](../includes/wf-md.md)] aplicaciones que tienen como destino el [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].  
  
 [!INCLUDE[wfd2](../includes/wfd2-md.md)] proporciona una manera de crear gráficamente aplicaciones de [!INCLUDE[wf](../includes/wf-md.md)] mediante la conocida interfaz de usuario de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. [!INCLUDE[wf](../includes/wf-md.md)] las aplicaciones de flujo de trabajo están formadas por pasos de proceso de flujo de trabajo denominados actividades. Para crear un flujo de trabajo, cree actividades en la superficie de diseño arrastrando sus diseñadores de actividad correspondientes desde **cuadro de herramientas** a la superficie de diseño.  
  
 En la siguiente tabla se enumeran las características clave de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para Windows Workflow Foundation.  
  
|Característica|Descripción|  
|-------------|-----------------|  
|Arrastrar y colocar actividad|Arrastre las actividades desde el **cuadro de herramientas** a la superficie de diseño para crear un flujo de trabajo.|  
|Examinador de propiedades|El estándar **propiedades** ventana en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se usa para configurar las propiedades de una actividad.|  
|Zoom|Los prismáticos **nivel de Zoom** icono se encuentra debajo de la barra de desplazamiento vertical en el lado derecho de la superficie de diseño. Haga clic en los prismáticos y seleccione un porcentaje de zoom para ampliar o reducir el gráfico del flujo de trabajo. También puede usar el **Pan** opciones del cursor de lupa de icono para acercar y alejar.|  
|Movimiento panorámico|El **Pan** icono, un círculo que contiene cuatro flechas cruzadas que señalan cuatro direcciones, se encuentra debajo de la barra de desplazamiento vertical en el lado derecho de la superficie de diseño, debajo del icono de zoom de prismáticos. Si hace clic en el icono de panorámica, aparece un menú emergente con las opciones de cursor siguientes:<br /><br /> -El **acercar** cursor de lupa le permite acercar haciendo clic en la superficie de diseño.<br />-El **alejar** cursor de lupa le permite alejar haciendo clic en la superficie de diseño.<br />-El **herramienta de navegación** cursor de mano que le permite "agarrar" y desplazar la vista de un flujo de trabajo en la superficie de diseño.<br />-El **predeterminada** cursor de flecha le permite pasar de los demás cursores al cursor de flecha predeterminado.|  
|Desplazamiento automático|Si tiene un flujo de trabajo grande, podría desear colocar una actividad más allá de la presentación visible del área de superficie de diseño. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] le permite arrastrar una actividad hacia el borde de la superficie de diseño más cercano al lugar donde desea colocar la actividad. La vista de superficie de diseño se desplaza automáticamente en esa dirección.|  
|Etiquetas inteligentes|Las actividades que no se configuran totalmente o cuya configuración no sea válida se marcan con un icono de signo de exclamación. Puede hacer clic en el icono y ver una lista desplegable con las necesidades de configuración de la actividad. A continuación, puede usar el **propiedades** ventana para configurar la actividad correctamente. Cuando todas las propiedades son válidas para la actividad, el icono de signo de exclamación desaparece.|  
  
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
 [Desarrollar flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65010)