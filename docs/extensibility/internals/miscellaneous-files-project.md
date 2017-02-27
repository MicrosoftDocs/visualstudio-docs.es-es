---
title: "Proyecto de archivos varios | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "archivos, agregar archivos existentes a soluciones"
  - "Proyecto de archivos varios"
  - "Carpeta de elementos de la solución"
  - "archivos, abrir con el proyecto de archivos varios"
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Proyecto de archivos varios
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando un usuario abre los elementos de proyecto, el IDE asigna al proyecto de archivos varios cualquier elemento que no son miembros de los proyectos de una solución.  
  
 Los proyectos representan un rol importante en determinar se utiliza el editor cuando un usuario abre un elemento de proyecto.  Un proyecto se puede diseñar para abrir algunos archivos mediante un editor específico del proyecto o un editor estándar.  
  
 Un editor específico del proyecto exige que el usuario tenga conocimiento especial o utilice interfaces especiales del proyecto.  Para obtener más información, vea [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Un editor estándar puede abrir cualquier archivo de una extensión concreta en cualquier proyecto.  El usuario puede personalizar algunos editores estándar, como el editor de texto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , porque proyectos pero conservar el carácter público.  Los editores estándar se crean utilizando el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
 Si responde ningún proyecto de la solución que puede abrir un elemento de proyecto, el IDE proporciona un proyecto especial denominado el proyecto de archivos varios que abrir cualquier archivo.  
  
 Este proyecto especial para abrir de un archivo fuera del contexto de un proyecto.  Durante el procesamiento del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> , el proyecto de archivos varios responde siempre con una prioridad muy baja.  Por consiguiente, el proyecto de archivos varios siempre a cualquier proyecto de prioridad más alta que puede abrir los archivos.  
  
 El proyecto de archivos varios no requiere que el usuario explícitamente hacerlo con el cuadro de diálogo de **Nuevo proyecto** .  Además, el proyecto de archivos varios no administra permanentemente una lista de miembros del proyecto.  Utiliza una característica opcional para grabar una lista de archivos usados recientemente para cada usuario.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Cómo: abrir editores estándares](../../extensibility/how-to-open-standard-editors.md)   
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)