---
title: 'Tutorial: Adición de características a un editor personalizado ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b145dd4d82887122009553afd883abb6cade849e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697792"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Tutorial: Agregar características a un editor personalizado
Después de crear un editor personalizado, puede agregarle más características.

## <a name="to-create-an-editor-for-a-vspackage"></a>Para crear un editor para un VSPackage

1. Cree un editor personalizado mediante la plantilla de proyecto Paquete de Visual Studio.

     Para obtener más información, consulte [Tutorial: Crear un editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Decida si desea que el editor admita una sola vista o varias vistas.

     Un editor que admite el comando **Nueva ventana** o tiene vista de formulario y vista de código, requiere objetos de datos de documento y objetos de vista de documento independientes. En un editor que admite una sola vista, el objeto de datos de documento y el objeto de vista de documento se pueden implementar en el mismo objeto.

     Para obtener un ejemplo de varias vistas, consulte [Compatibilidad con varias vistas](../extensibility/supporting-multiple-document-views.md)de documentos.

3. Implemente una fábrica de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> editores configurando la interfaz.

     Para obtener más información, consulte Fábricas de [editores](../extensibility/editor-factories.md).

4. Decida si desea que el editor utilice la activación in situ o la incrustación simplificada para administrar la ventana del objeto de vista de documento.

     Una ventana simplificada del editor de incrustación hospeda una vista de documento estándar, mientras que una ventana del editor de activación in situ hospeda un control ActiveX u otro objeto activo como su vista de documento. Para obtener más información, consulte [Incrustación simplificada](../extensibility/simplified-embedding.md) y [Activación](/visualstudio/misc/in-place-activation?view=vs-2015)in situ .

5. Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> la interfaz para controlar los comandos.

6. Proporcione la persistencia del documento y la respuesta a los cambios de archivo externo:

    1. Para conservar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> archivo, implemente y <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> en el objeto de datos de documento del editor.

    2. Para responder a los <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> cambios de archivos externos, implemente y <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> en el objeto de datos de documento del editor.

        > [!NOTE]
        > Llame `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> para obtener un `IVsFileChangeEx`puntero a .

7. Coordinar eventos de edición de documentos con control de código fuente. Siga estos pasos:

    1. Obtenga un `IVsQueryEditQuerySave2` puntero `QueryService` llamando <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>a .

    2. Cuando se produzca el primer <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> evento de edición, llame al método.

         Este método solicita al usuario que desproteja el archivo si aún no está desprotegido. Asegúrese de controlar una condición de "archivo no desprotegido" para evitar errores.

    3. Del mismo modo, antes <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> de guardar el archivo, llame al método.

         Este método solicita al usuario que guarde el archivo si no se ha guardado o si ha cambiado desde la última vez que se guardó.

8. Habilite la ventana **Propiedades** para mostrar las propiedades del texto seleccionado en el editor. Siga estos pasos:

    1. Llame <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> cada vez que cambie la <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>selección de texto, pasando la implementación de .

    2. Llame `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> al servicio para <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>obtener un puntero a .

9. Permitir a los usuarios arrastrar y colocar elementos entre el editor y el cuadro de **herramientas,** o entre editores externos (como Microsoft Word) y **el cuadro de herramientas**. Siga estos pasos:

    1. Implemente `IDropTarget` en el editor para alertar al IDE de que el editor es un destino de colocación.

    2. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> la interfaz en la vista para que el editor pueda habilitar y deshabilitar elementos en el **cuadro de herramientas**.

    3. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> y `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> llame al servicio para <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> obtener un puntero a las interfaces y.

         Estos pasos permiten que el VSPackage agregue nuevos elementos al **cuadro de herramientas.**

10. Decida si desea otras características opcionales para el editor.

    - Si desea que el editor admita <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>buscar y reemplazar comandos, implemente .

    - Si desea utilizar una ventana de herramientas de `IVsDocOutlineProvider`esquema de documento en el editor, implemente .

    - Si desea utilizar una barra de estado <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> en `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> el editor, `IVsStatusBar`implemente y llame para obtener un puntero a .

         Por ejemplo, un editor puede mostrar información de línea / columna, modo de selección (flujo / cuadro) y modo de inserción (insertar / sobreatacar).

    - Si desea que el `Undo` editor admita el comando, el método recomendado es usar el modelo de administrador de deshacer OLE. Como alternativa, puede hacer que `Undo` el editor controle el comando directamente.

11. Crear información del registro, incluidos los GUID para el VSPackage, los menús, el editor y otras características.

     A continuación se muestra un ejemplo genérico de código que pondría en el script de archivo *.rgs* para demostrar cómo registrar correctamente un editor.

    ```csharp
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

12. Implemente la compatibilidad con la Ayuda contextual.

     Este paso le permite proporcionar ayuda F1 y compatibilidad con la ventana Ayuda dinámica para los elementos del editor. Para obtener más información, consulte [Cómo: proporcionar contexto para editores](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. Exponga un modelo de objetos `IDispatch` de automatización desde el editor implementando la interfaz.

     Para obtener más información, consulta [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Programación sólida

- La instancia del editor se crea <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> cuando el IDE llama al método. Si el editor admite `CreateEditorInstance` varias vistas, crea los datos del documento y los objetos de vista de documento. Si el objeto de datos del documento `punkDocDataExisting` ya `IVsEditorFactory::CreateEditorInstance`está abierto, se pasa un valor no nulo a . La implementación de fábrica del editor debe determinar si un objeto de datos de documento existente es compatible consultando las interfaces adecuadas en él. Para obtener más información, consulte Compatibilidad con varias vistas de [documentos](../extensibility/supporting-multiple-document-views.md).

- Si utiliza el enfoque de incrustación simplificado, implemente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz.

- Si decide utilizar la activación in situ, implemente las siguientes interfaces:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > La `IOleInPlaceComponent` interfaz se utiliza para evitar la fusión de menús OLE 2.

   La `IOleCommandTarget` implementación controla comandos como **Cortar**, **Copiar**y **Pegar**. Al `IOleCommandTarget`implementar , decida si el editor requiere su propio archivo *.vsct* para definir su [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]propia estructura de menú de comandos o si puede implementar comandos estándar definidos por . Normalmente, los editores usan y extienden los menús del IDE y definen sus propias barras de herramientas. Sin embargo, a menudo es necesario que un editor defina sus propios comandos específicos además de usar el conjunto de comandos estándar del IDE. El editor debe declarar los comandos estándar que utiliza y, a continuación, definir los nuevos comandos, menús contextuales, menús de nivel superior y barras de herramientas en un archivo *.vsct.* Si crea un editor de activación in situ, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> y defina los menús y barras de herramientas para el editor en un archivo *.vsct* en lugar de usar la combinación de menús OLE 2.

- Para evitar el hacinamiento del comando de menú en la interfaz de usuario, debe usar los comandos existentes en el IDE antes de inventar nuevos comandos. Los comandos compartidos se definen en *SharedCmdDef.vsct* y *ShellCmdDef.vsct*. Estos archivos se instalan de forma predeterminada en el subdirectorio VisualStudioIntegration-Common-Inc de la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalación.

- `ISelectionContainer`pueden expresar selecciones individuales y múltiples. Cada objeto seleccionado se `IDispatch` implementa como un objeto.

- El IDE `IOleUndoManager` se implementa como <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> un servicio accesible desde un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>objeto o como un objeto que se puede crear una instancia a través de . El editor implementa `IOleUndoUnit` la `Undo` interfaz para cada acción.

- Hay dos lugares en los que un editor personalizado puede exponer objetos de automatización:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Vea también

- [Contribuir al modelo de automatización](../extensibility/internals/contributing-to-the-automation-model.md)
