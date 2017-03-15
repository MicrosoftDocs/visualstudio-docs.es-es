---
title: "Instrucciones de Control de origen adicionales para los proyectos y editores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente [Visual Studio SDK], directrices para proyectos y editores"
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Instrucciones de Control de origen adicionales para los proyectos y editores
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Hay varias instrucciones a las que los proyectos y editores deben cumplir para admitir el control de código fuente.  
  
## Instrucciones  
 El proyecto o el editor debe hacer lo siguiente para admitir el control de código fuente:  
  
|Área|Proyecto|Editor|Detalles|  
|----------|--------------|------------|--------------|  
|copias privadas de archivos|X||El entorno admite copias privadas de archivos.  Es decir, cada persona dada de alta en el proyecto tiene su propia copia privada de los archivos de ese proyecto.|  
|Persistencia ANSI Y Unicode|X|X|Si escribe código de persistencia, conserve los archivos en la forma ANSI porque la mayoría de los programas de control de origen no admiten Unicode.|  
|Muestra los archivos|X||El proyecto debe contener una lista específica de todos los archivos en el y debe poder enumerar la lista de archivos utilizando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> \(VSH\_PROPID\_First\_Child\/Next\_Sibling\).  El proyecto debe exponer nombres de elemento con su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> y búsqueda admiten el nombre \(archivos especiales incluida con su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> .|  
|formato de texto|X|X|Cuando sea posible, los archivos deben estar en formato de texto para admitir la combinación de distintas versiones.  Los archivos que no están en formato de texto no se pueden combinar con otras versiones de archivo después.  el formato de texto preferido es XML.|  
|Referencia\-basado|X||los proyectos en referencias se admiten fácilmente en el control de código fuente.  Sin embargo, los proyectos basados en directorios también son compatibles con el control de código fuente mientras el proyecto puede mostrar una lista de los archivos a petición, sin importar si esos archivos existen en el disco.  Al abrir un proyecto de control de código fuente, el archivo de proyecto se liberan antes de ninguno de los archivos.|  
|Conserve los objetos y propiedades en orden confiable|X|X|Se conservan los archivos en un orden confiable, como orden alfabético, para facilitar el la combinación.|  
|recarga|X|X|Cuando cambia un archivo en disco, el editor deben poder recargarlo.  Cuando se participa en control de código fuente, el entorno se recargará los datos automáticamente llamando a la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> .  El caso más difícil reload es cuando una comprobación se produce cuando se ha llamado a IVsQueryEditQuerySave:: el<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y está procesando la información.  sin embargo, el código de la recarga debe poder ejecutarse en esta situación.<br /><br /> El entorno los archivos de proyecto de las recargas automáticamente.  Sin embargo, un proyecto debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> si ha anidado jerarquías para admitir cargar los archivos de proyecto anidados.|  
  
## Vea también  
 [Compatibilidad con Control de código fuente](../../extensibility/internals/supporting-source-control.md)