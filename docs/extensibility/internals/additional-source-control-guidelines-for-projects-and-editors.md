---
title: Directrices adicionales de control de código fuente para proyectos y editores ? Microsoft Docs
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
ms.openlocfilehash: 181f6c10ff7ce95cd3a37151f117353d1bb47d41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710108"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Directrices adicionales de control de código fuente para proyectos y editores
Hay una serie de directrices que los proyectos y editores deben cumplir para admitir el control de código fuente.

## <a name="guidelines"></a>Directrices
 El proyecto o editor también debe hacer lo siguiente para admitir el control de código fuente:

|Área|proyecto|Editor|Detalles|
|----------|-------------|------------|-------------|
|Copias privadas de archivos|X||El entorno admite copias privadas de archivos. Es decir, cada persona alistada en el proyecto tiene su propia copia privada de los archivos en ese proyecto.|
|Persistencia ANSI/Unicode|X|X|Si escribe el código de persistencia, conserve los archivos en el formulario ANSI porque la mayoría de los programas de control de código fuente no admiten Unicode actualmente.|
|Enumerar archivos|X||El proyecto debe contener una lista específica de todos los archivos que contiene <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> y debe ser capaz de enumerar la lista de archivos mediante el o (VSH_PROPID_First_Child/Next_Sibling). El proyecto también debe exponer <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> los nombres de elemento a través de su implementación y búsqueda de nombres de soporte técnico (incluidos archivos especiales) a través de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementación.|
|Formato de texto|X|X|Cuando sea posible, los archivos deben estar en formato de texto para admitir la fusión de diferentes versiones. Los archivos que no están en formato de texto no se pueden combinar con otras versiones del archivo más adelante. El formato de texto preferido es XML.|
|Basado en referencias|X||Los proyectos basados en referencias se admiten fácilmente en el control de código fuente. Sin embargo, los proyectos basados en directorios también son compatibles con el control de código fuente siempre que el proyecto pueda generar una lista de sus archivos a petición, independientemente de si esos archivos existen en el disco. Al abrir un proyecto desde el control de código fuente, el archivo de proyecto se derriba primero antes de cualquiera de sus archivos.|
|Conservar objetos y propiedades en orden predecible|X|X|Persiste tus archivos en un orden predecible, como el orden alfabético, para facilitar la fusión.|
|Recargar|X|X|Cuando un archivo cambia en el disco, el editor debe poder volver a cargarlo. Cuando participe en el control de código fuente, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> el entorno volverá a cargar los datos por usted llamando a la implementación. El caso de recarga más difícil es cuando se produce una<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> desprotección cuando se ha llamado a IVsQueryEditQuerySave:: y está procesando información. Sin embargo, el código de recarga debe poder ejecutarse en esta situación.<br /><br /> El entorno vuelve a cargar automáticamente los archivos de proyecto. Sin embargo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> un proyecto debe implementarse si tiene jerarquías anidadas para admitir la recarga de archivos de proyecto anidados.|

## <a name="see-also"></a>Vea también
- [Control de código fuente de soporte](../../extensibility/internals/supporting-source-control.md)
