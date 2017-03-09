---
title: "Servicios que se usan en los ejemplos | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servicios, que aparecen en los ejemplos"
  - "ejemplos, servicios"
ms.assetid: 04864feb-9b8b-45c4-8233-fc2ed9273987
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Servicios que se usan en los ejemplos
Los ejemplos incluidos en [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] hace uso de muchos servicios.  La lista siguiente muestra varios servicios de uso general y ejemplos que los usan.  
  
> [!NOTE]
>  Si la referencia y ejemplos no compatibles están disponibles, sólo se muestra el ejemplo de referencia.  
  
|Servicio|Ejemplo|  
|--------------|-------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|BscEdit, ProjectSubtype|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|[Cómo: utilizar el registro de actividad](../extensibility/how-to-use-the-activity-log.md)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|BscPrj|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>|Obsoleto.  Utilice <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> en su lugar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|BscEdit, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|ejemplo de Reference.HelpIntegration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|ejemplo de SingleViewEditor.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|ejemplo de SingleViewEditor.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|Reference.Package, Reference.ToolWindow, y muchos otros ejemplos|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|ejemplo de SingleViewEditor.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Reference.Package, Reference.ToolWindow, y muchos otros ejemplos|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|BscEdt, BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|SingleViewEditor, BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Reference.ToolWindow, BscEdit, y muchos otros ejemplos|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|BscEdit, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|Reference.ToolWindow|  
  
## Vea también  
 [Lista de servicios disponibles](../extensibility/internals/list-of-available-services.md)   
 [Fundamentos del servicio](../extensibility/internals/service-essentials.md)