---
title: Guardar un documento estándar ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705548"
---
# <a name="saving-a-standard-document"></a>Guardado de un documento estándar
El entorno controla los comandos Guardar, Guardar como y Guardar todo. Cuando un usuario selecciona **Guardar**, **Guardar como**o **Guardar todo** en el menú **Archivo** o cierra la solución, lo que da como resultado **Guardar todo**, se produce el siguiente proceso.

 ![Editor estándar](../../extensibility/internals/media/public.gif "Público") Guardar, Guardar como y Guardar todo el control de comandos para un editor estándar

 Este proceso se detalla en los pasos siguientes:

1. Cuando se seleccionan los comandos **Guardar** <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> y Guardar **como,** el entorno utiliza el servicio para determinar la ventana de documento activa y, por lo tanto, qué elementos se deben guardar. Una vez que se conoce la ventana de documento activa, el entorno busca el puntero de jerarquía y el identificador de elemento (itemID) para el documento en la tabla de documentos en ejecución. Para obtener más información, consulte Ejecución de tabla de [documentos](../../extensibility/internals/running-document-table.md).

    Cuando se selecciona el comando **Guardar todo,** el entorno utiliza la información de la tabla de documentos en ejecución para compilar la lista de todos los elementos que se va a guardar.

2. Cuando la solución <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> recibe una llamada, recorre en iteración el conjunto de elementos seleccionados (es decir, las múltiples selecciones expuestas por el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servicio).

3. En cada elemento de la selección, la solución utiliza el puntero de jerarquía para llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> método para determinar si se debe habilitar el comando de menú **Guardar.** Si uno o más elementos están sucios, el comando **Guardar** está habilitado. Si la jerarquía utiliza un editor estándar, la jerarquía delega la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> consulta de estado sucio en el editor llamando al método.

4. En cada elemento seleccionado que está sucio, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> solución usa el puntero de jerarquía para llamar al método en las jerarquías adecuadas.

    Es común que la jerarquía utilice un editor estándar para editar el documento. En este caso, el objeto de datos <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> de documento para ese editor debe admitir la interfaz. Al recibir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> la llamada al método, el proyecto debe informar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> al editor de que el documento se está guardando llamando al método en el objeto de datos del documento. El editor puede permitir que el entorno controle `Query Service` el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> cuadro de diálogo **Guardar** como, llamando a la interfaz. Esto devuelve un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> puntero a la interfaz. A continuación, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> editor debe llamar al método, pasando un puntero a la implementación del <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> editor mediante el `pPersistFile` parámetro. A continuación, el entorno realiza la operación Guardar y proporciona el cuadro de diálogo **Guardar** como para el editor. A continuación, el entorno <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>vuelve a llamar al editor con .

5. Si el usuario está intentando guardar un documento sin título (es decir, un documento no guardado anteriormente), se realiza realmente un comando Guardar como.

6. Para el comando Guardar como, el entorno muestra el cuadro de diálogo Guardar como, solicitando al usuario un nombre de archivo.

    Si el nombre del archivo ha cambiado, la jerarquía es responsable de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>actualizar la información almacenada en caché del marco de documento mediante una llamada (VSFPROPID_MkDocument).

   Si el comando **Guardar como** mueve la ubicación del documento y la jerarquía es sensible a la ubicación del documento, la jerarquía es responsable de entregar la propiedad de la ventana de documento abierta a otra jerarquía. Por ejemplo, esto ocurre si el proyecto realiza un seguimiento de si el archivo es un archivo interno o externo (archivo varios) en relación con el proyecto. Use el siguiente procedimiento para cambiar la propiedad de un archivo al proyecto Archivos varios.

## <a name="changing-file-ownership"></a>Cambio de la propiedad del archivo

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Para cambiar la propiedad del archivo al proyecto Archivos varios

1. Servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> consulta para la interfaz.

     Se devuelve <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> un puntero a.

2. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> al`pszMkDocumentNew` `punkWindowFrame`método ( , ) para transferir el documento a la nueva jerarquía. La jerarquía que realiza el comando Guardar como llama a este método.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
