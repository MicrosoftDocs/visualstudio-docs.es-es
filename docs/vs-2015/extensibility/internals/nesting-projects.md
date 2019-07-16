---
title: Anidamiento de proyectos | Documentos de Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180419"
---
# <a name="nesting-projects"></a>Anidamiento de proyectos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los desarrolladores de aplicaciones empresariales que utilizan el paquete de VS cómodamente pueden agrupar tipos parecidos de proyectos juntos en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilizando *proyecto anidamiento*. Por ejemplo, el proyecto de plantilla de la empresa usa proyectos anidados para proyectos de grupo de categorías. Proyectos de Business fachada, los proyectos de la interfaz de usuario Web etc. se agrupan en una categoría.  
  
 En este escenario, no hay ningún límite al número de proyectos, que el desarrollador puede anidar en cada proyecto principal, aunque el desarrollador puede proporcionar mediante programación los límites. Este tipo de agrupación también se puede realizar recursiva, en cuyo caso se pueden anidar los proyectos del mismo tipo como un proyecto secundario en el elemento secundario para convertirse en un subproyecto del elemento secundario, que es un subproyecto del elemento primario.  
  
 Anidamiento de proyecto no es una parte intrínseca de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Tendrá que escribir el código para habilitar el anidamiento y subproyecto anidación dentro de los proyectos secundarios. El proyecto principal es un tipo de proyecto, creado y registrado con su propio GUID que incluye el código necesario para implementar el anidamiento de proyecto o VSPackage especial.  
  
 Puede encontrar un ejemplo de proyectos anidados en el proyecto Example.Nested de C# de ejemplo.  
  
## <a name="nested-projects-example"></a>Ejemplo de proyectos anidados  
 ![Anidar los proyectos de solución](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Ejemplo de proyectos anidados  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Implementación de proyectos anidados](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Consideraciones para descargar y volver a cargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Asistente para compatibilidad con proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registro de plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementación de control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtrado del cuadro de diálogo AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
