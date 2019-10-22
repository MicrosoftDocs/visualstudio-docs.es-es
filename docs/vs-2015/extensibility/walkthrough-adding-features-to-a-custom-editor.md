---
title: 'Tutorial: Agregar características a un Editor personalizado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d14fb36298518409df34302f9346e186f0b0263
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825163"
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Tutorial: Agregar características a un editor personalizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después de crear un editor personalizado, puede agregar más características en él.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Para crear un editor para un VSPackage  
  
1. Crear un editor personalizado mediante la plantilla de proyecto de paquete de Visual Studio.  
  
     Para obtener más información, vea [Tutorial: Crear un Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2. Decida si desea que el editor para admitir una vista única o varias vistas.  
  
     Un editor que admite el **nueva ventana** de comandos, o tiene la vista de formulario y vista de código, requiere objetos de documento independiente de datos y objetos de vista de documento. En un editor que admite una sola vista, el objeto de datos y el objeto de vista de documento se pueden implementar en el mismo objeto.  
  
     Para obtener un ejemplo de varias vistas, consulte [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
3. Implementar un generador de editores implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz.  
  
     Para obtener más información, consulte [generadores de editores](../extensibility/editor-factories.md).  
  
4. Decida si desea que el editor para utilizar la activación en contexto o incrustación para administrar la ventana de objeto de vista de documentos simplificada.  
  
     Una ventana del editor de incrustación simplificada hospeda una vista de documento estándar, mientras que una ventana del editor de activación en contexto que hospeda un control ActiveX u otro objeto como su vista del documento activo. Para obtener más información, consulte [incrustación simplificada](../extensibility/simplified-embedding.md) y [activación en contexto](../misc/in-place-activation.md).  
  
5. Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para controlar los comandos.  
  
6. Proporciona persistencia del documento y respuesta a los cambios de archivo externo haciendo lo siguiente:  
  
    1. Para conservar el archivo, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> y <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> en el objeto de datos del documento de su editor.  
  
    2. Para responder a los cambios de archivo externo, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> en el objeto de datos del documento de su editor.  
  
        > [!NOTE]
        > Llame a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> para obtener un puntero a `IVsFileChangeEx`.  
  
7. Coordinar eventos de edición de documentos con control de código fuente. Para hacerlo:  
  
    1. Obtener un puntero a `IVsQueryEditQuerySave2` mediante una llamada a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2. Cuando se produce el primer evento de edición, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método.  
  
         Esto pide al usuario que desproteja el archivo si ya no está desprotegido por. Asegúrese de controlar una condición de "archivo no está desprotegido" para evitar errores  
  
    3. De forma similar, antes de guardar el archivo, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> método.  
  
         Este método pide al usuario que guarde el archivo si no se ha guardado, o si ha cambiado desde la última vez que guardó.  
  
8. Habilitar la **propiedades** ventana para mostrar las propiedades para el texto seleccionado en el editor. Para hacerlo:  
  
    1. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> cambia cada selección de texto de tiempo, pasar en la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2. Llame a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> service para obtener un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Permitir que los usuarios arrastrar y soltar elementos entre el editor y el **cuadro de herramientas**, o entre editores externos (como Microsoft Word) y la **cuadro de herramientas**. Para hacerlo:  
  
    1. Implemente `IDropTarget` en el editor de alerte al IDE que su editor es un destino de colocación.  
  
    2. Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfaz en la vista, por lo que puede habilitar y deshabilitar elementos en el editor de la **cuadro de herramientas**.  
  
    3. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> y llamar a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> service para obtener un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfaces.  
  
         Esto permite que el VSPackage agregar nuevos elementos a la **cuadro de herramientas**.  
  
10. Decida si desea que todas las demás características opcionales para el editor.  
  
    - Si desea que el editor para admitir buscar y reemplazar los comandos, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    - Si desea utilizar una ventana de herramientas de esquema de documento en el editor, implemente `IVsDocOutlineProvider`.  
  
    - Si desea usar una barra de estado en el editor, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> y llamar a `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> para obtener un puntero a `IVsStatusBar`.  
  
         Por ejemplo, un editor puede mostrar línea / información de columna, el modo de selección (transmitir / cuadro) y el modo de inserción (insert / /overstrike).  
  
    - Si desea que el editor para admitir la `Undo` comando, el método recomendado es usar el modelo del Administrador de deshacer OLE. Como alternativa, puede tener el identificador de editor el `Undo` comando directamente.  
  
11. Creación de registro de información, incluidos los GUID para el VSPackage, los menús, el editor y otras características.  
  
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
  
     Esto le permite ofrecer soporte ventana Ayuda dinámica y la Ayuda F1 para los elementos en el editor. Para obtener más información, vea [Cómo: Proporcionar contexto para los editores](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Exponer un modelo de objetos de automatización desde el editor mediante la implementación de la `IDispatch` interfaz.  
  
     Para obtener más información, consulta [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Programación sólida  
  
- Se crea la instancia del editor cuando el IDE llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método. Si el editor admite varias vistas, `CreateEditorInstance` crea los datos del documento y los objetos de vista de documento. Si el objeto de datos ya está abierto, un valor no null `punkDocDataExisting` valor se pasa a `IVsEditorFactory::CreateEditorInstance`. Su implementación del generador de editor debe determinar si un objeto de datos del documento existente es compatible mediante la consulta de interfaces adecuadas en él. Para obtener más información, consulte [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
- Si utiliza el enfoque de incrustación simplificado, implementar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz.  
  
- Si decide utilizar la activación en contexto, implementar las interfaces siguientes:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    > El `IOleInPlaceComponent` interfaz se utiliza para evitar la combinación de menús OLE 2.  
  
     Su `IOleCommandTarget` implementación controla los comandos como **cortar**, **copia**, y **pegar**. Al implementar `IOleCommandTarget`, decidir si el editor que requiere su propio archivo .vsct para definir su propia estructura de menús de comandos o si se pueden implementar los comandos estándares definidos por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Normalmente, editores de usarán y amplían los menús del IDE y definen sus propias barras de herramientas. Sin embargo, a menudo es necesario para un editor definir sus propios comandos específicos además de usar el conjunto de comandos estándar del IDE. Para ello, el editor debe declarar los comandos estándar utiliza y, a continuación, define los nuevos comandos, menús contextuales, menús de nivel superior y las barras de herramientas en un archivo .vsct. Si crea una activación en contexto del editor, a continuación, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> y defina los menús y barras de herramientas para el editor en un archivo .vsct en lugar de usar la combinación de menús OLE 2.  
  
- Para evitar la aglomeración en la interfaz de usuario de comando de menú, debe usar los comandos existentes en el IDE antes de tener que inventar nuevos comandos. Los comandos compartidos se definen en SharedCmdDef.vsct y ShellCmdDef.vsct. Estos archivos se instalan de forma predeterminada en el subdirectorio VisualStudioIntegration\Common\Inc de su [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] instalación.  
  
- `ISelectionContainer` puede expresar sencillas y múltiples selecciones. Cada objeto seleccionado se implementa como un `IDispatch` objeto.  
  
- El IDE implementa `IOleUndoManager` como un servicio accesible desde un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> o como un objeto que se puede crear instancias mediante <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. El editor de implementa la `IOleUndoUnit` interfaz para cada `Undo` acción.  
  
- Hay dos lugares un editor personalizado puede exponer los objetos de automatización:  
  
  - `Document.Object`  

  - `Window.Object`  
  
## <a name="see-also"></a>Vea también  
 [Contribución al modelo de automatización](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Cómo: Proporcionar el contexto para los editores](../extensibility/how-to-provide-context-for-editors.md)
