---
title: Compatibilidad del asistente con proyectos anidados | Microsoft Docs
description: Obtenga información sobre los dos asistentes que puede implementar un proyecto primario para los proyectos anidados en el VSPackage en el SDK de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f52b42462fdc4b7878f97c01bdc65322f32eb5b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074150"
---
# <a name="wizard-support-for-nested-projects"></a>Compatibilidad del asistente con los proyectos anidados
El IDE ejecuta dos asistentes que puede implementar el proyecto primario para los proyectos anidados: el Asistente para **nuevo proyecto** y el Asistente para **Agregar elementos** .

 Si un usuario inicia el Asistente para **nuevo proyecto** seleccionando **Agregar proyecto** y haciendo clic en **nuevo proyecto** en el menú archivo o seleccionando **Agregar** y haciendo clic con el botón derecho en **nuevo proyecto** en explorador de soluciones, el IDE ejecuta el comando **AddProject** y la implementación del proyecto primario del comando **AddProject** devuelve un archivo de proyecto de plantilla o un archivo de asistente (. vsz) que tiene un conjunto de parámetros de contexto

 Del mismo modo, la implementación de un proyecto primario de los asistentes de **AddItem** devuelve un archivo. vsz que tiene un conjunto diferente de parámetros de contexto.

 Para obtener más información acerca de los asistentes, vea [Asistente (. Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parámetros de contexto](../../extensibility/internals/context-parameters.md) y [registro de plantillas de proyecto y de elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)
