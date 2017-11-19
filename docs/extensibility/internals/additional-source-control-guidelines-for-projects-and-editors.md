---
title: Instrucciones de Control de origen adicionales para proyectos y editores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ed84b4b1bf6c974f22682dcb8d899208c653ebc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Instrucciones de Control de origen adicionales para proyectos y editores
Hay una serie de instrucciones que editores y proyectos deben respetar para admitir el control de código fuente.  
  
## <a name="guidelines"></a>Instrucciones  
 El proyecto o el editor también debería hacer lo siguiente para admitir el control de código fuente:  
  
|Área|Proyecto|Editor|Detalles|  
|----------|-------------|------------|-------------|  
|Privada copias de archivos|X||El entorno admite privadas copias de archivos. Es decir, cada persona dada de alta en el proyecto tiene su propia copia privada de los archivos en el proyecto.|  
|Persistencia de ANSI o Unicode|X|X|Si escribe el código de persistencia, se conservan los archivos en la forma ANSI porque la mayoría de los programas de control de origen no admiten actualmente Unicode.|  
|Enumerar archivos|X||El proyecto debe contener una lista específica de todos los archivos contenidos en él y debe ser capaz de enumerar la lista de archivos mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). El proyecto debería exponer los nombres de elemento a través de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implementación y compatibilidad con búsqueda de nombres (incluidos los archivos especiales) a través de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementación.|  
|Formato de texto|X|X|Cuando sea posible, los archivos deben estar en formato de texto para admitir la combinación de las distintas versiones. Archivos que no están en formato de texto no se puede combinar con otras versiones del archivo más adelante. El formato de texto preferido es XML.|  
|Basada en referencias|X||Proyectos basados en la referencia se admiten con facilidad en control de código fuente. Sin embargo, también se admiten proyectos basados en el directorio por control de código fuente mientras el proyecto puede generar una lista de los archivos a petición, independientemente de si dichos archivos existen en el disco. Al abrir un proyecto de control de código fuente, el archivo de proyecto está inactivo primero antes de cualquiera de sus archivos.|  
|Conservar objetos y propiedades en orden predecible|X|X|Conservar los archivos en un orden predecible, como el orden alfabético, para facilitar la combinación.|  
|Volver a cargar|X|X|Cuando cambia un archivo en disco, el editor debe poder cargarlo de nuevo. Al participar en el control de código fuente, el entorno se volverá a cargar datos automáticamente mediante una llamada a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementación. El caso de volver a cargar más difícil es cuando se produce una desprotección cuando se llamó a IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y se procese la información. Sin embargo, el código de recarga debe ser capaz de ejecutar en esta situación.<br /><br /> El entorno vuelve a cargar automáticamente archivos de proyecto. Sin embargo, debe implementar un proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> si ha anidado jerarquías para admitir la recarga anida los archivos de proyecto.|  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)