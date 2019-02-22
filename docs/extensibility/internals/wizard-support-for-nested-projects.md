---
title: Asistente para compatibilidad con proyectos anidados | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fd9871e794c2968bab3effce0717ea1cae508eb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603969"
---
# <a name="wizard-support-for-nested-projects"></a>Compatibilidad del asistente con los proyectos anidados
El IDE ejecuta dos asistentes que puede implementar el proyecto principal para proyectos anidados: el **nuevo proyecto** asistente y el **Agregar elemento** asistente.

 Si el usuario inicia la **nuevo proyecto** asistente seleccionando **Agregar proyecto** y haga clic en **nuevo proyecto** en el menú archivo, o bien seleccionando **agregar** y con el botón secundario **nuevo proyecto** en el Explorador de soluciones, el IDE ejecuta el **AddProject** comando y la implementación del proyecto principal de la **AddProject**comando devuelve un archivo de proyecto de plantilla o un archivo de asistentes (.vsz) que tiene un conjunto de parámetros de contexto.

 De forma similar, la implementación de un proyecto elemento primario de **AddItem** asistentes devuelve un archivo .vsz que tiene un conjunto diferente de parámetros de contexto.

 Para obtener más información acerca de los asistentes, vea [asistente (. Archivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parámetros de contexto](../../extensibility/internals/context-parameters.md) y [registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)