---
title: Filtrado del cuadro de diálogo AddItem para proyectos anidados ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708377"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrar el cuadro de diálogo AddItem para proyectos anidados
Cuando se muestra un cuadro de diálogo **AddItem** para un proyecto anidado, el proyecto primario puede controlar qué elementos se muestran en el cuadro de diálogo.

 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaz le permite filtrar los nodos que estarán en un Cuadro de diálogo **AddItem.** Cuando el proyecto secundario muestra el Cuadro de `IVsFilterAddProjectItemDlg` diálogo **AddItem,** el elemento primario puede implementar la interfaz y filtrar los elementos que, de lo contrario, se mostrarían en el proyecto del elemento secundario.

 Cuando los proyectos se agrupan por función `IVsFilterAddProjectItemDlg` en proyectos primarios específicos, puede implementar cuando el usuario selecciona **Agregar elemento** de proyecto en el menú contextual de un proyecto anidado. Implementar `IvsFilterAddProjectItemDlg displays` solo elementos de proyecto o archivos específicos de ese grupo. Los elementos de proyecto para otros grupos se filtran fuera del cuadro de diálogo, incluso si se almacenan en el mismo directorio.

 Cuando un usuario abre el Cuadro de diálogo **AddItem** para `IVsFilterAddProjectItemDlg` el elemento secundario, se llama a la implementación de la interfaz del proyecto primario.

 La `IVsFilterAddProjectItemDlg` interfaz también puede implementar el filtrado por categoría. Para obtener más información, vea [Agregar elementos al cuadro](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) de diálogo Agregar nuevo elemento y Registrar plantillas de [proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrar plantillas de proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)
- [Proyectos Nest](../../extensibility/internals/nesting-projects.md)
