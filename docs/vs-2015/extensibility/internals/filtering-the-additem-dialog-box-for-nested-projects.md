---
title: Filtrado del cuadro de diálogo AddItem para proyectos anidados | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 363ba8e38ae2de445bd18bb9378d48aa4d824298
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769769"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrado del cuadro de diálogo AddItem para proyectos anidados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al mostrar una **AddItem** cuadro de diálogo para un proyecto anidado, el proyecto principal puede controlar qué elementos se muestran en el cuadro de diálogo.  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaz le permite filtrar los nodos que se incluirán en un **AddItem** cuadro de diálogo. Cuando se muestre el proyecto secundario la **AddItem** cuadro de diálogo, puede implementar el elemento primario del `IVsFilterAddProjectItemDlg` interfaz y filtrado de los elementos que se mostrará en el proyecto del elemento secundario.  
  
 Cuando los proyectos se agrupan por función en los proyectos principales específicos, puede implementar `IVsFilterAddProjectItemDlg` cuando el usuario selecciona **Agregar elemento de proyecto** en el menú contextual de un proyecto anidado. Implementar `IvsFilterAddProjectItemDlg displays` sólo el proyecto de elementos o archivos específico de ese grupo. Elementos de proyecto para otros grupos se filtran el cuadro de diálogo, incluso si están almacenados en el mismo directorio.  
  
 Cuando un usuario abre el **AddItem** cuadro de diálogo para el elemento secundario, implementación del proyecto principal de la `IVsFilterAddProjectItemDlg` interfaz se denomina.  
  
 El `IVsFilterAddProjectItemDlg` interfaz también puede implementar el filtrado por categoría. Para obtener más información, consulte [agregar elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) y [registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Agregar elementos a la Agregar nuevo elemento de los cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registro de plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)

