---
title: 'Tutorial: crear un editor principal y registrar un tipo de archivo de editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14296aa335ba6710d4d9eac8e5338af7463c0aac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687635"
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Tutorial: Crear un editor principal y registrar un tipo de archivo del editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo crear un VSPackage que inicia el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal cuando se carga un archivo con la extensión de nombre de archivo. myext.  
  
## <a name="prerequisites"></a>Prerrequisitos  
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Ubicaciones de la plantilla de proyecto de paquete de Visual Studio  
 La plantilla de proyecto del paquete de Visual Studio puede encontrarse en tres ubicaciones diferentes en el cuadro de diálogo **Nuevo proyecto** :  
  
1. En Extensibilidad de Visual Basic. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2. En Extensibilidad de C#. El lenguaje predeterminado del proyecto es C#.  
  
3. En otro tipos de extensibilidad del proyecto. El lenguaje predeterminado del proyecto es C++.  
  
### <a name="to-create-the-vspackage"></a>Para crear el VSPackage  
  
- Inicie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y cree un [!INCLUDE[csprcs](../includes/csprcs-md.md)] VSPackage denominado `MyPackage` , como se describe en [Tutorial: crear un VSPackage de comandos de menú](https://msdn.microsoft.com/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Para agregar el generador de editores  
  
1. Haga clic con el botón secundario en el proyecto de **paquete** , seleccione **Agregar** y, a continuación, haga clic en **clase**.  
  
2. En el cuadro de diálogo **Agregar nuevo elemento** , asegúrese de que la plantilla de **clase** está seleccionada, escriba `EditorFactory.cs` para el nombre y, a continuación, haga clic en **Agregar** para agregar la clase al proyecto.  
  
     El archivo EditorFactory.cs debe abrirse automáticamente.  
  
3. Haga referencia a los siguientes ensamblados desde el código.  
  
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
  
4. Agregue un GUID a la `EditorFactory` clase agregando el `Guid` atributo inmediatamente antes de la declaración de clase.  
  
     Puede generar un nuevo GUID mediante el guidgen.exe programa en el símbolo del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sistema o haciendo clic en **crear GUID** en el menú **herramientas** . El GUID que se usa aquí es solo un ejemplo; no lo use en el proyecto.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5. En la definición de clase, agregue dos variables privadas que contengan el paquete primario y un proveedor de servicios.  
  
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
  
6. Agregue un constructor de clase pública que toma un parámetro de tipo <xref:Microsoft.VisualStudio.Shell.Package> :  
  
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
  
7. Modifique la `EditorFactory` declaración de clase para que se derive de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8. Haga clic con el botón secundario <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> , haga clic en **implementar interfaz**y, a continuación, haga clic en **implementar interfaz explícitamente**.  
  
     Esto agrega los cuatro métodos que se deben implementar en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz.  
  
9. Reemplace el contenido del método `IVsEditorFactory.Close` por el siguiente código.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Reemplace el contenido de `IVsEditorFactory.SetSite` por el código siguiente.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Reemplace el contenido del método `IVsEditorFactory.MapLogicalView` por el siguiente código.  
  
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
  
12. Reemplace el contenido del método `IVsEditorFactory.CreateEditorInstance` por el siguiente código.  
  
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
  
13. Compile el proyecto y asegúrese de que no hay errores.  
  
### <a name="to-register-the-editor-factory"></a>Para registrar el generador de editores  
  
1. En **Explorador de soluciones**, haga doble clic en el archivo resources. resx para abrirlo en la tabla de cadenas, en la que se selecciona la entrada **cadena1** .  
  
2. Cambie el nombre del identificador a `IDS_EDITORNAME` y el texto a editor de **paquetes.** Esta cadena aparecerá como el nombre del editor.  
  
3. Abra el archivo VSPackage. resx y agregue una nueva cadena, establezca el nombre en **101** y el valor en `IDS_EDITORNAME` . Esto proporciona el paquete con un identificador de recurso para tener acceso a la cadena que acaba de crear.  
  
    > [!NOTE]
    > Si el archivo VSPackage. resx contiene otra cadena que `name` establece el atributo en **101**, sustituya otro valor numérico único, aquí y en los pasos siguientes.  
  
4. En **Explorador de soluciones**, abra el archivo MyPackagePackage.cs.  
  
     Este es el archivo de paquete principal.  
  
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
  
     El <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> atributo asocia la extensión de archivo. myext con el generador de editores para que cada vez que se cargue un archivo que tenga esa extensión, se invoque el generador de editores.  
  
6. Agregue una variable privada a la `MyPackage` clase, justo antes del constructor, y asígnele el tipo `EditorFactory` .  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7. Busque el `Initialize` método (es posible que tenga que abrir la `Package Members` región oculta) y agregue el código siguiente después de la llamada a `base.Initialize()` .  
  
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
  
     Este paso registra el generador de editores en el subárbol del registro experimental para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Si se le pide que invalide el archivo resource. h, haga clic en **Aceptar**.  
  
9. Cree un archivo de ejemplo denominado TextFile1. myext.  
  
10. Presione **F5** para abrir una instancia del experimental [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
11. En experimental [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , en el menú **archivo** , elija **abrir** y, a continuación, haga clic en **archivo**.  
  
12. Busque TextFile1. myext y, a continuación, haga clic en **abrir**.  
  
     Ahora debe cargarse el archivo.  
  
## <a name="robust-programming"></a>Programación sólida  
 El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal administra una amplia gama de tipos de archivos basados en texto y funciona en estrecha colaboración con los servicios de lenguaje para proporcionar un conjunto completo de características como el resaltado de sintaxis, la coincidencia de llaves y las listas de finalización de palabras de IntelliSense y de finalización de miembros. Si está trabajando con archivos basados en texto, puede usar el editor básico junto con un servicio de lenguaje personalizado que admita sus tipos de archivo específicos.  
  
 Un VSPackage puede invocar el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal proporcionando un generador de editores. Este generador de editores se usa cada vez que se carga un archivo que está asociado a él. Si el archivo forma parte de un proyecto, el editor principal se invoca automáticamente a menos que el VSPackage lo invalide. Sin embargo, si el archivo se carga fuera de un proyecto, el VSPackage debe invocarlo explícitamente.  
  
 Para obtener más información sobre el editor básico, vea [dentro del editor principal](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Consulte también  
 [Dentro del editor principal](../extensibility/inside-the-core-editor.md)   
 [Creación de instancias del editor principal mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
