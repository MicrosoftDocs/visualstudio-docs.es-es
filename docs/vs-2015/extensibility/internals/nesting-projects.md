---
title: Anidar proyectos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e3a0fae42dc7bf1497e3d0d4a9d23f9cab50675
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180419"
---
# <a name="nesting-projects"></a>Anidamiento de proyectos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los desarrolladores de aplicaciones empresariales que usan el paquete de VS pueden agrupar de manera cómoda tipos de proyectos similares en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mediante el *anidamiento de proyectos*. Por ejemplo, el proyecto de plantilla de empresa utiliza proyectos anidados para agrupar proyectos en categorías. Los proyectos de fachada empresarial, los proyectos de interfaz de usuario Web, etc. se agrupan en una categoría.  
  
 En este escenario, no hay ningún límite en el número de proyectos que el desarrollador puede anidar en cada proyecto primario, aunque el desarrollador puede proporcionar límites mediante programación. Este tipo de agrupación también se puede convertir en recursivo, en cuyo caso los proyectos del mismo tipo que un proyecto secundario se pueden anidar bajo el secundario para convertirse en un subproyecto del elemento secundario, que es un subproyecto del elemento primario.  
  
 El anidamiento del proyecto no es una parte intrínseca de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Tiene que escribir el código para habilitar el anidamiento y el anidamiento de subproyectos en los proyectos secundarios. El proyecto primario es un VSPackage especial, o un tipo de proyecto, creado y registrado con su propio GUID que incluye el código necesario para implementar el anidamiento del proyecto.  
  
 Puede encontrar un ejemplo de proyectos anidados en el ejemplo de C#. ejemplo de proyecto anidado.  
  
## <a name="nested-projects-example"></a>Ejemplo de proyectos anidados  
 ![Solución de proyectos anidados](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Ejemplo de proyectos anidados  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: implementar proyectos anidados](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Consideraciones para descargar y volver a cargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Compatibilidad del asistente con proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registrar plantillas de proyecto y de elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementar el control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtrar el cuadro de diálogo AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Lista de comprobación: crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Archivo de asistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
