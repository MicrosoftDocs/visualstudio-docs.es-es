---
title: Guardar un documento personalizado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705616"
---
# <a name="saving-a-custom-document"></a>Guardado de un documento personalizado
El entorno controla los comandos **Guardar**, **Guardar como**y **guardar todo** . Cuando un usuario hace clic en **Guardar**, **Guardar como** **o guardar todo** en el menú **archivo** o cierra la solución, lo que da lugar a guardar todo, se produce el siguiente proceso.

 ![Guardado del editor del cliente](../../extensibility/internals/media/private.gif "Privados") Guardar, guardar como y guardar todo el control de comandos para un editor personalizado

 Este proceso se describe en los pasos siguientes:

1. En el caso de los comandos **Guardar** y **Guardar como** , el entorno utiliza el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servicio para determinar la ventana de documento activa y, por tanto, los elementos que se deben guardar. Una vez que se conoce la ventana de documento activa, el entorno busca el puntero de la jerarquía y el identificador de elemento (itemID) del documento en la tabla de documentos en ejecución. Para obtener más información, vea [ejecutar la tabla de documentos](../../extensibility/internals/running-document-table.md).

     En el caso del comando guardar todo, el entorno usa la información de la tabla de documentos en ejecución para compilar la lista de todos los elementos que se van a guardar.

2. Cuando la solución recibe una <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> llamada, recorre en iteración el conjunto de elementos seleccionados (es decir, las selecciones múltiples expuestas por el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servicio).

3. En cada elemento de la selección, la solución usa el puntero de jerarquía para llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> método para determinar si el comando de menú guardar debe estar habilitado. Si se han modificado uno o más elementos, el comando Guardar está habilitado. Si la jerarquía usa un editor estándar, la jerarquía delega en el editor la consulta de estado sucio mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> método.

4. En cada elemento seleccionado que está sucio, la solución usa el puntero de jerarquía para llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> método en las jerarquías adecuadas.

     En el caso de un editor personalizado, la comunicación entre el objeto de datos del documento y el proyecto es privada. Por lo tanto, los problemas de persistencia especiales se controlan entre estos dos objetos.

    > [!NOTE]
    > Si implementa su propia persistencia, asegúrese de llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> método para ahorrar tiempo. Este método realiza una comprobación para asegurarse de que es seguro guardar el archivo (por ejemplo, el archivo no es de solo lectura).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
