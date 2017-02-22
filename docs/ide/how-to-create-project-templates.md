---
title: "C&#243;mo: Crear plantillas de proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ExportTemplateWizard"
helpviewer_keywords: 
  - "plantillas de proyecto, crear"
  - "plantillas de proyecto, ubicaciones de plantillas personalizadas"
  - "plantillas de proyecto, archivos de metadatos"
  - "plantillas de Visual Studio, crear plantillas de proyecto"
  - "plantillas de Visual Studio, plantillas de proyecto"
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Crear plantillas de proyectos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este procedimiento permite crear una plantilla mediante el **Asistente para exportar plantillas**, que empaqueta la plantilla en un archivo .zip.  También puede crear plantillas con el formato de archivo VSIX para la implementación mejorada mediante la extensión del asistente para Exportar plantillas, o con las plantillas incluidas en [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)], o puede crear plantillas manualmente.  
  
### Para crear una plantilla de proyecto personalizada con el Asistente para exportar plantillas estándar  
  
1.  Cree un proyecto.  
  
    > [!NOTE]
    >  Cuando asigne un nombre a un proyecto que será el origen de una plantilla, use únicamente caracteres de identificador válidos.  Una plantilla exportada desde un proyecto cuyo nombre contenga caracteres no válidos puede producir errores de compilación en proyectos futuros que se basen en la plantilla.  Para obtener más información sobre los caracteres de identificador válidos, vea [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
2.  Edite el proyecto hasta que esté listo para ser exportado como una plantilla.  
  
3.  Según corresponda, edite los archivos de código para indicar dónde debería tener lugar la sustitución del parámetro.  Para obtener más información sobre la sustitución del parámetro, vea [Cómo: Sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  En el menú **Archivo**, haga clic en **Exportar plantilla**.  Se abrirá el **Asistente para exportar plantillas**.  
  
5.  Haga clic en **Plantilla de proyecto**.  
  
6.  Si tiene más de un proyecto en la solución actual, seleccione los proyectos que desee exportar a una plantilla.  
  
7.  Haga clic en **Siguiente**.  
  
8.  Seleccione un icono y una imagen de vista previa para su plantilla.  Éstos aparecerán en el cuadro de diálogo **Nuevo proyecto**.  
  
9. Escriba un nombre y una descripción de la plantilla.  
  
10. Haga clic en **Finalizar**.  El proyecto se exporta a un archivo .zip y se coloca en la ubicación de salida especificada; además, si se ha seleccionado, se importa a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Si tiene [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalado, puede encapsular la plantilla acabada en un archivo .vsix para la implementación utilizando la plantilla **Proyecto VSIX**.  Para obtener más información, vea [Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## Vea también  
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md)