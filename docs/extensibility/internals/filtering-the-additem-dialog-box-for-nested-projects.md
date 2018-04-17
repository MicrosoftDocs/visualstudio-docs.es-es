---
title: Filtrar el cuadro de diálogo de AddItem para proyectos anidados | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50a9491dad92e4f1dd090a6de1ebf48ef1b88085
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrar el cuadro de diálogo de AddItem para proyectos anidados
Al mostrar una **AddItem** cuadro de diálogo para un proyecto anidado, el proyecto principal puede controlar qué elementos se muestran en el cuadro de diálogo.  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaz le permite filtrar los nodos que se incluirán en un **AddItem** cuadro de diálogo. Cuando se muestre el proyecto secundario la **AddItem** cuadro de diálogo, puede implementar el elemento primario del `IVsFilterAddProjectItemDlg` elementos de interfaz y filtrar en caso contrario, aparecerá en el proyecto del elemento secundario.  
  
 Cuando se agrupan los proyectos de función en proyectos de nodo principal específico, puede implementar `IVsFilterAddProjectItemDlg` cuando el usuario selecciona **Agregar elemento de proyecto** en el menú contextual de un proyecto anidado. Implementar `IvsFilterAddProjectItemDlg displays` proyecto solo elementos o archivos específico de ese grupo. Elementos de proyecto para otros grupos se filtran el cuadro de diálogo, incluso si están almacenados en el mismo directorio.  
  
 Cuando un usuario abre la **AddItem** cuadro de diálogo para el elemento secundario, implementación del proyecto principal de la `IVsFilterAddProjectItemDlg` interfaz se denomina.  
  
 El `IVsFilterAddProjectItemDlg` interfaz también puede implementar el filtrado por categoría. Para obtener más información, consulte [agregar elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) y [registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Agregar elementos a la para agregar elementos nuevos cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)