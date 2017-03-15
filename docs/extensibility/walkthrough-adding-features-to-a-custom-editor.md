---
title: "Tutorial: Agregar caracter&#237;sticas a un Editor personalizado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] personalizados - agregan características"
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# Tutorial: Agregar caracter&#237;sticas a un Editor personalizado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Después de crear un editor personalizado, puede agregar más características a él.  
  
### Para crear un editor para un VSPackage  
  
1.  Crear un editor personalizado mediante la plantilla de proyecto de paquete de Visual Studio.  
  
     Para obtener más información, consulta [Tutorial: Crear un Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Decida si desea que el editor para admitir una vista única o varias vistas.  
  
     Un editor que admita la **nueva ventana** comando, o tiene la vista formulario y vista de código, requiere objetos de datos de documentos independientes y objetos de vista de documento. En un editor que admite sólo una vista, el objeto de datos de documento y el objeto de vista de documento pueden implementarse en el mismo objeto.  
  
     Para obtener un ejemplo de varias vistas, consulte [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementar un generador de editores implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz.  
  
     Para obtener más información, consulta [Generadores de editores](../extensibility/editor-factories.md).  
  
4.  Decida si desea utilizar la activación en contexto el editor o para administrar la ventana de objetos de vista de documento con incrustación simplificada.  
  
     Una ventana del editor de incrustación simplificada hospeda una vista de documento estándar, mientras que una ventana del editor de activación en contexto hospeda un control ActiveX u otro objeto como su vista del documento activo. Para obtener más información, vea [Incrustación simplificada](../extensibility/simplified-embedding.md) y [activación en contexto](../misc/in-place-activation.md).  
  
5.  Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para controlar los comandos.  
  
6.  Proporcionar persistencia de documento y la respuesta a los cambios de archivo externo haciendo lo siguiente:  
  
    1.  Para conservar el archivo, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> y <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> en el objeto de datos de documentos de su editor.  
  
    2.  Para responder a los cambios de archivo externo, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> en el objeto de datos de documentos de su editor.  
  
        > [!NOTE]
        >  Llamar a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> para obtener un puntero a `IVsFileChangeEx`.  
  
7.  Coordinar eventos de edición de documentos con control de código fuente. Para hacerlo:  
  
    1.  Obtener un puntero a `IVsQueryEditQuerySave2` mediante una llamada a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Cuando se produce el primer evento de edición, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> \(método\).  
  
         Se pide al usuario que desproteja el archivo si ya no está desprotegido por. Asegúrese de controlar una condición de "archivo no está desprotegido" para evitar errores  
  
    3.  De forma similar, antes de guardar el archivo, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> \(método\).  
  
         Este método pide al usuario que guarde el archivo si no se ha guardado, o si ha cambiado desde la última vez que guardó.  
  
8.  Habilitar la **propiedades** ventana para mostrar las propiedades para el texto seleccionado en el editor. Para hacerlo:  
  
    1.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> cada selección de texto de tiempo cambia, pasando en la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Llamar a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> service para obtener un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Permitir a los usuarios arrastrar y colocar elementos entre el editor y el **cuadro de herramientas**, o entre editores externos \(como Microsoft Word\) y la **herramientas**. Para hacerlo:  
  
    1.  Implemente `IDropTarget` en el editor de la IDE de alerta que el editor es un destino de colocación.  
  
    2.  Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfaz en la vista para el editor puede habilitar y deshabilitar elementos de la **herramientas**.  
  
    3.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> y llamar a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> service para obtener un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfaces.  
  
         Esto permite el VSPackage agregar nuevos elementos a la **herramientas**.  
  
10. Decida si desea que todas las demás características opcionales para el editor.  
  
    -   Si desea que el editor para admitir buscar y reemplazar los comandos, implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Si desea utilizar una ventana de herramientas de esquema de documento en el editor, implementar `IVsDocOutlineProvider`.  
  
    -   Si desea usar una barra de estado en el editor, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> y llame a `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> para obtener un puntero a `IVsStatusBar`.  
  
         Por ejemplo, un editor puede mostrar línea \/ información de columna, el modo de selección \(transmitir \/ cuadro\) y el modo de inserción \(insert \/ \/overstrike\).  
  
    -   Si desea que el editor para admitir el `Undo` de comandos, el método recomendado es usar el modelo de administrador de deshacer OLE. Como alternativa, puede tener el identificador de editor el `Undo` comando directamente.  
  
11. Crear registro de información, incluidos los GUID para el paquete VSPackage, los menús, el editor y otras características.  
  
     El siguiente es un ejemplo de código que puede colocar en la secuencia de comandos del archivo .rgs para demostrar cómo registrar correctamente un editor genérico.  
  
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
  
     Esto le permite proporcionar compatibilidad con ayuda de F1 y la ventana Ayuda dinámica para los elementos en el editor. Para obtener más información sobre este tema vea [Cómo: proporcionar contexto para los editores](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Exponer un modelo de objetos de automatización de su editor mediante la implementación de la `IDispatch` interfaz.  
  
     Para obtener más información, consulta [Que contribuyen al modelo de automatización](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## Programación sólida  
  
-   Se crea la instancia del editor cuando el IDE se llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método. Si el editor admite varias vistas, `CreateEditorInstance` crea los datos del documento y los objetos de vista de documento. Si el objeto de datos de documento ya está abierto, un valor no null `punkDocDataExisting` valor se pasa a `IVsEditorFactory::CreateEditorInstance`. Su implementación del generador de editor debe determinar si un objeto de datos de documento existente es compatible mediante la consulta de las interfaces adecuadas en él. Para obtener más información, consulta [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md).  
  
-   Si utiliza el enfoque de incrustación simplificado, implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz.  
  
-   Si decide utilizar la activación en contexto, implementar las interfaces siguientes:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  El `IOleInPlaceComponent` interfaz se utiliza para evitar la combinación de menús OLE 2.  
  
     Su `IOleCommandTarget` controla la implementación de comandos como **Cortar**, **copia**, y **Pegar**. Al implementar `IOleCommandTarget`, decida si el editor requiere su propio archivo .vsct para definir su propia estructura de menú de comandos o si se pueden implementar comandos estándares definidos por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Normalmente, editores de usarán y extienden los menús del IDE y definen sus propias barras de herramientas. Sin embargo, a menudo es necesario para un editor definir sus propios comandos específicos además de usar el conjunto de comandos estándar del IDE. Para ello, el editor debe declarar los comandos estándar se utiliza y, a continuación, definir los nuevos comandos, menús contextuales, menús de nivel superior y las barras de herramientas en un archivo de vsct. Si crea una activación en contexto del editor, a continuación, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> y defina los menús y barras de herramientas para el editor en un archivo de vsct en lugar de utilizar la combinación de menús OLE 2.  
  
-   Para evitar la aglomeración en la interfaz de usuario de comando de menú, debe utilizar los comandos existentes en el IDE antes de inventar nuevos comandos. Comandos compartidas se definen en SharedCmdDef.vsct y ShellCmdDef.vsct. Estos archivos se instalan de forma predeterminada en el subdirectorio VisualStudioIntegration\\Common\\Inc de su [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalación.  
  
-   `ISelectionContainer` puede expresar simples y múltiples selecciones. Cada objeto seleccionado se implementa como un `IDispatch` objeto.  
  
-   Implementa el IDE `IOleUndoManager` como un servicio puede tener acceso desde un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> o como un objeto que se puede crear instancias mediante <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Implementa la editor el `IOleUndoUnit` interfaz para cada `Undo` acción.  
  
-   Hay dos lugares un editor personalizado puede exponer objetos de automatización:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## Vea también  
 [Que contribuyen al modelo de automatización](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Cómo: proporcionar contexto para los editores](../extensibility/how-to-provide-context-for-editors.md)