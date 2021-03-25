---
title: Subtipos de proyecto | Microsoft Docs
description: Obtenga información sobre cómo los subtipos de proyecto permiten personalizar el comportamiento de los sistemas de proyecto de Visual Studio. Los VSPackages implementan subtipos de proyecto mediante la agregación COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e1695bc79e38c7a9ebbda7736e57116123343f30
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064337"
---
# <a name="project-subtypes"></a>Subtipos de proyecto
Los subtipos de proyecto permiten personalizar o adaptar el comportamiento de los sistemas de proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Las personalizaciones incluyen el almacenamiento de datos adicionales en el archivo del proyecto, la adición o filtrado de elementos en el cuadro de diálogo **Agregar nuevo elemento** , el control de cómo se depuran y se implementan los ensamblados, y la extensión del cuadro de diálogo **páginas de propiedades** del proyecto. Los VSPackages implementan subtipos de proyecto mediante la agregación COM.

> [!NOTE]
> El sistema del proyecto Visual C++ no admite subtipos de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza subtipos de proyecto para implementar SQL Server y proyectos de Smart Device.

## <a name="in-this-section"></a>En esta sección

- [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)

  Describe el concepto de subtipos de proyecto.

- [Secuencia de inicialización de subtipos de proyecto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  Describe la secuencia de inicialización de subtipo de proyecto mediante programación por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno.

- [Propiedades y métodos ampliados por subtipos de proyecto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  Proporciona descripciones detalladas de las características y los métodos extendidos con más frecuencia mediante subtipos de proyecto.

- [Conservación de datos en el archivo de proyecto de MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  Describe cómo conservar los datos en un archivo de proyecto y cómo usar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> para mantener los datos en el archivo de proyecto en los niveles de agregación de subtipos de proyecto.

- [Interfaz de usuario de propiedades de proyecto](../../extensibility/internals/project-property-user-interface.md)

  Describe el modo en que los subtipos de proyecto pueden modificar el cuadro de diálogo **páginas de propiedades** del proyecto.

- [Ampliación del modelo de objetos del proyecto de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  Proporciona información sobre el modo en que los subtipos de proyecto pueden utilizar los extensores de automatización para extender el modelo de objetos de automatización.

- [Contribución al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  Describe cómo agregar elementos al cuadro de diálogo **Agregar nuevo elemento** .

- [Guardado de datos en archivos de proyecto](../../extensibility/saving-data-in-project-files.md)

  Explica cómo un subtipo de proyecto puede guardar y recuperar datos específicos del subtipo en el archivo de proyecto mediante el marco de trabajo de paquetes administrados (MPF).

- [Control de implementación especializada](../../extensibility/internals/handling-specialized-deployment.md)

  Explica cómo los subtipos de proyecto pueden proporcionar un comportamiento de implementación especializado implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz.

- [Adición y eliminación de páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)

  Describe cómo agregar y quitar páginas de propiedades en el diseñador de proyectos.

## <a name="related-sections"></a>Secciones relacionadas

- [Tipos de proyecto](../../extensibility/internals/project-types.md)

  Proporciona vínculos a temas en los que se detallan los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos.
