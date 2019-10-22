---
title: Subtipos de proyecto | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aede76a39506f74c39d9ec63ed4bb4a410d1013c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328104"
---
# <a name="project-subtypes"></a>Subtipos de proyecto
Subtipos de proyecto le permiten personalizar o flavor el comportamiento de los sistemas del proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Las personalizaciones incluyen guardando datos adicionales en el archivo de proyecto, agrega o filtra los elementos de la **Agregar nuevo elemento** cuadro de diálogo, controlar cómo se depura e implementados, los ensamblados y ampliando el proyecto **propiedad Páginas** cuadro de diálogo. Los paquetes VSPackage implementar subtipos de proyecto mediante agregación COM.

> [!NOTE]
> El sistema de proyectos de Visual C++ no admite subtipos de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa subtipos de proyecto para implementar los proyectos de SQL Server y Smart Device.

## <a name="in-this-section"></a>En esta sección
- [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)

 Describe el concepto de subtipos de proyecto.

- [Secuencia de inicialización de subtipos de proyecto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Describe la secuencia de inicialización del subtipo de proyecto mediante programación por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno.

- [Propiedades y métodos ampliados por subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Proporciona descripciones detalladas de las características y los métodos con más frecuencia extendidos mediante el uso de subtipos de proyecto.

- [Conservación de datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Describe cómo conservar los datos en un archivo de proyecto y cómo usar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> para mantener los datos en el archivo de proyecto entre los niveles de agregación del subtipo de proyecto.

- [Interfaz de usuario de propiedades de proyecto](../../extensibility/internals/project-property-user-interface.md)

 Se describe cómo los subtipos de proyecto pueden modificar el proyecto **páginas de propiedades** cuadro de diálogo.

- [Ampliación del modelo de objetos del proyecto de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Proporciona información sobre cómo subtipos de proyecto pueden usar extensores de automatización para extender el modelo de objetos de automatización.

- [Contribución al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 Describe cómo agregar elementos a la **Agregar nuevo elemento** cuadro de diálogo.

- [Guardado de datos en archivos de proyecto](../../extensibility/saving-data-in-project-files.md)

 Explica cómo puede guardar y recuperar datos específicos del subtipo en el archivo de proyecto mediante el uso de Managed Package Framework (MPF) un subtipo de proyecto.

- [Control de implementación especializada](../../extensibility/internals/handling-specialized-deployment.md)

 Explica cómo subtipos de proyecto pueden proporcionar el comportamiento de implementación especializada implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz.

- [Adición y eliminación de páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)

 Describe la adición y eliminación de páginas de propiedades en el Diseñador de proyectos.

## <a name="related-sections"></a>Secciones relacionadas
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona vínculos a temas que detallan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos.