---
title: Guardar un documento personalizado | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 896d56dc3fd66cd3dd9e733e8ae528ab710dbd83
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619698"
---
# <a name="saving-a-custom-document"></a>Guardado de un documento personalizado
Los identificadores de entorno la **guardar**, **Guardar como**, y **guardar todo** comandos. Cuando un usuario hace clic en **guardar**, **Guardar como**, **o guardar todo** en el **archivo** menú o se cierra la solución, lo que resulta en un comando Guardar todo, lo siguiente se produce el proceso.

 ![Guardar Editor de clientes](../../extensibility/internals/media/private.gif "privada") guardar, guardar como y guardar todos los comandos de control para un editor personalizado

 Este proceso se detalla en los pasos siguientes:

1.  Para el **guardar** y **Guardar como** comandos, el entorno utiliza el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> de servicio para determinar la ventana de documento activo y, por tanto, se deben guardar qué elementos. Una vez que se conoce la ventana de documento activo, el entorno busca el puntero de la jerarquía y el identificador (ID) del elemento para el documento en la tabla de documentos en ejecución. Para obtener más información, consulte [tabla de documentos en ejecución](../../extensibility/internals/running-document-table.md).

     El comando Guardar todo, el entorno usa la información de la tabla de documentos en ejecución para compilar la lista de todos los elementos para guardar.

2.  Cuando la solución recibe un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> llamada, recorre en iteración el conjunto de elementos seleccionados (es decir, las selecciones múltiples expuestas por el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service).

3.  En cada elemento de la selección, la solución utiliza el puntero de la jerarquía para llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> método para determinar si se debe habilitar el comando de menú de guardar. Si uno o varios elementos están desfasados, está habilitado el comando Guardar. Si la jerarquía usa un editor estándar, los delegados de la jerarquía consultar dirty estado en el editor mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> método.

4.  En cada elemento seleccionado que está desfasado, la solución utiliza el puntero de la jerarquía para llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> método en las jerarquías adecuadas.

     En el caso de un editor personalizado, la comunicación entre el objeto de datos y el proyecto es privada. Por lo tanto, se tratan los problemas de persistencia especial entre estos dos objetos.

    > [!NOTE]
    >  Si implementa su propia persistencia, no olvide llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> método para ahorrar tiempo. Este método comprueba para asegurarse de que es seguro guardar el archivo (por ejemplo, el archivo no es de solo lectura).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)