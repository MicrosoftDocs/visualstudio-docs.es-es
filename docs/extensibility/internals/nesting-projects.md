---
title: "Proyectos de anidamiento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "anidamiento de proyecto"
  - "proyectos anidados"
  - "proyectos [Visual Studio SDK] proyectos secundarios"
  - "proyectos [Visual Studio SDK] de anidamiento"
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Proyectos de anidamiento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los desarrolladores de aplicaciones empresariales que utilizan el paquete de VS cómodamente pueden agrupar tipos parecidos de proyectos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizando *proyecto anidamiento*. Por ejemplo, el proyecto de Enterprise Templates utiliza proyectos anidados para agrupar proyectos en categorías. Proyectos de la fachada de negocios, proyectos de interfaz de usuario Web etc. se agrupan en una categoría.  
  
 En este escenario, no hay ningún límite en el número de proyectos que el desarrollador puede anidar en cada proyecto principal, aunque el desarrollador puede proporcionar mediante programación los límites. Este tipo de agrupación también es posible hacer recursiva, en cuyo caso los proyectos del mismo tipo como un proyecto secundario pueden estar anidados en el elemento secundario se convierta en un subproyecto del elemento secundario, que es un subproyecto del elemento primario.  
  
 Anidamiento de proyecto no es parte intrínseca de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Tendrá que escribir el código para habilitar el anidamiento y subproyecto anidamiento dentro de los proyectos secundarios. El proyecto principal es un tipo de proyecto, creado y registrado con su propio GUID que incluye el código necesario para implementar el anidamiento de proyecto o VSPackage especial.  
  
 Puede encontrar un ejemplo de proyectos anidados en el proyecto Example.Nested de C\# de ejemplo.  
  
## Ejemplo de proyectos anidados  
 ![Solución de proyectos anidados](~/docs/extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Ejemplo de proyectos anidados  
  
## Vea también  
 [Cómo: implementar proyectos anidados](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Consideraciones para descargar y volver a cargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Admite el Asistente para proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementación de control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtrar el cuadro de diálogo AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Asistente \(. Archivo vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)