---
title: Proyectos de anidamiento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35d0f4f8906acc08733894d1c24b6d8c2199e1f7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="nesting-projects"></a>Proyectos de anidamiento
Los desarrolladores de aplicaciones empresariales que utilizan el paquete de VS cómodamente pueden agrupar tipos parecidos de proyectos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizando *proyecto anidamiento*. Por ejemplo, el proyecto de Enterprise Templates utiliza proyectos anidados para proyectos de grupo de categorías. Proyectos de la fachada de negocios, proyectos de interfaz de usuario Web y así sucesivamente se agrupan en una categoría.  
  
 En este escenario, no hay ningún límite para el número de proyectos que el desarrollador puede anidar en cada proyecto principal, aunque el desarrollador puede proporcionar mediante programación los límites. Este tipo de agrupación pueden hacer recursiva, en cuyo caso los proyectos del mismo tipo como un proyecto secundario pueden estar anidados en el elemento secundario se convierta en un subproyecto del elemento secundario, que es un subproyecto del elemento primario.  
  
 Anidamiento de proyecto no es una parte intrínseca de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Tendrá que escribir el código para habilitar el anidamiento y subproyecto anidamiento dentro de los proyectos secundarios. El proyecto principal es un tipo de proyecto, creado y registrado con su propio GUID que incluye el código que se necesita para implementar el anidamiento de proyecto o VSPackage especial.  
  
 Puede encontrar un ejemplo de proyectos anidados en el proyecto Example.Nested de C# de ejemplo.  
  
## <a name="nested-projects-example"></a>Ejemplo de proyectos anidados  
 ![Anidar proyectos solución](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Ejemplo de proyectos anidados  
  
## <a name="see-also"></a>Vea también  
 [Cómo: implementar proyectos anidados](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Consideraciones para descargar y volver a cargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Asistente para compatibilidad con proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementar el control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtrar el cuadro de diálogo de AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)