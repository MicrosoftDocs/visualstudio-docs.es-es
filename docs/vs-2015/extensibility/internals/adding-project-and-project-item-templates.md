---
title: Agregar el proyecto y plantillas de elemento de proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203862"
---
# <a name="adding-project-and-project-item-templates"></a>Adición de plantillas de proyecto y de elementos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al crear sus propios tipos de proyecto, debe proporcionar soporte técnico para agregar nuevos proyectos y elementos de proyecto mediante el estándar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrado cuadros de diálogo (IDE) del entorno de desarrollo. Los temas siguientes describen las distintas técnicas para agregar proyectos y elementos de proyecto.  
  
## <a name="in-this-section"></a>En esta sección  
 [Contexto del proyecto](../../extensibility/internals/project-context.md)  
 Explica que el proyecto proporciona la mayor parte de la información de contexto para lo que ocurre en el entorno.  
  
 [Prioridad del proyecto](../../extensibility/internals/project-priority.md)  
 Explica que un elemento de proyecto suele ser un miembro de un proyecto para ayudar a evitar la ambigüedad sobre qué proyecto se usa para abrir el elemento.  
  
 [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)  
 Proporciona información acerca de los dos tipos de editores que pueden usarse para abrir archivos en un proyecto y el rol reproduce el proyecto para determinar qué editor usar cuando se abre un elemento de proyecto.  
  
 [Registro de plantillas para proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explica lo que ocurre cuando un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se crea el proyecto.  
  
 [Adición de elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explica el proceso para agregar elementos a la **Agregar nuevo elemento** cuadro de diálogo.  
  
 [Adición de directorios al cuadro de diálogo Nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Proporciona un ejemplo de cómo registrar un nuevo directorio que contiene las plantillas personalizadas que se puso a disposición un VSPackage.  
  
 [Adición directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Proporciona un ejemplo de cómo registrar un nuevo conjunto de directorios para la **Agregar nuevo elemento** cuadro de diálogo.  
  
 [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Enumera los diferentes tipos de elementos de comando que se usan para ampliar sistemas del proyecto.  
  
 [CATID para los objetos que se utilizan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Enumera el CATID para los objetos que se utilizan para extender [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] sistemas del proyecto.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Procedimientos: Abrir editores específicos de proyecto](../../extensibility/how-to-open-project-specific-editors.md)  
 Proporciona instrucciones paso a paso para abrir un elemento intrínsecamente enlazado a un editor específico para un proyecto.  
  
 [Cómo: Abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)  
 Proporciona instrucciones paso a paso para abrir un editor estándar.  
  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)  
 Proporciona vínculos a temas conceptuales del subtipo de proyecto. Subtipos de proyecto extienden existente [!INCLUDE[csprcs](../../includes/csprcs-md.md)] y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] proyectos.  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.
