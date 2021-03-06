---
title: Filtrar el cuadro de diálogo AddItem para proyectos anidados | Microsoft Docs
description: Obtenga información sobre cómo filtrar el cuadro de diálogo AddItem para un proyecto anidado en Visual Studio implementando la interfaz IVsFilterAddProjectItemDlg del proyecto primario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 59ae3c229ba359af0349ad93edc75e53c2cc3557
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069587"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrar el cuadro de diálogo AddItem para proyectos anidados
Cuando se muestra un cuadro de diálogo **AddItem** para un proyecto anidado, el proyecto primario puede controlar qué elementos se muestran en el cuadro de diálogo.

 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaz le permite filtrar los nodos que estarán en un cuadro de diálogo **AddItem** . Cuando el proyecto secundario muestra el cuadro de diálogo **AddItem** , el elemento primario puede implementar la `IVsFilterAddProjectItemDlg` interfaz y filtrar los elementos que de otro modo se mostrarían en el proyecto del elemento secundario.

 Cuando los proyectos se agrupan por función en proyectos primarios específicos, puede implementar `IVsFilterAddProjectItemDlg` cuando el usuario selecciona **Agregar elemento de proyecto** en el menú contextual de un proyecto anidado. Implementar `IvsFilterAddProjectItemDlg displays` solo los elementos de proyecto o los archivos específicos de ese grupo. Los elementos de proyecto de otros grupos se filtran del cuadro de diálogo, incluso si están almacenados en el mismo directorio.

 Cuando un usuario abre el cuadro de diálogo **AddItem** para el elemento secundario, se llama a la implementación del proyecto primario de la `IVsFilterAddProjectItemDlg` interfaz.

 La `IVsFilterAddProjectItemDlg` interfaz también puede implementar el filtrado por categoría. Para obtener más información, vea [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) y [registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Anidar proyectos](../../extensibility/internals/nesting-projects.md)
