---
title: Subtipos de proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 21d7f013989607f7f5416a57829bc9b2b29b61d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="project-subtypes"></a>Subtipos de proyecto
Subtipos de proyecto le permiten personalizar o flavor el comportamiento de los sistemas del proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Personalizaciones incluyen guardar datos adicionales en el archivo de proyecto, agregar o filtrar elementos de la **Agregar nuevo elemento** cuadro de diálogo, controlar cómo se depuran e implementados, ensamblados y ampliar el proyecto **propiedad Páginas** cuadro de diálogo. VSPackages implementar mediante la agregación de COM de subtipos de proyecto.  
  
> [!NOTE]
>  El sistema de proyectos de Visual C++ no admite subtipos de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]por sí mismo utiliza subtipos de proyecto para implementar los proyectos de Smart Device y SQL Server.  
  
## <a name="in-this-section"></a>En esta sección  
 [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)  
 Describe el concepto de subtipos de proyecto.  
  
 [Secuencia de inicialización de subtipos de proyecto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Describe la secuencia de inicialización del subtipo de proyecto mediante programación por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno.  
  
 [Propiedades y métodos ampliados por subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Proporciona descripciones detalladas de las características y los métodos con más frecuencia extendidos con subtipos de proyecto.  
  
 [Conservación de datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Describe cómo conservar los datos en un archivo de proyecto y cómo usar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> para mantener los datos en el archivo de proyecto a través de los niveles de agregación del subtipo de proyecto.  
  
 [Interfaz de usuario de propiedades de proyecto](../../extensibility/internals/project-property-user-interface.md)  
 Describe cómo los subtipos de proyecto pueden modificar el proyecto **páginas de propiedades** cuadro de diálogo.  
  
 [Ampliación del modelo de objetos del proyecto de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Proporciona información acerca de cómo los subtipos de proyecto pueden utilizar extensores de automatización para ampliar el modelo de objetos de automatización.  
  
 [Contribución al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Describe cómo agregar elementos a la **Agregar nuevo elemento** cuadro de diálogo.  
  
 [Guardado de datos en archivos de proyecto](../../extensibility/saving-data-in-project-files.md)  
 Explica cómo un subtipo de proyecto puede guardar y recuperar datos específicos de subtipo en el archivo de proyecto mediante Managed Package Framework (MPF).  
  
 [Control de implementación especializada](../../extensibility/internals/handling-specialized-deployment.md)  
 Explica cómo subtipos de proyecto pueden proporcionar el comportamiento de implementación especializada implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz.  
  
 [Adición y eliminación de páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)  
 Describe agregando y quitando páginas de propiedades en el Diseñador de proyectos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas que detalla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos.