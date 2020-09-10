---
title: Directrices de control de código fuente para proyectos y editores
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b783fdf7231bd3f440686a1bef2a038d9b32f2e4
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743395"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Instrucciones adicionales de control de código fuente para proyectos y editores
Hay una serie de instrucciones que se deben cumplir con los proyectos y los editores para admitir el control de código fuente.

## <a name="guidelines"></a>Directrices
 El proyecto o el editor también debe hacer lo siguiente para admitir el control de código fuente:

|Área|Project|Editor|Detalles|
|----------|-------------|------------|-------------|
|Copias privadas de archivos|X||El entorno admite copias privadas de archivos. Es decir, cada persona dada de alta en el proyecto tiene su propia copia privada de los archivos de ese proyecto.|
|Persistencia de ANSI/Unicode|X|X|Si escribe el código de persistencia, almacene los archivos en formato ANSI, ya que la mayoría de los programas de control de código fuente no admiten actualmente Unicode.|
|Enumerar archivos|X||El proyecto debe contener una lista específica de todos los archivos que contiene y debe poder enumerar la lista de archivos mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). El proyecto también debe exponer los nombres de los elementos a través <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> de su implementación y la búsqueda de nombres de soporte (incluidos los archivos especiales) a través de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementación.|
|Formato de texto|X|X|Cuando sea posible, los archivos deben estar en formato de texto para admitir la combinación de versiones diferentes. Los archivos que no están en formato de texto no se pueden combinar con otras versiones del archivo posteriormente. El formato de texto preferido es XML.|
|Basado en referencias|X||Los proyectos basados en referencia se admiten fácilmente en el control de código fuente. Sin embargo, el control de código fuente también admite proyectos basados en directorios, siempre que el proyecto pueda generar una lista de sus archivos a petición, independientemente de si estos archivos existen en el disco. Al abrir un proyecto desde el control de código fuente, el archivo de proyecto se desactivará primero antes que cualquiera de sus archivos.|
|Conservar objetos y propiedades en orden predecible|X|X|Conservar los archivos en un orden predecible, como el orden alfabético, para facilitar la combinación.|
|Recargar|X|X|Cuando un archivo cambia en el disco, el editor debe poder volver a cargarlo. Al participar en el control de código fuente, el entorno volverá a cargar los datos mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementación. El caso de recarga más difícil es cuando se produce una desprotección cuando se llama a IVsQueryEditQuerySave:: <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y se procesa información. Sin embargo, el código de recarga debe ser capaz de ejecutarse en esta situación.<br /><br /> El entorno vuelve a cargar automáticamente los archivos de proyecto. Sin embargo, un proyecto debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> si tiene jerarquías anidadas para admitir la recarga de archivos de proyecto anidados.|

## <a name="see-also"></a>Vea también
- [Compatibilidad con el control de código fuente](../../extensibility/internals/supporting-source-control.md)
