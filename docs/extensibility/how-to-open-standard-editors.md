---
title: 'Cómo: Abrir Editores Estándar Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710783"
---
# <a name="how-to-open-standard-editors"></a>Cómo: Abrir editores estándar
Al abrir un editor estándar, permite que el IDE determine un editor estándar para un tipo de archivo designado, en lugar de especificar un editor específico del proyecto para el archivo.

 Complete el siguiente procedimiento <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> para implementar el método. Esto abrirá un archivo de proyecto en un editor estándar.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Para implementar el método OpenItem con un editor estándar

1. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> `RDT_EditLock`a ( ) para determinar si el archivo de objeto de datos de documento ya está abierto.

2. Si el archivo ya está abierto, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> vuelva a exponer el `IDO_ActivateIfOpen` archivo `grfIDO` llamando al método, especificando un valor para el parámetro.

     Si el archivo está abierto y el documento es propiedad de un proyecto diferente del proyecto de llamada, el proyecto recibe una advertencia de que el editor que se está abrendo es de otro proyecto. A continuación, aparece la ventana de archivo.

3. Si el documento no está abierto o no <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> está`OSE_ChooseBestStdEditor`en la tabla de documentos en ejecución, llame al método ( ) para abrir un editor estándar para el archivo.

     Cuando se llama al método, el IDE realiza las siguientes tareas:

    1. En el Registro, el IDE examina la subclave Editors/-guidEditorType/Extensions para determinar qué editor puede abrir el archivo y tiene la prioridad más alta para hacerlo.

    2. Después de que el IDE haya determinado qué <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>editor puede abrir el archivo, el IDE llama . La implementación del editor de este método devuelve información <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> necesaria para que el IDE llame y sitio el documento recién abierto.

    3. Por último, el IDE carga el documento mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>la interfaz de persistencia habitual, como .

    4. Si el IDE ha determinado previamente que la jerarquía <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> o el elemento de jerarquía está <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> disponible, el IDE llama al método en el proyecto para obtener un puntero de contexto de nivel de proyecto para volver a pasar con la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> llamada al método.

4. Devuelve <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> un puntero al IDE cuando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> el IDE llama al proyecto si desea permitir que el editor obtenga contexto del proyecto.

     Al realizar este paso, el proyecto permite ofrecer servicios adicionales al editor.

     Si la vista de documento o el objeto de vista de documento se ha <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>ubicado correctamente en un marco de ventana, el objeto se inicializa con sus datos llamando a .

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Abrir y guardar elementos del proyecto](../extensibility/internals/opening-and-saving-project-items.md)
- [Cómo: Abrir editores específicos de proyectos](../extensibility/how-to-open-project-specific-editors.md)
- [Cómo: Abrir editores para documentos abiertos](../extensibility/how-to-open-editors-for-open-documents.md)
- [Mostrar archivos mediante el comando Abrir archivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
