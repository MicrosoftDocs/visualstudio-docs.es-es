---
title: Filtrar el cuadro de diálogo AddItem para proyectos anidados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538101"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrado del cuadro de diálogo AddItem para proyectos anidados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando se muestra un cuadro de diálogo **AddItem** para un proyecto anidado, el proyecto primario puede controlar qué elementos se muestran en el cuadro de diálogo.  
  
 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaz le permite filtrar los nodos que estarán en un cuadro de diálogo **AddItem** . Cuando el proyecto secundario muestra el cuadro de diálogo **AddItem** , el elemento primario puede implementar la `IVsFilterAddProjectItemDlg` interfaz y filtrar los elementos que de otro modo se mostrarían en el proyecto del elemento secundario.  
  
 Cuando los proyectos se agrupan por función en proyectos primarios específicos, puede implementar `IVsFilterAddProjectItemDlg` cuando el usuario selecciona **Agregar elemento de proyecto** en el menú contextual de un proyecto anidado. Implementar `IvsFilterAddProjectItemDlg displays` solo los elementos de proyecto o los archivos específicos de ese grupo. Los elementos de proyecto de otros grupos se filtran del cuadro de diálogo, incluso si están almacenados en el mismo directorio.  
  
 Cuando un usuario abre el cuadro de diálogo **AddItem** para el elemento secundario, se llama a la implementación del proyecto primario de la `IVsFilterAddProjectItemDlg` interfaz.  
  
 La `IVsFilterAddProjectItemDlg` interfaz también puede implementar el filtrado por categoría. Para obtener más información, vea [Agregar elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) y [registrar plantillas de proyecto y de elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Agregar elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrar plantillas de proyecto y de elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)
