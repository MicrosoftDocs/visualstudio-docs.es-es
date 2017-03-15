---
title: "Implementaci&#243;n de control de comandos para proyectos anidados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos anidados, implementar el control de comandos"
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Implementaci&#243;n de control de comandos para proyectos anidados
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El IDE puede pasar los comandos que se pasan a través de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> e interfaces de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> a proyectos anidados, o proyectos primarios pueden filtrar o reemplazar los comandos.  
  
> [!NOTE]
>  Únicamente los comandos controla normalmente por el proyecto principal se pueden filtrar.  Los comandos como **Build** y **Deploy** controlados por el IDE no se pueden filtrar.  
  
 Los pasos siguientes describen el proceso para implementar la administración de comando.  
  
## Procedimientos  
  
#### Para implementar la administración de comando  
  
1.  Cuando el usuario selecciona un proyecto anidados o un nodo de un proyecto anidada:  
  
    1.  El IDE llama al método de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> .  
  
     \-O bien\-  
  
    1.  Si el comando se originó en una ventana jerarquía, como un comando de menú contextual en el explorador de soluciones, el IDE llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> en el elemento primario del proyecto.  
  
2.  El proyecto principal puede examinar los parámetros que se pasarán a `QueryStatus`, como `pguidCmdGroup` y `prgCmds`, para determinar si el proyecto principal debe filtrar los comandos.  Si el proyecto principal se implementa los comandos de filtro, debe establecer:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     El proyecto principal debe devolver `S_OK`.  
  
     Si el proyecto principal no filtra el comando, debe simplemente devolver `S_OK`.  En este caso, el IDE automáticamente distribuye el comando al proyecto secundario.  
  
     El proyecto principal no tiene que distribuir el comando al proyecto secundario.  El IDE realiza esta tarea.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Barras de herramientas, menús y comandos](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Proyectos de anidamiento](../../extensibility/internals/nesting-projects.md)