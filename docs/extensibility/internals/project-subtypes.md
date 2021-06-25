---
title: Subtipos de proyecto | Microsoft Docs
description: Obtenga información sobre cómo los subtipos de proyecto permiten personalizar el comportamiento de los sistemas de proyecto de Visual Studio. Los VSPackages implementan subtipos de proyecto mediante la agregación COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd0f959d300fdc797d9e42d581a163b8b0892591
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903598"
---
# <a name="project-subtypes"></a>Subtipos de proyecto
Los subtipos de proyecto permiten personalizar o personalizar el comportamiento de los sistemas de proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Las personalizaciones incluyen guardar datos adicionales en el  archivo de proyecto, agregar o filtrar elementos en el cuadro  de diálogo Agregar nuevo elemento, controlar cómo se depuran e implementan los ensamblados y extender el cuadro de diálogo Páginas de propiedades del proyecto. Los VSPackages implementan subtipos de proyecto mediante la agregación COM.

> [!NOTE]
> El Visual C++ proyecto no admite subtipos de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa subtipos de proyecto para implementar SQL Server y proyectos de dispositivo inteligente.

## <a name="in-this-section"></a>En esta sección

- [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)

  Describe el concepto de subtipos de proyecto.

- [Secuencia de inicialización de subtipos de proyecto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  Describe la secuencia de inicialización del subtipo de proyecto mediante programación por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno.

- [Propiedades y métodos ampliados por subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  Proporciona descripciones detalladas de las características y métodos que se extienden con más frecuencia mediante subtipos de proyecto.

- [Conservación de datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  Describe cómo conservar los datos en un archivo de proyecto y cómo usar para mantener los datos del archivo de proyecto en los niveles de agregación <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> del subtipo del proyecto.

- [Interfaz de usuario de propiedades de proyecto](../../extensibility/internals/project-property-user-interface.md)

  Describe cómo los subtipos de proyecto pueden modificar el cuadro de diálogo Páginas **de propiedades** del proyecto.

- [Ampliación del modelo de objetos del proyecto de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  Proporciona información sobre cómo los subtipos de proyecto pueden usar extensores de Automation para ampliar el modelo de objetos de automatización.

- [Contribución al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  Describe cómo agregar elementos al cuadro **de diálogo Agregar** nuevo elemento.

- [Guardado de datos en archivos de proyecto](../../extensibility/saving-data-in-project-files.md)

  Explica cómo un subtipo de proyecto puede guardar y recuperar datos específicos del subtipo en el archivo de proyecto mediante Managed Package Framework (MPF).

- [Control de implementación especializada](../../extensibility/internals/handling-specialized-deployment.md)

  Explica cómo los subtipos de proyecto pueden proporcionar un comportamiento de implementación especializado mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz .

- [Adición y eliminación de páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)

  Describe cómo agregar y quitar páginas de propiedades en el Diseñador de proyectos.

## <a name="related-sections"></a>Secciones relacionadas

- [Tipos de proyecto](../../extensibility/internals/project-types.md)

  Proporciona vínculos a temas que detallan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] los proyectos.
