---
title: Adición de plantillas de proyecto y elemento de proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710205"
---
# <a name="add-project-and-project-item-templates"></a>Agregar plantillas de proyecto y elemento de proyecto
Al crear sus propios tipos de proyecto, debe proporcionar compatibilidad para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] agregar nuevos proyectos y elementos de proyecto mediante los cuadros de diálogo de entorno de desarrollo integrado estándar (IDE). En los temas siguientes se describen diferentes técnicas para agregar proyectos y elementos de proyecto.

## <a name="in-this-section"></a>En esta sección
- [Contexto del proyecto](../../extensibility/internals/project-context.md)

 Explica que el proyecto proporciona la mayor parte de la información de contexto para lo que sucede en el entorno.

- [Prioridad del proyecto](../../extensibility/internals/project-priority.md)

 Explica que un elemento de proyecto suele ser miembro de un proyecto para ayudar a evitar la ambiguedad sobre qué proyecto se usa para abrir el elemento.

- [Proyecto de Archivos Varios](../../extensibility/internals/miscellaneous-files-project.md)

 Proporciona información sobre los dos tipos de editores que se pueden usar para abrir archivos en un proyecto y el papel que desempeña el proyecto para determinar qué editor usar cuando se abre un elemento de proyecto.

- [Registrar plantillas de proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)

 Explica lo que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ocurre cuando se crea un proyecto.

- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Explica el proceso para agregar elementos al cuadro de diálogo **Agregar nuevo elemento.**

- [Agregar directorios al cuadro de diálogo Nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Proporciona un ejemplo de registro de un nuevo directorio que contiene plantillas personalizadas disponibles por un VSPackage.

- [Agregar directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Proporciona un ejemplo de registro de un nuevo conjunto de directorios para el **Agregar nuevo elemento** cuadro de diálogo.

- [Comandos definidos por IDE para ampliar los sistemas de proyectos](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Enumera los diferentes tipos de elementos de comando utilizados para ampliar los sistemas de proyecto.

- [CATID para objetos que se utilizan normalmente para extender proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Enumera los CATID para los [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]objetos que se utilizan para extender , [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] los sistemas de proyecto.

## <a name="related-sections"></a>Secciones relacionadas
- [Cómo: Abrir editores específicos de proyectos](../../extensibility/how-to-open-project-specific-editors.md)

 Proporciona instrucciones paso a paso para abrir un elemento enlazado intrínsecamente a un editor específico para un proyecto.

- [Cómo: Abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)

 Proporciona instrucciones paso a paso para abrir un editor estándar.

- [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)

 Proporciona vínculos a temas conceptuales de subtipo de proyecto. Los subtipos [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proyecto amplían los proyectos y los existentes.

- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.
