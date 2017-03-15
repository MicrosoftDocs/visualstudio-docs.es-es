---
title: "C&#243;mo: abrir editores para los documentos abiertos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK], abrir para abrir documentos"
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# C&#243;mo: abrir editores para los documentos abiertos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Antes de abrir un proyecto en una ventana de documento, primero el proyecto debe determinar si el archivo está abierto en la ventana de documento para otro editor.  El archivo se abre en un editor específico del proyecto, o uno de los editores estándar registrados con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Abrir un editor de Proyecto\-Specific  
 Utilice el procedimiento siguiente para abrir un editor específico de proyecto para un archivo que ya está abierto.  
  
#### Para abrir un editor específico de proyecto para un archivo abierto  
  
1.  Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.  
  
     Esta llamada devuelve punteros en la jerarquía del documento, elemento de jerarquía, y el marco de la ventana, si es adecuado.  
  
2.  Si el documento abierto, el proyecto debe comprobando si solo existe un objeto del documento, o si un objeto de vista del documento también está presente.  
  
    -   Si existe un objeto de vista del documento, y esta vista es para otra jerarquía o elemento de jerarquía, el proyecto utiliza el puntero al marco de la ventana de la vista para volver a mejorar el la ventana existente.  
  
    -   Si existe un objeto de vista del documento, y esta vista es para la misma jerarquía y elemento de jerarquía, el proyecto puede abrir una segunda vista si puede asociar el objeto de datos subyacente del documento.  Si no, el proyecto debe usar el puntero al marco de la ventana de la vista para volver a mejorar el la ventana existente.  
  
    -   Si solo existe el objeto del documento, el proyecto debe determinar si puede usar el objeto del documento para la vista.  Si el objeto del documento es compatible, complete los pasos descritos en [Abrir un editor de Proyecto\-Specific](../extensibility/how-to-open-project-specific-editors.md).  
  
     Si el objeto del documento no es compatible, un error se debería mostrar al usuario que indica que el archivo está actualmente en uso.  Este error se debe mostrar únicamente en casos transitorios, por ejemplo cuando un archivo se está compilado a la vez el usuario intenta abrir el archivo con un editor distinto del editor de texto de la base de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  El editor de texto básico puede compartir el objeto del documento al compilador.  
  
3.  Si el documento no está abierto porque no hay ningún objeto del objeto de datos o de vista del documento del documento, complete los pasos de [Abrir un editor de Proyecto\-Specific](../extensibility/how-to-open-project-specific-editors.md).  
  
## Abrir un editor estándar  
 Utilice el procedimiento siguiente para abrir un editor estándar para un archivo que ya está abierto.  
  
#### para abrir un editor estándar para un archivo abierto  
  
1.  Llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Este método comprueba primero que el documento aún no esté abierto llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.  Si el documento está abierto, se vuelve a mejorar el de la ventana del editor.  
  
2.  Si el documento no está abierto, después completar los pasos de [Cómo: abrir editores estándares](../extensibility/how-to-open-standard-editors.md).  
  
## Vea también  
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: abrir editores específicos del proyecto](../extensibility/how-to-open-project-specific-editors.md)   
 [Cómo: abrir editores estándares](../extensibility/how-to-open-standard-editors.md)