---
title: "C&#243;mo: abrir editores est&#225;ndares | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK], abrir"
  - "proyectos [Visual Studio SDK], abrir editores estándares"
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: abrir editores est&#225;ndares
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al abrir un editor estándar, deja el IDE determinar un editor estándar para un tipo de archivo designado, en lugar de especificar un editor específico de proyecto para el archivo.  
  
 Complete el procedimiento siguiente para implementar el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> .  esto abrirá un archivo de proyecto en un editor estándar.  
  
### para implementar el método de OpenItem con un editor estándar  
  
1.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> \(`RDT_EditLock`\) para determinar si el archivo del objeto del documento está abierto.  
  
2.  Si el archivo está abierto, vuelva a mejorar el archivo llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> , especificando un valor de `IDO_ActivateIfOpen` para el parámetro de `grfIDO` .  
  
     Si el archivo está abierto y el documento es propiedad de un proyecto diferente que el proyecto de la llamada, el proyecto recibe una advertencia que el editor abierta es de otro proyecto.  La ventana del archivo se emerge.  
  
3.  Si el documento no está abierto o no en la tabla en el documento, llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> \(`OSE_ChooseBestStdEditor`\) para abrir un editor estándar para el archivo.  
  
     Cuando se llama al método, el IDE realiza las tareas siguientes:  
  
    1.  El IDE examina la subclave de Editors\/{guidEditorType} \/Extensions del registro para determinar qué editor puede abrir el archivo y tiene la máxima prioridad para ello.  
  
    2.  Después de que el IDE determinar qué editor puede abrir el archivo, el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  La implementación del editor de este método devuelve la información necesaria para que el IDE llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> y el sitio el documento que se acaba de abrir.  
  
    3.  Finalmente, el IDE carga el documento mediante la interfaz habitual de persistencia, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Si el IDE ha determinado previamente que la jerarquía o el elemento de la jerarquía está disponible, el IDE llama a método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> en el proyecto de obtener un puntero de <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> de contexto de nivel de proyecto para pasar la reproducción en con la llamada al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> .  
  
4.  Devuelve un puntero de <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> al IDE cuando el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> en el proyecto si desea que el editor obtener contexto del proyecto.  
  
     Seguir este paso permite a los servicios adicionales de la propuesta de proyecto en el editor.  
  
     Si la vista del documento o el objeto de vista del documento se ha ubicado correctamente en un marco de ventana, el objeto se inicializó con sus datos llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: abrir editores específicos del proyecto](../extensibility/how-to-open-project-specific-editors.md)   
 [Cómo: abrir editores para los documentos abiertos](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Mostrar archivos mediante el comando Abrir archivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)