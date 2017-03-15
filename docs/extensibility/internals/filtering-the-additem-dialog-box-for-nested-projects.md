---
title: "Filtrar el cuadro de di&#225;logo AddItem para proyectos anidados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtrado de proyectos anidados"
  - "proyectos anidados, AddItem diálogo cuadro filtrado"
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Filtrar el cuadro de di&#225;logo AddItem para proyectos anidados
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando se muestra un cuadro de diálogo de **AddItem** para un proyecto anidado, el proyecto principal puede controlar qué elementos se muestran en el cuadro de diálogo.  
  
 La interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> permite filtrar los nodos que estarán en un cuadro de diálogo de **AddItem** .  Cuando el proyecto secundario muestra el cuadro de diálogo de **AddItem** , el elemento primario puede implementar la interfaz de `IVsFilterAddProjectItemDlg` y filtrar los elementos que se mostrarán de otra manera en el proyecto del elemento secundario.  
  
 Cuando los proyectos se agrupan por la función en proyectos primarios concretos, puede implementar `IVsFilterAddProjectItemDlg` cuando el usuario selecciona **agregue el elemento de proyecto** en el menú contextual de un proyecto anidados.  Implementar elementos de proyecto o archivos de `IvsFilterAddProjectItemDlg displays` sólo específicos de ese grupo.  Los elementos de proyecto para otros grupos se filtran del cuadro de diálogo, aunque se almacenan en el mismo directorio.  
  
 Cuando un usuario abre el cuadro de diálogo de **AddItem** para el elemento secundario, la aplicación de proyecto principal de la interfaz de `IVsFilterAddProjectItemDlg` se denomina.  
  
 La interfaz de `IVsFilterAddProjectItemDlg` puede implementar filtrar por categoría.  Para obtener más información, vea [Agregar elementos a la para agregar elementos nuevos cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) y [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Agregar elementos a la para agregar elementos nuevos cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Proyectos de anidamiento](../../extensibility/internals/nesting-projects.md)