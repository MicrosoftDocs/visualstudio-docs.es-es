---
title: 'Cómo: agregar un nuevo elemento a un proyecto de flujo de trabajo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 004f079576b792fb76d596ee8ebac3f6f96f316e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656629"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Cómo agregar un nuevo elemento a un proyecto de flujo de trabajo
Después de haber creado un proyecto de flujo de trabajo, puede agregar actividades, diseñadores y otros elementos conocidos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] al proyecto.

 En la tabla siguiente se enumeran los elementos de [!INCLUDE[wf](../includes/wf-md.md)] que puede agregar a un proyecto de flujo de trabajo.

|Nombre|Descripción|
|----------|-----------------|
|Actividad|Actividad que va a estar formada por otras actividades. Al seleccionar este elemento, se agrega el mismo archivo XAML al proyecto que obtendría cuando se selecciona la plantilla **biblioteca de actividades** para un nuevo proyecto. [!INCLUDE[crabout](../includes/crabout-md.md)] en este procedimiento, consulte [Cómo: crear una biblioteca de actividades](../workflow-designer/how-to-create-an-activity-library.md).|
|Diseñador de actividad|Diseñador que se usa para personalizar la experiencia en tiempo de diseño de una actividad. Al seleccionar este elemento, se agregan los mismos archivos al proyecto que obtendría cuando se selecciona la plantilla **biblioteca del diseñador de actividad** para un nuevo proyecto. [!INCLUDE[crabout](../includes/crabout-md.md)] en este procedimiento, vea [Cómo: crear una biblioteca del diseñador de actividad](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Actividad de código|Actividad con lógica de ejecución escrita en código. Ya se ha generado automáticamente un archivo de código fuente con invalidación del método <xref:System.Activities.CodeActivity.Execute%2A>.|
|Servicio de flujo de trabajo WCF|Servicio de [!INCLUDE[indigo2](../includes/indigo2-md.md)] compilado mediante actividades de flujo de trabajo. Al seleccionar este elemento, se agregan los mismos archivos al proyecto que obtendría cuando se selecciona la plantilla **aplicación de servicio de flujo de trabajo WCF** para un nuevo proyecto. [!INCLUDE[crabout](../includes/crabout-md.md)] en este procedimiento, consulte [Cómo: crear una aplicación de servicio de flujo de trabajo WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Para agregar un nuevo elemento a un proyecto de flujo de trabajo

1. En el menú **proyecto** , haga clic en **Agregar nuevo elemento.**...

     Se abre el cuadro de diálogo **Agregar un nuevo elemento** .

2. En el panel **plantillas instaladas** , seleccione grupo de **flujo de trabajo** .

3. Seleccione uno de los cuatro elementos. En la tabla anterior aparecen las selecciones disponibles.

4. Escriba un nombre apropiado para el elemento en el cuadro **nombre** situado en la parte inferior del cuadro de diálogo.

5. Haga clic en **Agregar** para agregar el elemento al proyecto de flujo de trabajo actual.

## <a name="see-also"></a>Consulte también
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)