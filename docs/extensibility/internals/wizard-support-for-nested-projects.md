---
title: Soporte de asistente sin asistentes para proyectos anidados ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703191"
---
# <a name="wizard-support-for-nested-projects"></a>Compatibilidad del asistente con los proyectos anidados
El IDE ejecuta dos asistentes que el proyecto primario para proyectos anidados puede implementar: el Asistente para **nuevo proyecto** y el Asistente para **agregar elementos.**

 Si un usuario inicia el Asistente para **nuevo proyecto** seleccionando **Agregar proyecto** y haciendo clic en Nuevo **proyecto** en el menú Archivo o seleccionando **Agregar** y haciendo clic con el botón secundario en **Nuevo proyecto** en el Explorador de soluciones, el IDE ejecuta el comando **AddProject** y la implementación del proyecto primario del comando **AddProject** devuelve un archivo de proyecto de plantilla o un archivo de asistente (.vsz) que tiene un conjunto de parámetros de contexto.

 De forma similar, la implementación de un proyecto primario de **asistentes AddItem** devuelve un archivo .vsz que tiene un conjunto diferente de parámetros de contexto.

 Para obtener más información acerca de los asistentes, consulte [Asistente (. Vsz) Archivo](../../extensibility/internals/wizard-dot-vsz-file.md), [Parámetros de contexto](../../extensibility/internals/context-parameters.md) y Registro de plantillas de proyecto y [elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)
