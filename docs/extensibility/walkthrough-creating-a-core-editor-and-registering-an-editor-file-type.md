---
title: Crear un Editor de núcleo y registrar un tipo de archivo del Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd6514ec43cd3180d808c20d5589bf18e3a9b58b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048210"
---
# <a name="walkthrough-create-a-core-editor-and-registering-an-editor-file-type"></a>Tutorial: Crear un editor de núcleo y registrar un tipo de archivo del editor
En este tutorial se muestra cómo crear un VSPackage que se inicia el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de núcleo cuando un archivo con el *.myext* se carga la extensión de nombre de archivo.

## <a name="prerequisites"></a>Requisitos previos
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Ubicaciones de la plantilla de proyecto de paquete de Visual Studio
 La plantilla de proyecto del paquete de Visual Studio puede encontrarse en tres ubicaciones diferentes en el cuadro de diálogo **Nuevo proyecto** :

1. En **Extensibilidad de Visual Basic**. El lenguaje predeterminado del proyecto es Visual Basic.

2. En **Extensibilidad de C#**. El lenguaje predeterminado del proyecto es C#.

3. En **Extensibilidad de Otros tipos de proyectos**. El lenguaje predeterminado del proyecto es C++.

### <a name="to-create-the-vspackage"></a>Para crear el VSPackage

- Iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y cree un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage llamado `MyPackage`, tal y como se describe en [Tutorial: Crear un comando de menú VSPackage](https://msdn.microsoft.com/library/d699c149-5d1e-47ff-94c7-e1222af02c32).

### <a name="to-add-the-editor-factory"></a>Para agregar el generador de editores

1. Haga clic en el **MyPackage** , seleccione **agregar**y, a continuación, haga clic en **clase**.

2. En el **Agregar nuevo elemento** diálogo cuadro, asegúrese de que el **clase** se selecciona la plantilla, tipo `EditorFactory.cs` para el nombre y, a continuación, haga clic en **agregar** para agregar la clase al proyecto.

    El *EditorFactory.cs* archivo debería abrirse automáticamente.

3. Hacer referencia a los siguientes ensamblados desde el código.

   ```vb
   Imports System.Runtime.InteropServices
   Imports Microsoft.VisualStudio
   Imports Microsoft.VisualStudio.Shell
   Imports Microsoft.VisualStudio.Shell.Interop
   Imports Microsoft.VisualStudio.OLE.Interop
   Imports Microsoft.VisualStudio.TextManager.Interop
   Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider
   ```

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio;
   using Microsoft.VisualStudio.Shell;
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio.OLE.Interop;
   using Microsoft.VisualStudio.TextManager.Interop;
   using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;

   ```

4. Agregar un GUID para el `EditorFactory` clase agregando el `Guid` atributo inmediatamente antes de la declaración de clase.

    Puede generar un nuevo GUID mediante el *guidgen.exe* programe el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comando símbolo del sistema o haciendo clic en **crear GUID** en el **herramientas** menú. El GUID que usa aquí es sólo un ejemplo; No usar en el proyecto.

   ```vb
   <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _
   ```

   ```csharp
   [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]
   ```

5. En la definición de clase, agregue dos variables privadas para que contenga el paquete primario y un proveedor de servicios.

   ```vb
   Class EditorFactory
       Private parentPackage As Package
       Private serviceProvider As IOleServiceProvider
   ```

   ```csharp
   class EditorFactory
   {
       private Package parentPackage;
       private IOleServiceProvider serviceProvider;
   }

   ```

6. Agregue un constructor de clase pública que toma un parámetro de tipo <xref:Microsoft.VisualStudio.Shell.Package>:

   ```vb
   Public Sub New(ByVal parentPackage As Package)
       Me.parentPackage = parentPackage
   End Sub
   ```

   ```csharp
   public EditorFactory(Package parentPackage)
   {
       this.parentPackage = parentPackage;
   }
   ```

7. Modificar el `EditorFactory` declaración pueden derivar de la clase el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz.

   ```vb
   Class EditorFactory Implements IVsEditorFacto
   ```

   ```csharp
   class EditorFactory : IVsEditorFactory

   ```

8. Haga clic en <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, haga clic en **Implementar interfaz**y, a continuación, haga clic en **Implementar interfaz explícitamente**.

    Este paso agrega los cuatro métodos que deben implementarse en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz.

9. Reemplace el contenido del método `IVsEditorFactory.Close` con el código siguiente.

    ```vb
    Return VSConstants.S_OK
    ```

    ```csharp
    return VSConstants.S_OK;
    ```

10. Reemplace el contenido de la `IVsEditorFactory.SetSite` con el código siguiente.

    ```vb
    Me.serviceProvider = psp
    Return VSConstants.S_OK
    ```

    ```csharp
    this.serviceProvider = psp;
    return VSConstants.S_OK;
    ```

11. Reemplace el contenido del método `IVsEditorFactory.MapLogicalView` con el código siguiente.

    ```vb
    Dim retval As Integer = VSConstants.E_NOTIMPL
    pbstrPhysicalView = Nothing ' We support only one view.
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then
        retval = VSConstants.S_OK
    End If
    Return retval
    ```

    ```csharp
    int retval = VSConstants.E_NOTIMPL;
    pbstrPhysicalView = null;   // We support only one view.
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))
    {
        retval = VSConstants.S_OK;
    }
    return retval;
    ```

12. Reemplace el contenido del método `IVsEditorFactory.CreateEditorInstance` con el código siguiente.

    ```vb
    Dim retval As Integer = VSConstants.E_FAIL

    ' Initialize these to empty to start with
    ppunkDocView = IntPtr.Zero
    ppunkDocData = IntPtr.Zero
    pbstrEditorCaption = ""
    pguidCmdUI = Guid.Empty
    pgrfCDW = 0

    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _
    VSConstants.CEF_SILENT)) = 0 Then
        Throw New ArgumentException("Only Open or Silent is valid")
    End If
    If punkDocDataExisting <> IntPtr.Zero Then
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA
    End If

    ' Instantiate a text buffer of type VsTextBuffer.
    ' Note: we only need an IUnknown (object) interface for
    ' this invocation.
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown
    Dim pTextBuffer As Object = pTextBuffer = _
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _
    GetType(Object))

    If Not pTextBuffer Is Nothing Then
        ' "Site" the text buffer with the service provider we were
        ' provided.
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _
        IObjectWithSite)
        If Not textBufferSite Is Nothing Then
            textBufferSite.SetSite(Me.serviceProvider)
        End If

        ' Instantiate a code window of type IVsCodeWindow.
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID
        Dim pCodeWindow As IVsCodeWindow = _
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)
        If Not pCodeWindow Is Nothing Then
            ' Give the text buffer to the code window.
            ' We are giving up ownership of the text buffer!
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))

            ' Now tell the caller about all this new stuff
            ' that has been created.
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)

            ' Specify the command UI to use so keypresses are
            ' automatically dealt with.
            pguidCmdUI = VSConstants.GUID_TextEditorFactory

            ' This caption is appended to the filename and
            ' lets us know our invocation of the core editor
            ' is up and running.
            pbstrEditorCaption = " [MyPackage]"

            retval = VSConstants.S_OK
        End If
    End If
    Return retval
    ```

    ```csharp
    int retval = VSConstants.E_FAIL;

    // Initialize these to empty to start with
    ppunkDocView       = IntPtr.Zero;
    ppunkDocData       = IntPtr.Zero;
    pbstrEditorCaption = "";
    pguidCmdUI         = Guid.Empty; 
    pgrfCDW            = 0;

    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |
          VSConstants.CEF_SILENT)) == 0)
    { 
        throw new ArgumentException("Only Open or Silent is valid");
    }
    if (punkDocDataExisting != IntPtr.Zero)
    {
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;
    }

    // Instantiate a text buffer of type VsTextBuffer.
    // Note: we only need an IUnknown (object) interface for 
    // this invocation.
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(
          ref clsidTextBuffer,
          ref iidTextBuffer,
          typeof(object));

    if (pTextBuffer != null)
    {
        // "Site" the text buffer with the service provider we were
        // provided.
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;
        if (textBufferSite != null)
        {
            textBufferSite.SetSite(this.serviceProvider);
        }

        // Instantiate a code window of type IVsCodeWindow.
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;
        IVsCodeWindow pCodeWindow =
        (IVsCodeWindow)this.parentPackage.CreateInstance( 
              ref clsidCodeWindow,
              ref iidCodeWindow,
              typeof(IVsCodeWindow));
        if (pCodeWindow != null)
        {
            // Give the text buffer to the code window.
            // We are giving up ownership of the text buffer!
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);

            // Now tell the caller about all this new stuff 
            // that has been created.
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);

            // Specify the command UI to use so keypresses are 
            // automatically dealt with.
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;

            // This caption is appended to the filename and
            // lets us know our invocation of the core editor 
            // is up and running.
            pbstrEditorCaption = " [MyPackage]";

            retval = VSConstants.S_OK;
        } 
    } 
    return retval; 
    ```

13. Compile el proyecto y asegúrese de que no hay ningún error.

### <a name="to-register-the-editor-factory"></a>Para registrar el generador de editores

1. En **el Explorador de soluciones**, haga doble clic en el **Resources.resx** archivo para abrirlo en la tabla de cadenas, en el que la entrada **String1 es** seleccionado.

2. Cambiar el nombre del identificador para `IDS_EDITORNAME` y el texto para **MyPackage Editor.** Esta cadena aparece como el nombre de su editor.

3. Abra el **VSPackage.resx** de archivos, agregar una nueva cadena, establezca el nombre en **101**y establezca el valor en `IDS_EDITORNAME`. Este paso proporciona el paquete con un identificador de recurso para tener acceso a la cadena que creó.

   > [!NOTE]
   >  Si el **VSPackage.resx** archivo contiene otra cadena que el `name` atributo establecido en **101**, sustituya otro valor único, numeric, aquí y en los pasos siguientes.

4. En **el Explorador de soluciones**, abra el **MyPackagePackage.cs** archivo.

    Este archivo es el archivo de paquete principal.

5. Agregue los siguientes atributos de usuario justo antes del `Guid` atributo.

   ```vb
   <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _
   <ProvideEditorExtensionAttribute(GetType(EditorFactory), _
         ".myext", 32, NameResourceID:=101 )> _
   ```

   ```csharp
   [ProvideEditorFactory(typeof(EditorFactory), 101)]
   [ProvideEditorExtension(typeof(EditorFactory),
         ".myext", 32, NameResourceID = 101)]
   ```

    El <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> atributo asocia la *.myext* extensión con el generador de editores de archivo para que cada vez que un archivo que tiene que cargar extensión, se invoca el generador de editores.

6. Agregue una variable privada a la `MyPackage` clase justo antes del constructor y asígnele el tipo `EditorFactory`.

   ```vb
   Private editorFactory As EditorFactory
   ```

   ```csharp
   private EditorFactory editorFactory;
   ```

7. Buscar el `Initialize` (método) (puede que tenga que abrir el `Package Members` región oculta) y agregue el código siguiente después de llamar a `base.Initialize()`.

   ```vb
   'Create our editor factory and register it.
   Me.editorFactory = New EditorFactory(Me)
   MyBase.RegisterEditorFactory(Me.editorFactory)
   ```

   ```csharp
   // Create our editor factory and register it.
   this.editorFactory = new EditorFactory(this);
   base.RegisterEditorFactory(this.editorFactory);

   ```

8. Compile el programa y asegúrese de que no existan errores.

    Este paso registra el generador de editores en el subárbol del registro experimental para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si se le pide para invalidar el *resource.h* de archivos, haga clic en **Aceptar**.

9. Cree un archivo de ejemplo denominado *TextFile1.myext*.

10. Presione **F5** para abrir una instancia de la instancia experimental [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

11. En la instancia experimental [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en el **archivo** menú, elija **abierto** y, a continuación, haga clic en **archivo**.

12. Buscar **TextFile1.myext** y, a continuación, haga clic en **abierto**.

     Ahora debe cargar el archivo.

## <a name="robust-programming"></a>Programación sólida
 El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal controla una amplia gama de tipos de archivo basado en texto y colabora estrechamente con los servicios de lenguaje para proporcionar un amplio conjunto de características como el resaltado de sintaxis, coincidencia de llaves y finalización de palabras de IntelliSense y listas de finalización de miembros. Si está trabajando con archivos de texto, puede usar el editor principal junto con un servicio de lenguaje personalizado que admite los tipos de archivo específicos.

 Un VSPackage puede invocar el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal proporcionando un generador de editores. Este generador de editores se usa cuando se carga un archivo que está asociado con él. Si el archivo es parte de un proyecto, el editor básico se invoca automáticamente a menos que se reemplaza por el VSPackage. Sin embargo, si se carga el archivo fuera de un proyecto, el editor principal se debe invocar explícitamente por el VSPackage.

 Para obtener más información sobre el editor básico, consulte [dentro del editor de núcleo](../extensibility/inside-the-core-editor.md).

## <a name="see-also"></a>Vea también
- [Dentro del editor de núcleo](../extensibility/inside-the-core-editor.md)
- [Crear una instancia el editor básico mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)