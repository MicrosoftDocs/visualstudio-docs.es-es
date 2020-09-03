---
title: Agregar plantillas de proyecto y de elemento de proyecto | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203862"
---
# <a name="adding-project-and-project-item-templates"></a>Adición de plantillas de proyecto y de elementos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando cree sus propios tipos de proyecto, debe proporcionar compatibilidad para agregar nuevos proyectos y elementos de proyecto mediante los cuadros de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] diálogo del entorno de desarrollo integrado (IDE) estándar. En los temas siguientes se describen las distintas técnicas para agregar proyectos y elementos de proyecto.  
  
## <a name="in-this-section"></a>En esta sección  
 [Contexto del proyecto](../../extensibility/internals/project-context.md)  
 Explica que el proyecto proporciona la mayor parte de la información de contexto de lo que ocurre en el entorno.  
  
 [Prioridad del proyecto](../../extensibility/internals/project-priority.md)  
 Explica que un elemento de proyecto suele ser miembro de un proyecto para evitar la ambigüedad sobre qué proyecto se usa para abrir el elemento.  
  
 [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)  
 Proporciona información sobre los dos tipos de editores que se pueden usar para abrir archivos en un proyecto y el rol que desempeña el proyecto para determinar qué editor se debe utilizar cuando se abre un elemento de proyecto.  
  
 [Registro de plantillas para proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explica lo que ocurre cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se crea un proyecto.  
  
 [Adición de elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explica el proceso para agregar elementos al cuadro de diálogo **Agregar nuevo elemento** .  
  
 [Adición de directorios al cuadro de diálogo Nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Proporciona un ejemplo de cómo registrar un nuevo directorio que contenga plantillas personalizadas que haya disponible un VSPackage.  
  
 [Adición de directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Proporciona un ejemplo de registro de un nuevo conjunto de directorios para el cuadro de diálogo **Agregar nuevo elemento** .  
  
 [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Enumera los distintos tipos de elementos de comandos que se usan para extender los sistemas de proyecto.  
  
 [CATID para los objetos que se usan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Muestra los CATID de los objetos que se usan para extender [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] los sistemas de proyectos de, y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Apertura de editores específicos de proyecto](../../extensibility/how-to-open-project-specific-editors.md)  
 Proporciona instrucciones paso a paso para abrir un elemento enlazado de forma intrínseca a un editor específico para un proyecto.  
  
 [Apertura de editores estándar](../../extensibility/how-to-open-standard-editors.md)  
 Proporciona instrucciones paso a paso para abrir un editor estándar.  
  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)  
 Proporciona vínculos a temas conceptuales del subtipo de proyecto. Los subtipos de proyecto extienden los [!INCLUDE[csprcs](../../includes/csprcs-md.md)] proyectos y existentes [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.
