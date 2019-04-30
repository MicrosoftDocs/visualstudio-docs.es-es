---
title: Subtipos de proyecto | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5ad1e105d43c40782b13d8799b20626e57363c2f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421829"
---
# <a name="project-subtypes"></a>Subtipos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Subtipos de proyecto le permiten personalizar o flavor el comportamiento de los sistemas del proyecto de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Las personalizaciones incluyen guardando datos adicionales en el archivo de proyecto, agrega o filtra los elementos de la **Agregar nuevo elemento** cuadro de diálogo, controlar cómo se depura e implementados, los ensamblados y ampliando el proyecto **propiedad Páginas** cuadro de diálogo. Los paquetes VSPackage implementar subtipos de proyecto mediante agregación COM.  
  
> [!NOTE]
> El sistema de proyectos de Visual C++ no admite subtipos de proyecto. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usa subtipos de proyecto para implementar los proyectos de SQL Server y Smart Device.  
  
## <a name="in-this-section"></a>En esta sección  
 [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)  
 Describe el concepto de subtipos de proyecto.  
  
 [Secuencia de inicialización de subtipos de proyecto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Describe la secuencia de inicialización del subtipo de proyecto mediante programación por [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno.  
  
 [Propiedades y métodos ampliados por subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Proporciona descripciones detalladas de las características y los métodos con más frecuencia extendidos mediante el uso de subtipos de proyecto.  
  
 [Conservación de datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Describe cómo conservar los datos en un archivo de proyecto y cómo usar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> para mantener los datos en el archivo de proyecto entre los niveles de agregación del subtipo de proyecto.  
  
 [Interfaz de usuario de propiedades de proyecto](../../extensibility/internals/project-property-user-interface.md)  
 Se describe cómo los subtipos de proyecto pueden modificar el proyecto **páginas de propiedades** cuadro de diálogo.  
  
 [Ampliación del modelo de objetos del proyecto de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Proporciona información sobre cómo subtipos de proyecto pueden usar extensores de automatización para extender el modelo de objetos de automatización.  
  
 [Contribución al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Describe cómo agregar elementos a la **Agregar nuevo elemento** cuadro de diálogo.  
  
 [Guardado de datos en archivos de proyecto](../../extensibility/saving-data-in-project-files.md)  
 Explica cómo puede guardar y recuperar datos específicos del subtipo en el archivo de proyecto mediante el uso de Managed Package Framework (MPF) un subtipo de proyecto.  
  
 [Control de implementación especializada](../../extensibility/internals/handling-specialized-deployment.md)  
 Explica cómo subtipos de proyecto pueden proporcionar el comportamiento de implementación especializada implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz.  
  
 [Adición y eliminación de páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)  
 Describe la adición y eliminación de páginas de propiedades en el Diseñador de proyectos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas que detallan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proyectos.
