---
title: Agregando el proyecto y plantillas de elemento de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 94d521d288b470db56736668f11d47dab71d2533
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128753"
---
# <a name="adding-project-and-project-item-templates"></a>Agregar proyecto y plantillas de elemento de proyecto
Cuando cree sus propios tipos de proyecto, debe proporcionar soporte técnico para agregar nuevos proyectos y elementos de proyecto mediante el estándar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrado cuadros de diálogo de desarrollo (IDE) de entorno. Los temas siguientes describen técnicas diferentes para agregar proyectos y elementos de proyecto.  
  
## <a name="in-this-section"></a>En esta sección  
 [Contexto del proyecto](../../extensibility/internals/project-context.md)  
 Explica que el proyecto proporciona la mayor parte de la información de contexto para lo que ocurre en el entorno.  
  
 [Prioridad del proyecto](../../extensibility/internals/project-priority.md)  
 Explica que un elemento de proyecto suele ser un miembro de un proyecto para ayudar a evitar la ambigüedad sobre qué proyecto se utiliza para abrir el elemento.  
  
 [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)  
 Proporciona información acerca de los dos tipos de editores que pueden utilizarse para abrir archivos en un proyecto y el rol desempeña el proyecto para determinar el editor que desea usar cuando se abre un elemento de proyecto.  
  
 [Registro de plantillas para proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explica lo que ocurre cuando un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se crea el proyecto.  
  
 [Adición de elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explica el proceso para agregar elementos a la **Agregar nuevo elemento** cuadro de diálogo.  
  
 [Adición de directorios al cuadro de diálogo Nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Proporciona un ejemplo de cómo registrar un nuevo directorio que contiene plantillas personalizadas facilitadas por un paquete VSPackage.  
  
 [Adición directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Proporciona un ejemplo de cómo registrar un nuevo conjunto de directorios para la **Agregar nuevo elemento** cuadro de diálogo.  
  
 [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Enumera los tipos diferentes de elementos de comando que se utiliza para extender los sistemas del proyecto.  
  
 [CATID para los objetos que se utilizan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Enumera CATID para los objetos que se utilizan para extender [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sistemas del proyecto.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Apertura de editores específicos de proyecto](../../extensibility/how-to-open-project-specific-editors.md)  
 Proporciona instrucciones paso a paso para abrir un elemento intrínsecamente enlazado a un editor específico para un proyecto.  
  
 [Apertura de editores estándar](../../extensibility/how-to-open-standard-editors.md)  
 Proporciona instrucciones paso a paso para abrir un editor estándar.  
  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)  
 Proporciona vínculos a temas conceptuales de subtipo del proyecto. Subtipos de proyecto extienden existente [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proyectos.  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.