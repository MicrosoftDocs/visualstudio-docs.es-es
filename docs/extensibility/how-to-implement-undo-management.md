---
title: "C&#243;mo: implementar la administraci&#243;n de deshacer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - deshacer administración"
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# C&#243;mo: implementar la administraci&#243;n de deshacer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La interfaz principal utilizada para la administración de deshacer es <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, que el entorno.  Para admitir la administración de deshacer, unidades independientes de deshacer de implementan \(es decir, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, que pueden contener pasos individuales.  
  
 Cómo se implementa la administración de deshacer varía dependiendo de si el editor admite varias vistas o no.  Procedimientos para cada implementación se detallan en las secciones siguientes.  
  
## casos donde un editor admite una vista única  
 En este escenario, el editor no admite varias vistas.  Hay solo un editor y un documento, y admiten deshacer.  Use el procedimiento siguiente para implementar la administración de deshacer.  
  
#### Para admitir la administración de deshacer para un editor en la vista única  
  
1.  Llame a `QueryInterface` en la interfaz de `IServiceProvider` en el marco de la ventana para `IOleUndoManager`, objetos de vista del documento para tener acceso al administrador de deshacer \(`IID_IOLEUndoManager`\).  
  
2.  Cuando una vista se encuentra en un marco de ventana, obtiene un puntero de sitio, que puede utilizar para llamar a `QueryInterface` para `IServiceProvider`.  
  
## Casos donde un editor admite varias vistas  
 Si tiene documento y separación de la vista, hay normalmente un administrador de deshacer asociado al documento propiamente dicho.  Todas las unidades de deshacer se colocan en un administrador de deshacer asociado con el objeto del documento.  
  
 En lugar de la vista de consulta para el administrador de deshacer, cuyo hay uno para cada vista, el objeto del documento llama <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> para crear una instancia del administrador de deshacer, especificando un identificador de clase de CLSID\_OLEUndoManager.  El identificador de clase se define en el archivo de OCUNDOID.h.  
  
 Al utilizar <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> para crear dispone de la instancia del administrador de deshacer, utilice el siguiente procedimiento enlazar el administrador de deshacer en el entorno.  
  
#### Enlazar el administrador de deshacer en el entorno  
  
1.  Llame a `QueryInterface` en el objeto devuelto de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> para `IID_IOleUndoManager`.  almacene el puntero a <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  Llame a `QueryInterface` en `IOleUndoManager` para `IID_IOleCommandTarget`.  almacene el puntero a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Retransmitir el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> y las llamadas de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> en la interfaz almacenada de `IOleCommandTarget` para los siguientes comandos StandardCommandSet97:  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  llamada `QueryInterface` en `IOleUndoManager` para `IID_IVsChangeTrackingUndoManager`.  almacene el puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Utilice el puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> para llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>, y los métodos de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5.  llamada `QueryInterface` en `IOleUndoManager` para `IID_IVsLinkCapableUndoManager`.  
  
6.  Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> con el documento, que también debe implementar la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> .  Cuando se cierra el documento, llame a `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  Cuando se cierra el documento, llame a `QueryInterface` en el administrador de deshacer para `IID_IVsLifetimeControlledObject`.  
  
8.  Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Cuando se realizan cambios en el documento, llame a <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> en el administrador con una clase de `OleUndoUnit` .  El método de <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> mantiene una referencia al objeto, por lo que normalmente se versión él justo después de <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 La clase de `OleUndoManager` representa una instancia única de la pila de deshacer.  Así, hay un objeto de administrador de deshacer por entidad de datos que va seguida para deshacer o rehacer.  
  
> [!NOTE]
>  Mientras que el objeto de administrador de deshacer se usa ampliamente en el editor de texto, es un componente general que no tiene compatibilidad concreto para el editor de texto.  Si desea admitir deshacer o rehacer de varios niveles, puede utilizar este objeto para ello.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Cómo: borrar la pila de deshacer](../extensibility/how-to-clear-the-undo-stack.md)