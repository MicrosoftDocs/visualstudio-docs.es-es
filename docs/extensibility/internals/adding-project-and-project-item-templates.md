---
title: Agregar plantillas de proyecto y de elemento de proyecto | Microsoft Docs
description: Obtenga información sobre cómo agregar plantillas de proyecto y de elemento de proyecto a los cuadros de diálogo del entorno de desarrollo integrado (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ff54e24408577ba8bfbf553a5c641eab2d15814
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906232"
---
# <a name="add-project-and-project-item-templates"></a>Agregar plantillas de proyecto y de elemento de proyecto
Cuando cree sus propios tipos de proyecto, debe proporcionar compatibilidad para agregar nuevos proyectos y elementos de proyecto mediante los cuadros de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diálogo del entorno de desarrollo integrado (IDE) estándar. En los temas siguientes se describen las distintas técnicas para agregar proyectos y elementos de proyecto.

## <a name="in-this-section"></a>En esta sección
- [Contexto del proyecto](../../extensibility/internals/project-context.md)

 Explica que el proyecto proporciona la mayor parte de la información de contexto de lo que ocurre en el entorno.

- [Prioridad del proyecto](../../extensibility/internals/project-priority.md)

 Explica que un elemento de proyecto suele ser miembro de un proyecto para evitar la ambigüedad sobre qué proyecto se usa para abrir el elemento.

- [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)

 Proporciona información sobre los dos tipos de editores que se pueden usar para abrir archivos en un proyecto y el rol que desempeña el proyecto para determinar qué editor se debe utilizar cuando se abre un elemento de proyecto.

- [Registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)

 Explica lo que ocurre cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se crea un proyecto.

- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Explica el proceso para agregar elementos al cuadro de diálogo **Agregar nuevo elemento** .

- [Agregar directorios al cuadro de diálogo nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Proporciona un ejemplo de cómo registrar un nuevo directorio que contenga plantillas personalizadas que haya disponible un VSPackage.

- [Agregar directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Proporciona un ejemplo de registro de un nuevo conjunto de directorios para el cuadro de diálogo **Agregar nuevo elemento** .

- [Comandos definidos por el IDE para la extensión de sistemas de proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Enumera los distintos tipos de elementos de comandos que se usan para extender los sistemas de proyecto.

- [CATID para los objetos que se utilizan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Muestra los CATID de los objetos que se usan para extender [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] los sistemas de proyectos de, y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .

## <a name="related-sections"></a>Secciones relacionadas
- [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md)

 Proporciona instrucciones paso a paso para abrir un elemento enlazado de forma intrínseca a un editor específico para un proyecto.

- [Cómo: abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)

 Proporciona instrucciones paso a paso para abrir un editor estándar.

- [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)

 Proporciona vínculos a temas conceptuales del subtipo de proyecto. Los subtipos de proyecto extienden los [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proyectos y existentes [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .

- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.
