---
title: "Cómo: Crear plantillas de proyectos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 603cfdd3a52163959ed223952994d3e8e4147298
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-project-templates"></a>Cómo: Crear plantillas de proyectos
Este procedimiento le permite crear una plantilla con el Asistente **Exportar plantilla**, que empaqueta su plantilla en un archivo .zip. También puede crear plantillas en el formato de archivo VSIX para obtener una implementación mejorada con la extensión del Asistente Exportar plantilla, o con las plantillas que se incluyen en [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)], o puede crear plantillas manualmente.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Para crear una plantilla de proyecto personalizada con el Asistente Exportar plantilla estándar  
  
1.  Cree un proyecto.  
  
    > [!NOTE]
    >  Use solo caracteres de identificador válidos al asignar un nombre al proyecto que será el origen de una plantilla. Una plantilla exportada desde un proyecto denominado con caracteres no válidos puede provocar errores de compilación en futuros proyectos basados en la plantilla. Para obtener más información sobre los caracteres de identificador válidos, vea [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
2.  Modifique el proyecto hasta que esté listo para exportarse como una plantilla.  
  
3.  Modifique los archivos de código según corresponda para indicar dónde debe aplicarse el reemplazo de parámetros. Para obtener más información sobre el reemplazo de parámetros, vea [Cómo: Sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  En el menú **Proyecto**, haga clic en **Exportar plantilla**. Se abre el Asistente **Exportar plantilla**.  
  
5.  Haga clic en **Plantilla de proyecto**.  
  
6.  Si tiene más de un proyecto en su solución actual, seleccione los proyectos que quiere exportar a una plantilla.  
  
7.  Haga clic en **Siguiente**.  
  
8.  Seleccione un icono y una imagen de vista previa para su plantilla. Estos aparecerán en el cuadro de diálogo **Nuevo proyecto**.  
  
9. Escriba un nombre de plantilla y una descripción.  
  
10. Haga clic en **Finalizar**. Su proyecto se exporta en un archivo .zip y se coloca en la ubicación de salida especificada, y, si se selecciona, se importa en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Si tiene [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalado, puede ajustar la plantilla terminada en un archivo .vsix para su implementación con la plantilla **Proyecto VSIX**. Para obtener más información, vea [Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md)
