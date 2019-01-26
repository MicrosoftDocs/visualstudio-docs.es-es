---
title: Agregar el proyecto y plantillas de elemento de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8315626f346a96d907686e009af006e2170e072c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929567"
---
# <a name="add-project-and-project-item-templates"></a>Agregar proyecto y plantillas de elemento de proyecto
Al crear sus propios tipos de proyecto, debe proporcionar soporte técnico para agregar nuevos proyectos y elementos de proyecto mediante el estándar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrado cuadros de diálogo (IDE) del entorno de desarrollo. Los temas siguientes describen las distintas técnicas para agregar proyectos y elementos de proyecto.  
  
## <a name="in-this-section"></a>En esta sección  
 [Contexto del proyecto](../../extensibility/internals/project-context.md)  
 Explica que el proyecto proporciona la mayor parte de la información de contexto para lo que ocurre en el entorno.  
  
 [Prioridad del proyecto](../../extensibility/internals/project-priority.md)  
 Explica que un elemento de proyecto suele ser un miembro de un proyecto para ayudar a evitar la ambigüedad sobre qué proyecto se usa para abrir el elemento.  
  
 [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)  
 Proporciona información acerca de los dos tipos de editores que pueden usarse para abrir archivos en un proyecto y el rol reproduce el proyecto para determinar qué editor usar cuando se abre un elemento de proyecto.  
  
 [Registrar las plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explica lo que ocurre cuando un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se crea el proyecto.  
  
 [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explica el proceso para agregar elementos a la **Agregar nuevo elemento** cuadro de diálogo.  
  
 [Agregar directorios al cuadro de diálogo nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Proporciona un ejemplo de cómo registrar un nuevo directorio que contiene las plantillas personalizadas que se puso a disposición un VSPackage.  
  
 [Agregar directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Proporciona un ejemplo de cómo registrar un nuevo conjunto de directorios para la **Agregar nuevo elemento** cuadro de diálogo.  
  
 [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Enumera los diferentes tipos de elementos de comando que se usan para ampliar sistemas del proyecto.  
  
 [CATID para los objetos que se suelen usar para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Enumera el CATID para los objetos que se utilizan para extender [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sistemas del proyecto.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Cómo: Abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md)  
 Proporciona instrucciones paso a paso para abrir un elemento intrínsecamente enlazado a un editor específico para un proyecto.  
  
 [Cómo: Abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)  
 Proporciona instrucciones paso a paso para abrir un editor estándar.  
  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)  
 Proporciona vínculos a temas conceptuales del subtipo de proyecto. Subtipos de proyecto extienden existente [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proyectos.  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.