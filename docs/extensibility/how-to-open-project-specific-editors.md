---
title: 'Cómo: abrir editores de Project-Specific | Microsoft Docs'
description: Obtenga información sobre cómo implementar el método OpenItem con un editor específico del proyecto para que un proyecto pueda abrir un archivo enlazado a un editor para ese proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4cbba1f4d6cf0a2a5a45dd2999afa5bbf3443fca
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993788"
---
# <a name="how-to-open-project-specific-editors"></a>Cómo: abrir editores específicos del proyecto
Si un archivo de elemento abierto por un proyecto está enlazado de forma intrínseca al editor determinado para ese proyecto, el proyecto debe abrir el archivo mediante un editor específico del proyecto. El archivo no se puede delegar al mecanismo del IDE para seleccionar un editor. Por ejemplo, en lugar de usar un editor de mapas de bits estándar, puede usar esta opción de editor específica del proyecto para especificar un editor de mapa de bits específico que reconozca la información del archivo que es única para el proyecto.

 El IDE llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método cuando determina que un proyecto específico debe abrir un archivo. Para obtener más información, vea [Mostrar archivos mediante el comando Abrir archivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Utilice las instrucciones siguientes para implementar el `OpenItem` método para que el proyecto abra un archivo mediante un editor específico del proyecto.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Para implementar el método OpenItem con un editor específico del proyecto

1. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método ( `RDT_EditLock` ) para determinar si el archivo (objeto de datos de documento) ya está abierto.

    > [!NOTE]
    > Para obtener más información sobre los datos de documento y los objetos de vista de documento, vea [datos de documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Si el archivo ya está abierto, vuelva a exponer el archivo llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> método y especificando un valor de IDO_ActivateIfOpen para el `grfIDO` parámetro.

     Si el archivo está abierto y el documento es propiedad de un proyecto distinto del proyecto que realiza la llamada, se mostrará una advertencia al usuario que indica que el editor que se está abriendo procede de otro proyecto. La ventana de archivo se Surface.

3. Si el búfer de texto (objeto de datos de documento) ya está abierto y desea adjuntar otra vista, es responsabilidad suya enlazar esa vista. El enfoque recomendado para crear una instancia de una vista (objeto de vista de documento) desde el proyecto es el siguiente:

    1. Llame a `QueryService` en el <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> servicio para obtener un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interfaz.

    2. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> método para crear una instancia de la clase de vista de documento.

4. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> método, especificando el objeto de vista del documento.

     Este método localiza el objeto de vista de documento en una ventana de documento.

5. Realice las llamadas adecuadas a los <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> métodos o.

     En este momento, la vista debe inicializarse completamente y estar lista para abrirse.

6. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método para mostrar y abrir la vista.

## <a name="see-also"></a>Consulte también
- [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)
- [Cómo: abrir editores estándar](../extensibility/how-to-open-standard-editors.md)
- [Cómo: abrir editores para documentos abiertos](../extensibility/how-to-open-editors-for-open-documents.md)
