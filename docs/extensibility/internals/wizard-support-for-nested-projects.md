---
title: Compatibilidad del asistente con proyectos anidados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e498f21499f4b07bf77bb79829fc6d92227f1f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721434"
---
# <a name="wizard-support-for-nested-projects"></a>Compatibilidad del asistente con los proyectos anidados
El IDE ejecuta dos asistentes que puede implementar el proyecto primario para los proyectos anidados: el Asistente para **nuevo proyecto** y el Asistente para **Agregar elementos** .

 Si un usuario inicia el Asistente para **nuevo proyecto** seleccionando **Agregar proyecto** y haciendo clic en **nuevo proyecto** en el menú archivo o seleccionando **Agregar** y haciendo clic con el botón secundario en **nuevo proyecto** en explorador de soluciones, el IDE ejecuta el **AddProject** el comando y la implementación del proyecto primario del comando **AddProject** devuelven un archivo de proyecto de plantilla o un archivo de asistente (. vsz) que tiene un conjunto de parámetros de contexto.

 Del mismo modo, la implementación de un proyecto primario de los asistentes de **AddItem** devuelve un archivo. vsz que tiene un conjunto diferente de parámetros de contexto.

 Para obtener más información acerca de los asistentes, vea [Asistente (. Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parámetros de contexto](../../extensibility/internals/context-parameters.md) y [registro de plantillas de proyecto y de elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)