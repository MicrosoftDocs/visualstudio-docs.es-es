---
title: 'Cómo: Abrir Editores Específicos de Proyectos Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710839"
---
# <a name="how-to-open-project-specific-editors"></a>Cómo: Abrir editores específicos de proyectos
Si un archivo de elemento abierto por un proyecto está intrínsecamente enlazado al editor concreto para ese proyecto, el proyecto debe abrir el archivo mediante un editor específico del proyecto. El archivo no se puede delegar en el mecanismo del IDE para seleccionar un editor. Por ejemplo, en lugar de usar un editor de mapa de bits estándar, puede usar esta opción de editor específica del proyecto para especificar un editor de mapa de bits específico que reconozca la información del archivo que es exclusiva del proyecto.

 El IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> llama al método cuando determina que un archivo debe abrirse por un proyecto específico. Para obtener más información, consulte [Mostrar archivos mediante el comando Abrir archivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Use las siguientes directrices para implementar el método para que el `OpenItem` proyecto abra un archivo mediante un editor específico del proyecto.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Implementar el método OpenItem con un editor específico del proyecto

1. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> al`RDT_EditLock`método ( ) para determinar si el archivo (objeto de datos de documento) ya está abierto.

    > [!NOTE]
    > Para obtener más información sobre los datos de documento y los objetos de vista de documento, consulte Datos de documento y vista de [documento en editores personalizados.](../extensibility/document-data-and-document-view-in-custom-editors.md)

2. Si el archivo ya está abierto, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> vuelva a exponer el archivo `grfIDO` llamando al método y especificando un valor de IDO_ActivateIfOpen para el parámetro.

     Si el archivo está abierto y el documento es propiedad de un proyecto distinto del proyecto de llamada, se mostrará una advertencia al usuario de que el editor que se está abiertando es de otro proyecto. A continuación, aparece la ventana de archivo.

3. Si el búfer de texto (objeto de datos de documento) ya está abierto y desea adjuntarle otra vista, es responsable de enlazar esa vista. El enfoque recomendado para crear instancias de una vista (objeto de vista de documento) del proyecto es el siguiente:

    1. Llame `QueryService` al <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> servicio para obtener <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> un puntero a la interfaz.

    2. Llame <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> al método para crear una instancia de la clase de vista de documento.

4. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> al método, especificando el objeto de vista de documento.

     Este método emplaza el objeto de vista de documento en una ventana de documento.

5. Realice las llamadas <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> adecuadas <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> a los métodos o a los métodos.

     En este punto, la vista debe inicializarse completamente y estar lista para abrirse.

6. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> al método para mostrar y abrir la vista.

## <a name="see-also"></a>Vea también
- [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)
- [Cómo: Abrir editores estándar](../extensibility/how-to-open-standard-editors.md)
- [Cómo: Abrir editores para documentos abiertos](../extensibility/how-to-open-editors-for-open-documents.md)
