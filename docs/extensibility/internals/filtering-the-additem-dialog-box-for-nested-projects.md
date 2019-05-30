---
title: Filtrado del cuadro de diálogo AddItem para proyectos anidados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc3ff1f85e8c8c71bf8ef16e6fe0c89bf3613f4d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328949"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrar el cuadro de diálogo AddItem para proyectos anidados
Al mostrar una **AddItem** cuadro de diálogo para un proyecto anidado, el proyecto principal puede controlar qué elementos se muestran en el cuadro de diálogo.

 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaz le permite filtrar los nodos que se incluirán en un **AddItem** cuadro de diálogo. Cuando se muestre el proyecto secundario la **AddItem** cuadro de diálogo, puede implementar el elemento primario del `IVsFilterAddProjectItemDlg` interfaz y filtrado de los elementos que se mostrará en el proyecto del elemento secundario.

 Cuando los proyectos se agrupan por función en los proyectos principales específicos, puede implementar `IVsFilterAddProjectItemDlg` cuando el usuario selecciona **Agregar elemento de proyecto** en el menú contextual de un proyecto anidado. Implementar `IvsFilterAddProjectItemDlg displays` sólo el proyecto de elementos o archivos específico de ese grupo. Elementos de proyecto para otros grupos se filtran el cuadro de diálogo, incluso si están almacenados en el mismo directorio.

 Cuando un usuario abre el **AddItem** cuadro de diálogo para el elemento secundario, implementación del proyecto principal de la `IVsFilterAddProjectItemDlg` interfaz se denomina.

 El `IVsFilterAddProjectItemDlg` interfaz también puede implementar el filtrado por categoría. Para obtener más información, consulte [agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) y [registrar las plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrar las plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Proyectos de anidamiento](../../extensibility/internals/nesting-projects.md)