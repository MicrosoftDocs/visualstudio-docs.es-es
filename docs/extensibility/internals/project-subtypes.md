---
title: "Subtipos de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [Visual Studio SDK] subtipos"
  - "subtipos de proyecto [Visual Studio SDK]"
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Subtipos de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Subtipos de proyecto le permiten personalizar o toque el comportamiento de los sistemas del proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Las personalizaciones incluyen guardar datos adicionales en el archivo de proyecto, agregar o filtrar elementos en el **Agregar nuevo elemento** cuadro de diálogo, controlar cómo se depuran e implementados, ensamblados y ampliar el proyecto **páginas de propiedades** cuadro de diálogo. VSPackages implementar mediante la agregación de COM de subtipos de proyecto.  
  
> [!NOTE]
>  El sistema de proyecto de Visual C\+\+ no admite los subtipos de proyecto.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa subtipos de proyecto para implementar los proyectos de SQL Server y dispositivos inteligentes.  
  
## En esta sección  
 [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)  
 Describe el concepto de subtipos de proyecto.  
  
 [Secuencia de inicialización de subtipos de proyecto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Describe la secuencia de inicialización del subtipo de proyecto mediante programación por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno.  
  
 [Propiedades y métodos extendidos subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Proporciona una descripción detallada de las funciones y métodos extendidos con más frecuencia mediante el uso de subtipos de proyecto.  
  
 [Conservar los datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Describe cómo conservar los datos en un archivo de proyecto y cómo usar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> para mantener los datos en el archivo de proyecto a través de los niveles de agregación del subtipo de proyecto.  
  
 [Interfaz de usuario de propiedades de proyecto](../../extensibility/internals/project-property-user-interface.md)  
 Describe cómo los subtipos de proyecto pueden modificar el proyecto **páginas de propiedades** cuadro de diálogo.  
  
 [Extender el modelo de objetos del proyecto de Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Proporciona información acerca de cómo los subtipos de proyecto pueden utilizar extensores de automatización para ampliar el modelo de objetos de automatización.  
  
 [Contribuir a la Add New Item Dialog Box](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Describe cómo agregar elementos a la **Agregar nuevo elemento** cuadro de diálogo.  
  
 [Guardar datos en archivos de proyecto](../../extensibility/saving-data-in-project-files.md)  
 Explica cómo un subtipo de proyecto puede guardar y recuperar datos específicos del subtipo en el archivo de proyecto mediante el marco de paquete administrados \(MPF\).  
  
 [Control especializado de implementación](../../extensibility/internals/handling-specialized-deployment.md)  
 Explica cómo subtipos de proyecto pueden proporcionar el comportamiento de implementación especializada implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz.  
  
 [Agregar y quitar páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)  
 Describe la adición y eliminación de páginas de propiedades en el Diseñador de proyectos.  
  
## Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas que detallan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos.