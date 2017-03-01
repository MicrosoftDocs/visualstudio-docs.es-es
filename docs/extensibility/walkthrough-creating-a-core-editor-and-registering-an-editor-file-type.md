---
title: "Crear un Editor de núcleo y registrar un tipo de archivo del Editor | Documentos de Microsoft&quot;"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 7bde276b0d53793f57266c13c5ccf63583f7aacf
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Tutorial: Crear un Editor de núcleo y registrar un tipo de archivo del Editor
Este tutorial muestra cómo crear un VSPackage que se inicia el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de núcleo cuando un archivo que tiene la extensión de nombre de archivo .myext se carga.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el Visual Studio SDK. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Ubicaciones de la plantilla de proyecto de paquete de Visual Studio  
 La plantilla de proyecto del paquete de Visual Studio puede encontrarse en tres ubicaciones diferentes en el cuadro de diálogo **Nuevo proyecto** :  
  
1.  En Extensibilidad de Visual Basic. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2.  En Extensibilidad de C#. El lenguaje predeterminado del proyecto es C#.  
  
3.  En otro tipos de extensibilidad del proyecto. El lenguaje predeterminado del proyecto es C++.  
  
### <a name="to-create-the-vspackage"></a>Para crear el paquete VSPackage  
  
-   Iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y crear una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage llamado `MyPackage`, como se describe en [Tutorial: crear un VSPackage del comando de menú](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Para agregar el generador del editor  
  
1.  Haga clic en el **MyPackage** del proyecto, seleccione **agregar** y, a continuación, haga clic en **clase**.  
  
2.  En el **Agregar nuevo elemento** diálogo cuadro, asegúrese de que el **clase** se selecciona la plantilla, tipo `EditorFactory.cs` para el nombre y, a continuación, haga clic en **agregar** para agregar la clase al proyecto.  
  
     El archivo EditorFactory.cs debe abrirse automáticamente.  
  
3.  Hacer referencia a los siguientes ensamblados desde el código.  
  
    ```vb#  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```c#  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4.  Agregar un GUID para el `EditorFactory` clase agregando el `Guid` atributo inmediatamente antes de la declaración de clase.  
  
     Puede generar un nuevo GUID mediante el programa guidgen.exe en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comando símbolo del sistema o haciendo clic en **crear GUID** en el **herramientas** menú. El GUID que se usa aquí es sólo un ejemplo; no lo utilice en su proyecto.  
  
    ```vb#  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```c#  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  En la definición de clase, agregue dos variables privadas para que contenga el paquete primario y un proveedor de servicios.  
  
    ```vb#  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```c#  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6.  Agregue un constructor de clase pública que toma un parámetro de tipo <xref:Microsoft.VisualStudio.Shell.Package>:</xref:Microsoft.VisualStudio.Shell.Package>  
  
    ```vb#  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```c#  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7.  Modificar el `EditorFactory` declaración pueden derivar de la clase del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>interfaz.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
    ```vb#  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```c#  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  Haga clic en <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, haga clic en **Implementar interfaz**y, a continuación, haga clic en **Implementar interfaz explícitamente**.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
     Esto agrega los cuatro métodos que deben implementarse en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>interfaz.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
9. Reemplace el contenido del método `IVsEditorFactory.Close` con el código siguiente.  
  
    ```vb#  
    Return VSConstants.S_OK  
    ```  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
10. Reemplace el contenido de la `IVsEditorFactory.SetSite` con el código siguiente.  
  
    ```vb#  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```c#  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Reemplace el contenido del método `IVsEditorFactory.MapLogicalView` con el código siguiente.  
  
    ```vb#  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```c#  
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
  
    ```vb#  
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
  
    ```c#  
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
  
13. Compile el proyecto y asegúrese de que no existen errores.  
  
### <a name="to-register-the-editor-factory"></a>Para registrar el generador del editor  
  
1.  En **el Explorador de soluciones**, haga doble clic en el archivo Resources.resx para abrirlo en la tabla de cadenas, en el que la entrada **String1 es** seleccionado.  
  
2.  Cambiar el nombre del identificador para `IDS_EDITORNAME` y el texto **MyPackage Editor.** Esta cadena aparecerá como el nombre de su editor.  
  
3.  Abra el archivo VSPackage.resx y agregue una nueva cadena, establezca el nombre en **101** y el valor en `IDS_EDITORNAME`. Esto proporciona el paquete con un identificador de recurso para tener acceso a la cadena que acaba de crear.  
  
    > [!NOTE]
    >  Si el archivo VSPackage.resx contiene otra cadena que el `name` atributo establecido en **101**, sustituir otro valor único, numeric, aquí y en los pasos siguientes.  
  
4.  En **el Explorador de soluciones**, abra el archivo MyPackagePackage.cs.  
  
     Este es el archivo de paquete principal.  
  
5.  Agregue los siguientes atributos de usuario justo antes del `Guid` atributo.  
  
    ```vb#  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```c#  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     El <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>atributo asocia la extensión de archivo .myext con el generador de editores para que cada vez que un archivo que tiene que cargar extensión, se invoca el generador de editores.</xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>  
  
6.  Agregue una variable privada a la `MyPackage` clase justo antes del constructor y asígnele el tipo `EditorFactory`.  
  
    ```vb#  
    Private editorFactory As EditorFactory  
    ```  
  
    ```c#  
    private EditorFactory editorFactory;  
    ```  
  
7.  Buscar el `Initialize` (método) (es posible que deba abrir el `Package Members` región oculta) y agregue el código siguiente después de llamar a `base.Initialize()`.  
  
    ```vb#  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```c#  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8.  Compile el programa y asegúrese de que no existan errores.  
  
     Este paso registra el generador del editor en el subárbol del registro experimental para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si se le pide que reemplace el archivo resource.h, haga clic en **Aceptar**.  
  
9. Crear un archivo de ejemplo denominado TextFile1.myext.  
  
10. Presione **F5** para abrir una instancia de la instancia experimental [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. En la instancia experimental [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en la **archivo** menú, seleccione **abiertos** y, a continuación, haga clic en **archivo**.  
  
12. Buscar TextFile1.myext y, a continuación, haga clic en **abiertos**.  
  
     Ahora se debe cargar el archivo.  
  
## <a name="robust-programming"></a>Programación sólida  
 El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal controla una amplia gama de tipos de archivo basado en texto y colabora estrechamente con los servicios de lenguaje que proporcionan un amplio conjunto de características tales como resaltado de sintaxis, coincidencia de llaves y las listas de finalización de palabras y la finalización de miembro de IntelliSense. Si trabaja con archivos de texto, a continuación, puede utilizar el editor principal junto con un servicio de lenguaje personalizado que admite los tipos de archivo específicos.  
  
 Puede invocar un VSPackage la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal proporcionando un generador del editor. Este generador del editor se usa cuando se carga un archivo que está asociado a él. Si el archivo forma parte de un proyecto, el editor principal se invoca automáticamente a menos que se reemplaza por el VSPackage. Sin embargo, si se carga el archivo fuera de un proyecto, a continuación, el editor principal debe invocar explícitamente el VSPackage.  
  
 Para obtener más información acerca del editor de núcleo, consulte [en el Editor principal](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Vea también  
 [Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Crear una instancia del Editor principal mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
