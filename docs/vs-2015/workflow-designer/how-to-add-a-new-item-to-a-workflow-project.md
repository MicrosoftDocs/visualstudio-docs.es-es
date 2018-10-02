---
title: 'Cómo: agregar un nuevo elemento a un proyecto de flujo de trabajo | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 1779fa4f3f644913bfe39164e707dfee4673502b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574033"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Cómo agregar un nuevo elemento a un proyecto de flujo de trabajo
Después de haber creado un proyecto de flujo de trabajo, puede agregar actividades, diseñadores y otros elementos conocidos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] al proyecto.  
  
 En la tabla siguiente se enumeran los elementos de [!INCLUDE[wf](../includes/wf-md.md)] que puede agregar a un proyecto de flujo de trabajo.  
  
|Name|Descripción|  
|----------|-----------------|  
|Actividad|Actividad que va a estar formada por otras actividades. Al seleccionar esta opción agrega el mismo archivo XAML al proyecto que obtendría cuando se selecciona el **biblioteca de actividades** plantilla para un nuevo proyecto. [!INCLUDE[crabout](../includes/crabout-md.md)] en este procedimiento, consulte [Cómo: crear una biblioteca de actividades](../workflow-designer/how-to-create-an-activity-library.md).|  
|Diseñador de actividad|Diseñador que se usa para personalizar la experiencia en tiempo de diseño de una actividad. Si selecciona este elemento agrega los mismos archivos al proyecto que obtendría cuando se selecciona el **biblioteca del Diseñador de actividad** plantilla para un nuevo proyecto. [!INCLUDE[crabout](../includes/crabout-md.md)] en este procedimiento, consulte [Cómo: crear una biblioteca del Diseñador de actividades](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Actividad de código|Actividad con lógica de ejecución escrita en código. Ya se ha generado automáticamente un archivo de código fuente con invalidación del método <xref:System.Activities.CodeActivity.Execute%2A>.|  
|Servicio de flujo de trabajo WCF|Servicio de [!INCLUDE[indigo2](../includes/indigo2-md.md)] compilado mediante actividades de flujo de trabajo. Si selecciona este elemento agrega los mismos archivos al proyecto que obtendría cuando se selecciona el **aplicación de servicio de flujo de trabajo de WCF** plantilla para un nuevo proyecto. [!INCLUDE[crabout](../includes/crabout-md.md)] en este procedimiento, consulte [Cómo: crear una aplicación de servicio de flujo de trabajo de WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>Para agregar un nuevo elemento a un proyecto de flujo de trabajo  
  
1.  En el **proyecto** menú, haga clic en **Agregar nuevo elemento...** .  
  
     El **agregar un nuevo elemento** abre el cuadro de diálogo.  
  
2.  En el **plantillas instaladas** panel, seleccione **flujo de trabajo** grupo.  
  
3.  Seleccione uno de los cuatro elementos. En la tabla anterior aparecen las selecciones disponibles.  
  
4.  Escriba un nombre adecuado para el elemento en el **nombre** cuadro en la parte inferior del cuadro de diálogo.  
  
5.  Haga clic en **agregar** para agregar el elemento al proyecto de flujo de trabajo actual.  
  
## <a name="see-also"></a>Vea también  
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)