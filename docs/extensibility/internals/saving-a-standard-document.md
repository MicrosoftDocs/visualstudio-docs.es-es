---
title: Guardar un documento estándar | Microsoft Docs
description: Obtenga información sobre el proceso que se produce para un documento estándar para un tipo de proyecto que se agrega al IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 18e7fcb73a5ce89fae0936189eada9e3b959a55f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958458"
---
# <a name="saving-a-standard-document"></a>Guardado de un documento estándar
El entorno controla los comandos guardar, guardar como y guardar todo. Cuando un usuario selecciona **Guardar**, **Guardar como** o **guardar todo** en el menú **archivo** o cierra la solución, lo que da lugar a **guardar todo**, se produce el siguiente proceso.

 ![Editor estándar](../../extensibility/internals/media/public.gif "Público") Guardar, guardar como y guardar todo el control de comandos para un editor estándar

 Este proceso se describe en los pasos siguientes:

1. Cuando se seleccionan los comandos **Guardar** y **Guardar como** , el entorno utiliza el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servicio para determinar la ventana de documento activa y, por tanto, los elementos que se deben guardar. Una vez que se conoce la ventana de documento activa, el entorno busca el puntero de la jerarquía y el identificador de elemento (itemID) del documento en la tabla de documentos en ejecución. Para obtener más información, vea [ejecutar la tabla de documentos](../../extensibility/internals/running-document-table.md).

    Cuando se selecciona el comando **guardar todo** , el entorno usa la información de la tabla de documentos en ejecución para compilar la lista de todos los elementos que se van a guardar.

2. Cuando la solución recibe una <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> llamada, recorre en iteración el conjunto de elementos seleccionados (es decir, las selecciones múltiples expuestas por el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servicio).

3. En cada elemento de la selección, la solución usa el puntero de jerarquía para llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> método para determinar si el comando de menú **Guardar** debe estar habilitado. Si se han modificado uno o más elementos, el comando **Guardar** está habilitado. Si la jerarquía usa un editor estándar, la jerarquía delega en el editor la consulta de estado sucio mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> método.

4. En cada elemento seleccionado que está sucio, la solución usa el puntero de jerarquía para llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> método en las jerarquías adecuadas.

    Es habitual que la jerarquía use un editor estándar para editar el documento. En este caso, el objeto de datos de documento de ese editor debe admitir la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaz. Al recibir la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> llamada al método, el proyecto debe informar al editor de que el documento se está guardando llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> método en el objeto de datos del documento. El editor puede permitir que el entorno controle el cuadro de diálogo **Guardar como** , llamando a `Query Service` para la <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interfaz. Esto devuelve un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz. A continuación, el editor debe llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> método, pasando un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementación del editor mediante el `pPersistFile` parámetro. Después, el entorno realiza la operación de guardar y proporciona el cuadro de diálogo **Guardar como** para el editor. A continuación, el entorno llama de nuevo al editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .

5. Si el usuario está intentando guardar un documento sin título (es decir, un documento previamente no guardado), se realiza un comando Guardar como.

6. En el caso del comando Guardar como, el entorno muestra el cuadro de diálogo Guardar como y solicita al usuario un nombre de archivo.

    Si el nombre del archivo ha cambiado, la jerarquía es responsable de actualizar la información almacenada en caché del marco del documento llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument).

   Si el comando **Guardar como** mueve la ubicación del documento y la jerarquía es sensible a la ubicación del documento, la jerarquía es responsable de entregar la propiedad de la ventana de documento abierta a otra jerarquía. Por ejemplo, esto ocurre si el proyecto realiza un seguimiento de si el archivo es un archivo interno o externo (archivo varios) en relación con el proyecto. Utilice el procedimiento siguiente para cambiar la propiedad de un archivo en el proyecto archivos varios.

## <a name="changing-file-ownership"></a>Cambiar la propiedad del archivo

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Para cambiar la propiedad del archivo al proyecto archivos varios

1. Servicio de consulta para la <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interfaz.

     Se devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> .

2. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> `pszMkDocumentNew` método (, `punkWindowFrame` ) para transferir el documento a la nueva jerarquía. La jerarquía que realiza el comando Guardar como llama a este método.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
