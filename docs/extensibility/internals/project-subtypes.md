---
title: Subtipos de proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71dab4767c806b44cbd1f9638738b4a13d6b2bcb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706406"
---
# <a name="project-subtypes"></a>Subtipos de proyecto
Los subtipos de proyecto permiten personalizar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dar sabor al comportamiento de los sistemas de proyecto de . Las personalizaciones incluyen guardar datos adicionales en el archivo de proyecto, agregar o filtrar elementos en el cuadro de diálogo **Agregar nuevo elemento,** controlar cómo se depuran e implementar los ensamblados y ampliar el cuadro de diálogo **Páginas** de propiedades del proyecto. VSPackages implementan subtipos de proyecto mediante la agregación COM.

> [!NOTE]
> El sistema de proyectos Visual C++ no admite subtipos de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utiliza subtipos de proyecto para implementar proyectos de SQL Server y Smart Device.

## <a name="in-this-section"></a>En esta sección
- [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)

 Describe el concepto de subtipos de proyecto.

- [Secuencia de inicialización de subtipos de proyecto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Describe la secuencia de inicialización [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de subtipo de proyecto mediante programación por entorno.

- [Propiedades y métodos ampliados por subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Proporciona descripciones detalladas de las características y métodos que se extienden con más frecuencia mediante subtipos de proyecto.

- [Conservación de datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Describe cómo conservar datos en un archivo <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> de proyecto y cómo usar para mantener los datos en el archivo de proyecto en los niveles de agregación de subtipos de proyecto.

- [Interfaz de usuario de propiedades de proyecto](../../extensibility/internals/project-property-user-interface.md)

 Describe cómo los subtipos de proyecto pueden modificar el cuadro de diálogo **Páginas** de propiedades del proyecto.

- [Ampliación del modelo de objetos del proyecto de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Proporciona información sobre cómo los subtipos de proyecto pueden utilizar los extensores de automatización para ampliar el modelo de objetos de automatización.

- [Contribución al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 Describe cómo agregar elementos al cuadro de diálogo **Agregar nuevo elemento.**

- [Guardado de datos en archivos de proyecto](../../extensibility/saving-data-in-project-files.md)

 Explica cómo un subtipo de proyecto puede guardar y recuperar datos específicos del subtipo en el archivo de proyecto mediante Managed Package Framework (MPF).

- [Control de implementación especializada](../../extensibility/internals/handling-specialized-deployment.md)

 Explica cómo los subtipos de proyecto pueden <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> proporcionar un comportamiento de implementación especializado mediante la implementación de la interfaz.

- [Adición y eliminación de páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)

 Describe cómo agregar y quitar páginas de propiedades en el Diseñador de proyectos.

## <a name="related-sections"></a>Secciones relacionadas
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona vínculos a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] temas que detallan proyectos.
