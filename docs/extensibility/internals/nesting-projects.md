---
title: Proyectos de Anidación (Nesting Projects) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707033"
---
# <a name="nesting-projects"></a>Anidamiento de proyectos
Los desarrolladores de aplicaciones empresariales que usan el paquete [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE VS pueden agrupar convenientemente tipos similares de proyectos mediante el anidamiento de *proyectos.* Por ejemplo, el proyecto Plantilla de empresa utiliza proyectos anidados para agrupar proyectos en categorías. Los proyectos de fachada empresarial, los proyectos de interfaz de usuario web, etc., se agrupan en una categoría.

 En este escenario, no hay límite en el número de proyectos que el desarrollador puede anidar en cada proyecto primario, aunque el desarrollador puede proporcionar límites mediante programación. Este tipo de agrupación también se puede hacer recursivo, en cuyo caso los proyectos del mismo tipo que un proyecto secundario se pueden anidar bajo el elemento secundario para convertirse en un subproyecto del elemento secundario, que es un subproyecto del elemento primario.

 El anidamiento de proyectos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]no es una parte intrínseca de . Debe escribir el código para habilitar el anidamiento y el anidamiento de subproyectos dentro de proyectos secundarios. El proyecto primario es un VSPackage especial, o tipo de proyecto, creado y registrado con su propio GUID que incluye el código necesario para implementar el anidamiento del proyecto.

 Puede encontrar un ejemplo sobre cómo anidar proyectos en [Cómo: Implementar proyectos anidados](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Ejemplo de proyectos anidados
 ![Solución de proyectos anidados](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") Ejemplo de proyectos anidados

## <a name="see-also"></a>Vea también
- [Consideraciones para descargar y volver a cargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Compatibilidad del asistente con los proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registro de plantillas para proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementación del control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrado del cuadro de diálogo AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)
- [Archivo de asistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
