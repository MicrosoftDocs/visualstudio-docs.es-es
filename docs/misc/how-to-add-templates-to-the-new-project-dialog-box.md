---
title: "C&#243;mo: Agregar plantillas al cuadro de di&#225;logo Nuevo proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cuadros de diálogo, agregar plantillas a proyecto"
  - "proyectos [SDK de Visual Studio], agregar plantillas al cuadro de diálogo"
  - "plantillas [Visual Studio], agregar al cuadro de diálogo de proyecto"
ms.assetid: fd044681-e666-410d-815c-33db923ed888
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# C&#243;mo: Agregar plantillas al cuadro de di&#225;logo Nuevo proyecto
Durante la instalación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], se instala una serie de plantillas de proyecto predefinidas. Para obtener una lista completa de plantillas de proyecto predefinidas, vea [NIB Crear proyectos a partir de plantillas](http://msdn.microsoft.com/es-es/7c36d86a-6b79-4480-8228-0f925f1204b2). Además de las plantillas de proyecto predeterminadas puede crear plantillas de proyecto personalizadas específicas de subtipo. Por ejemplo, el subtipo **Smart Device** proporciona sus propias plantillas para proyectos [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Para obtener instrucciones sobre cómo crear una plantilla personalizada, vea [Cómo: Crear plantillas de proyectos](../ide/how-to-create-project-templates.md).  
  
## Agregar una plantilla al cuadro de diálogo Nuevo proyecto  
  
#### Para agregar una plantilla al cuadro de diálogo Nuevo proyecto  
  
1.  Cree una plantilla, incluido el archivo MyTemplate.vstemplate.  
  
2.  Seleccione los archivos de la plantilla \(incluido el archivo .stemplate\), haga clic con el botón secundario en ellos, haga clic en **Enviar a** y, a continuación, en **Carpetas comprimidas \(en zip\)**. Los archivos que ha extraído previamente se comprimen en un archivo .zip.  
  
 Coloque el archivo .zip de plantilla en **%USERPROFILE%\\Documents\\Visual Studio 2015\\Templates\\ProjectTemplates**.  
  
## Vea también  
 [Project Subtypes](d235b47b-cf11-4d47-a63f-e33d9d16105d2044a030-0795-4940-bd65-a6e44de98a0f)   
 [NIB: Plantillas de Visual Studio](http://msdn.microsoft.com/es-es/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Contribuir a la Add New Item Dialog Box](../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)