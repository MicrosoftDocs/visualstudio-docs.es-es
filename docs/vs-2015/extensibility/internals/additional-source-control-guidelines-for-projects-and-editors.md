---
title: Las instrucciones de Control de origen adicionales para los proyectos y editores | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b671397e5be6701176fc0fd5aaa3ae2be24e609
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577774"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Instrucciones de control de código fuente adicionales para proyectos y editores
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [las instrucciones de Control de origen adicionales para los proyectos y editores](https://docs.microsoft.com/visualstudio/extensibility/internals/additional-source-control-guidelines-for-projects-and-editors).  
  
Hay una serie de instrucciones de proyectos y editores deben cumplir con el fin de admitir el control de código fuente.  
  
## <a name="guidelines"></a>Instrucciones  
 Su editor o proyecto también debe hacer lo siguiente para admitir el control de código fuente:  
  
|Área|Proyecto|Editor|Detalles|  
|----------|-------------|------------|-------------|  
|Copias privadas de archivos|X||El entorno admite copias privadas de los archivos. Es decir, cada persona dada de alta en el proyecto tiene su propia copia privada de los archivos en el proyecto.|  
|Persistencia de ANSI o Unicode|X|X|Si escribe el código de persistencia, persistencia de archivos en la forma ANSI porque la mayoría de los programas de control de código fuente es actualmente compatibles con Unicode.|  
|Enumerar archivos|X||El proyecto debe contener una lista de todos los archivos y debe ser capaz de enumerar la lista de archivos mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). El proyecto también debería exponer los nombres de elemento a través de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implementación y compatibilidad con búsqueda de nombres (incluyendo archivos especiales) a través de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementación.|  
|Formato de texto|X|X|Cuando sea posible, los archivos deben estar en formato de texto para admitir la combinación de diferentes versiones. Los archivos que no están en formato de texto no se pueden combinar con otras versiones del archivo más adelante. El formato de texto preferido es XML.|  
|Basada en referencias|X||Los proyectos basados en la referencia se admiten fácilmente en el control de código fuente. Sin embargo, los proyectos basados en el directorio también son compatibles con control de código fuente, siempre y cuando el proyecto puede generar una lista de sus archivos a petición, independientemente de que esos archivos existan en el disco. Al abrir un proyecto de control de código fuente, el archivo de proyecto está inactivo primero antes de cualquiera de sus archivos.|  
|Conservar objetos y propiedades en orden predecible|X|X|Conserve sus archivos en un orden predecible, como el orden alfabético, para facilitar la combinación.|  
|Volver a cargar|X|X|Cuando cambia un archivo en disco, el editor debe poder volver a cargarlo. Al participar en el control de código fuente, el entorno se volverá a cargar datos automáticamente mediante una llamada a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementación. El caso de volver a cargar más difícil es cuando se produce una desprotección cuando llama a IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y procesamiento de información. Sin embargo, el código de recarga debe ser capaz de ejecutar en esta situación.<br /><br /> El entorno vuelve a cargar automáticamente archivos de proyecto. Sin embargo, debe implementar un proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> si ha anidado jerarquías para admitir la recarga anidan archivos de proyecto.|  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)

