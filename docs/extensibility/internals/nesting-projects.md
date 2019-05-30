---
title: Anidamiento de proyectos | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 209d3ca013e72ff709d0bd581dd460205d8e347d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326686"
---
# <a name="nesting-projects"></a>Anidamiento de proyectos
Los desarrolladores de aplicaciones empresariales que utilizan el paquete de VS cómodamente pueden agrupar tipos parecidos de proyectos juntos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizando *proyecto anidamiento*. Por ejemplo, el proyecto de plantilla de la empresa usa proyectos anidados para proyectos de grupo de categorías. Proyectos de Business fachada, los proyectos de la interfaz de usuario Web etc. se agrupan en una categoría.

 En este escenario, no hay ningún límite al número de proyectos, que el desarrollador puede anidar en cada proyecto principal, aunque el desarrollador puede proporcionar mediante programación los límites. Este tipo de agrupación también se puede realizar recursiva, en cuyo caso se pueden anidar los proyectos del mismo tipo como un proyecto secundario en el elemento secundario para convertirse en un subproyecto del elemento secundario, que es un subproyecto del elemento primario.

 Anidamiento de proyecto no es una parte intrínseca de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Tendrá que escribir el código para habilitar el anidamiento y subproyecto anidación dentro de los proyectos secundarios. El proyecto principal es un tipo de proyecto, creado y registrado con su propio GUID que incluye el código necesario para implementar el anidamiento de proyecto o VSPackage especial.

 Puede encontrar un ejemplo de proyectos anidados en el proyecto Example.Nested de C# de ejemplo.

## <a name="nested-projects-example"></a>Ejemplo de proyectos anidados
 ![Anidar los proyectos de solución](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") ejemplo de los proyectos anidados

## <a name="see-also"></a>Vea también
- [Cómo: Implementar proyectos anidados](../../extensibility/internals/how-to-implement-nested-projects.md)
- [Consideraciones para descargar y volver a cargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Compatibilidad del Asistente para proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registro de plantillas para proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementación del control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrado del cuadro de diálogo AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Lista de comprobación: Creación de tipos de proyectos](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)
- [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)