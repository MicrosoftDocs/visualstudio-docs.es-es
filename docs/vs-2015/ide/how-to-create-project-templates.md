---
title: Procedimiento Crear plantillas de proyecto | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 918462bff3c2ac8dc57cb9c2c55a7d901707683c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051549"
---
# <a name="how-to-create-project-templates"></a>Procedimiento Crear plantillas de proyecto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este procedimiento le permite crear una plantilla con el Asistente **Exportar plantilla**, que empaqueta su plantilla en un archivo .zip. También puede crear plantillas en el formato de archivo VSIX para obtener una implementación mejorada con la extensión del Asistente Exportar plantilla, o con las plantillas que se incluyen en [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)], o puede crear plantillas manualmente.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Para crear una plantilla de proyecto personalizada con el Asistente Exportar plantilla estándar  
  
1. Cree un proyecto.  
  
    > [!NOTE]
    >  Use solo caracteres de identificador válidos al asignar un nombre al proyecto que será el origen de una plantilla. Una plantilla exportada desde un proyecto denominado con caracteres no válidos puede provocar errores de compilación en futuros proyectos basados en la plantilla. Para obtener más información sobre los caracteres de identificador válidos, vea [Nombres de elementos declarados](http://msdn.microsoft.com/library/09d8843b-c0dc-4afe-9dab-87c439a69e66).  
  
2. Modifique el proyecto hasta que esté listo para exportarse como una plantilla.  
  
3. Modifique los archivos de código según corresponda para indicar dónde debe aplicarse el reemplazo de parámetros. Para obtener más información sobre el reemplazo de parámetros, vea [Cómo: Sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4. En el menú **Archivo**, haga clic en **Exportar plantilla**. Se abre el Asistente **Exportar plantilla**.  
  
5. Haga clic en **Plantilla de proyecto**.  
  
6. Si tiene más de un proyecto en su solución actual, seleccione los proyectos que quiere exportar a una plantilla.  
  
7. Haga clic en **Siguiente**.  
  
8. Seleccione un icono y una imagen de vista previa para su plantilla. Estos aparecerán en el cuadro de diálogo **Nuevo proyecto**.  
  
9. Escriba un nombre de plantilla y una descripción.  
  
10. Haga clic en **Finalizar**. Su proyecto se exporta en un archivo .zip y se coloca en la ubicación de salida especificada, y, si se selecciona, se importa en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Si tiene [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] instalado, puede ajustar la plantilla terminada en un archivo .vsix para su implementación con la plantilla **Proyecto VSIX**. Para obtener más información, vea [Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [Cómo: crear plantillas de elemento](../ide/how-to-create-item-templates.md)
