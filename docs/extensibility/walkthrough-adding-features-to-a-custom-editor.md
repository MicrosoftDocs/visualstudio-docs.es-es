---
title: 'Tutorial: Agregar características a un Editor personalizado | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14642a13553f3c4a09b86daa2d7638183fe7d8d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Tutorial: Agregar características a un Editor personalizado
Después de crear un editor personalizado, puede agregar más características a él.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Para crear un editor para un paquete VSPackage  
  
1.  Crear un editor personalizado mediante la plantilla de proyecto de paquete de Visual Studio.  
  
     Para obtener más información, consulte [Tutorial: crear un Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Decida si desea que el editor para admitir una vista única o varias vistas.  
  
     Un editor que admita la **nueva ventana** comando, o tiene la vista de formulario y vista de código, se requiere objetos de datos de documentos independientes y objetos de vista de documento. En un editor que admite una sola vista, el objeto de datos de documento y el objeto de vista de documento se pueden implementar en el mismo objeto.  
  
     Para obtener un ejemplo de varias vistas, vea [admitir varias vistas de documento](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementar un generador de editores implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz.  
  
     Para obtener más información, consulte [generadores de editores](../extensibility/editor-factories.md).  
  
4.  Decida si desea que el editor para utilizar la activación en contexto o simplificado de incrustación para administrar la ventana de objetos de vista de documento.  
  
     Una ventana del editor de incrustación simplificada hospeda una vista estándar del documento, mientras que una ventana del editor de activación en contexto hospeda un control ActiveX u otro objeto activo como su vista de documento. Para obtener más información, consulte [simplificado incrustar](../extensibility/simplified-embedding.md) y [activación en contexto](../extensibility/in-place-activation.md).  
  
5.  Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para controlar comandos.  
  
6.  Proporcionar persistencia de documento y la respuesta a los cambios de archivo externo haciendo lo siguiente:  
  
    1.  Para conservar el archivo, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> y <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> en el objeto de datos de documentos de su editor.  
  
    2.  Para responder a los cambios de archivo externo, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> en el objeto de datos de documentos de su editor.  
  
        > [!NOTE]
        >  Llame a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> para obtener un puntero a `IVsFileChangeEx`.  
  
7.  Coordinar eventos de edición de documentos con control de código fuente. Para hacerlo:  
  
    1.  Obtener un puntero al `IVsQueryEditQuerySave2` mediante una llamada a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Cuando se produce el primer evento de edición, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método.  
  
         Esto pide al usuario que desproteger el archivo si no está activada. Asegúrese de controlar una condición de "archivo no está desprotegido" para evitar errores  
  
    3.  De forma similar, antes de guardar el archivo, llame al método el <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> método.  
  
         Este método pide al usuario que guarde el archivo si no se ha guardado, o si ha cambiado desde la última vez que guardó.  
  
8.  Habilitar la **propiedades** ventana para mostrar las propiedades para el texto seleccionado en el editor. Para hacerlo:  
  
    1.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> cambia cada selección de texto de tiempo, pasar en la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Llame a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> service para obtener un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Permitir a los usuarios arrastrar y colocar elementos entre el editor y el **cuadro de herramientas**, o entre editores externos (por ejemplo, Microsoft Word) y la **cuadro de herramientas**. Para hacerlo:  
  
    1.  Implemente `IDropTarget` en su editor de alerte al IDE que su editor es un destino de colocación.  
  
    2.  Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfaz en la vista para el editor puede habilitar y deshabilitar elementos de la **cuadro de herramientas**.  
  
    3.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> y llame a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> service para obtener un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfaces.  
  
         Esto permite que el paquete de VS agregar nuevos elementos a la **cuadro de herramientas**.  
  
10. Decida si desea que todas las demás características opcionales para el editor.  
  
    -   Si desea que el editor para admitir buscar y reemplazar comandos, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Si desea utilizar una ventana de herramientas de esquema de documento en el editor, implemente `IVsDocOutlineProvider`.  
  
    -   Si desea usar una barra de estado en el editor, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> y llame a `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> para obtener un puntero a `IVsStatusBar`.  
  
         Por ejemplo, un editor puede mostrar línea / información de columna, el modo de selección (transmitir / cuadro) y el modo de inserción (Insertar / /overstrike).  
  
    -   Si desea que el editor para admitir la `Undo` de comandos, el método recomendado es usar el modelo de administrador de deshacer OLE. Como alternativa, puede tener el identificador de editor el `Undo` comando directamente.  
  
11. Crear registro de información, incluidos los GUID para el VSPackage, los menús, el editor y otras características.  
  
     El siguiente es un ejemplo de código que tendría que poner en la secuencia de comandos del archivo .rgs para demostrar cómo registrar correctamente un editor genérico.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Implementar la compatibilidad con la Ayuda contextual.  
  
     Esto permite ofrecer soporte F1 Ayuda y la ventana Ayuda dinámica para los elementos en el editor. Para obtener más información sobre esto, consulte [Cómo: proporcionar contexto para los editores](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Exponer un modelo de objetos de automatización en el editor de implementando la `IDispatch` interfaz.  
  
     Para obtener más información, consulte [que contribuyen al modelo de automatización](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Programación sólida  
  
-   Se crea la instancia del editor cuando el IDE llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método. Si el editor admite varias vistas, `CreateEditorInstance` crea los datos del documento y los objetos de vista de documento. Si el objeto de datos del documento ya está abierto, un valor no nulo `punkDocDataExisting` valor se pasa a `IVsEditorFactory::CreateEditorInstance`. Su implementación del generador de editor debe determinar si un objeto de datos del documento existente es compatible mediante la consulta para las interfaces adecuadas en él. Para obtener más información, consulte [admitir varias vistas de documento](../extensibility/supporting-multiple-document-views.md).  
  
-   Si utiliza el enfoque de incrustación simplificado, implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz.  
  
-   Si decide utilizar la activación en contexto, implementar las interfaces siguientes:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  El `IOleInPlaceComponent` interfaz se utiliza para evitar la combinación de menús OLE 2.  
  
     Su `IOleCommandTarget` implementación controla los comandos como **cortar**, **copia**, y **pegar**. Al implementar `IOleCommandTarget`, decida si el editor requiere su propio archivo .vsct para definir su propia estructura de menús de comando o si pueden implementar comandos estándares definidos por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Por lo general, editores de usarán y extienden los menús del IDE y definen sus propias barras de herramientas. Sin embargo, a menudo es necesario para un editor definir sus propios comandos específicos además de usar el conjunto de comandos estándar del IDE. Para ello, el editor debe declarar los comandos estándares se utiliza y, a continuación, se definen nuevos comandos, menús contextuales, menús de nivel superior y las barras de herramientas en un archivo .vsct. Si creas una activación en contexto en el editor, a continuación, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> y defina los menús y barras de herramientas para el editor en un archivo .vsct en lugar de utilizar la combinación de menús OLE 2.  
  
-   Para evitar que los comandos de menú saturar en la interfaz de usuario, debe usar los comandos existentes en el IDE antes de crear nuevos comandos. Comandos compartidas se definen en SharedCmdDef.vsct y ShellCmdDef.vsct. Estos archivos se instalan de forma predeterminada en el subdirectorio VisualStudioIntegration\Common\Inc de su [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalación.  
  
-   `ISelectionContainer` puede expresar selecciones múltiples e individuales. Cada objeto seleccionado se implementa como un `IDispatch` objeto.  
  
-   El IDE implementa `IOleUndoManager` como un servicio puede tener acceso desde una <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> o como un objeto que se puede crear instancias a través de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Implementa la editor el `IOleUndoUnit` interfaz para cada `Undo` acción.  
  
-   Hay dos lugares un editor personalizado puede exponer los objetos de automatización:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>Vea también  
 [Que contribuyen al modelo de automatización](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Cómo: proporcionar un contexto para los editores](../extensibility/how-to-provide-context-for-editors.md)