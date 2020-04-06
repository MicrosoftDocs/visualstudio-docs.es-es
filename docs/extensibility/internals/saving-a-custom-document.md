---
title: Guardar un documento personalizado ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705616"
---
# <a name="saving-a-custom-document"></a>Guardado de un documento personalizado
El entorno controla los comandos **Guardar**como , **Guardar como**y **Guardar todo.** Cuando un usuario hace clic en **Guardar**, **Guardar como**o **Guardar todo** en el menú **Archivo** o cierra la solución, lo que da como resultado Guardar todo, se produce el siguiente proceso.

 ![Editor de clientes Guardar](../../extensibility/internals/media/private.gif "Private") Guardar, Guardar como y Guardar todo el control de comandos para un editor personalizado

 Este proceso se detalla en los pasos siguientes:

1. Para los comandos **Guardar** y Guardar <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> **como,** el entorno utiliza el servicio para determinar la ventana de documento activa y, por lo tanto, qué elementos se deben guardar. Una vez que se conoce la ventana de documento activa, el entorno busca el puntero de jerarquía y el identificador de elemento (itemID) para el documento en la tabla de documentos en ejecución. Para obtener más información, consulte Ejecución de tabla de [documentos](../../extensibility/internals/running-document-table.md).

     Para el comando Guardar todo, el entorno utiliza la información de la tabla de documentos en ejecución para compilar la lista de todos los elementos que se va a guardar.

2. Cuando la solución <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> recibe una llamada, recorre en iteración el conjunto de elementos seleccionados (es decir, las múltiples selecciones expuestas por el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servicio).

3. En cada elemento de la selección, la solución utiliza el puntero de jerarquía para llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> método para determinar si se debe habilitar el comando de menú Guardar. Si uno o más elementos están sucios, el comando Guardar está habilitado. Si la jerarquía utiliza un editor estándar, la jerarquía delega la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> consulta de estado sucio en el editor llamando al método.

4. En cada elemento seleccionado que está sucio, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> solución usa el puntero de jerarquía para llamar al método en las jerarquías adecuadas.

     En el caso de un editor personalizado, la comunicación entre el objeto de datos del documento y el proyecto es privada. Por lo tanto, cualquier preocupación de persistencia especial se controla entre estos dos objetos.

    > [!NOTE]
    > Si implementa su propia persistencia, asegúrese de llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> método para ahorrar tiempo. Este método comprueba que es seguro guardar el archivo (por ejemplo, el archivo no es de solo lectura).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
