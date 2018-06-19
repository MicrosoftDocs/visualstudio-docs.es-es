---
title: Compatibilidad con fragmentos de código en un servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb62481b9ba2c42ed067275480ba137b151a483b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135687"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Compatibilidad con fragmentos de código en un servicio de lenguaje heredado
Un fragmento de código es un fragmento de código que se inserta en el archivo de origen. El fragmento de código es una plantilla basada en XML con un conjunto de campos. Estos campos se resaltan después de que el fragmento de código se inserta y puede tener diferentes valores en función del contexto en el que se inserta el fragmento de código. Inmediatamente después de inserta el fragmento de código, el servicio de lenguaje puede dar formato el fragmento de código.  
  
 El fragmento de código se inserta en un modo de edición especial que permite a los campos del fragmento de código para navegar mediante el uso de la tecla TAB. Los campos pueden admitir los menús desplegables de estilo de IntelliSense. El usuario confirma el fragmento de código en el archivo de origen escribiendo el ENTRAR o la tecla ESC. Para más información acerca de los fragmentos, vea [fragmentos de código](../../ide/code-snippets.md).  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información, consulte [Tutorial: implementar fragmentos de código](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Compatibilidad con marco de trabajo de paquete para fragmentos de código administrado  
 Managed package framework (MPF) es compatible con la mayoría de las funciones de fragmento de código, de la lectura de la plantilla para insertar el fragmento de código y habilitar especial del modo de edición. Soporte técnico se administra a través de la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> clase.  
  
 Cuando el <xref:Microsoft.VisualStudio.Package.Source> se crea una instancia de clase, el <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase se denomina para obtener un <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto (tenga en cuenta que la base de <xref:Microsoft.VisualStudio.Package.LanguageService> clase siempre devuelve un nuevo <xref:Microsoft.VisualStudio.Package.ExpansionProvider> para cada objeto <xref:Microsoft.VisualStudio.Package.Source> objeto).  
  
 MPF no admite funciones de expansión. Una función de expansión es una función con nombre que se incrusta en una plantilla del fragmento y devuelve uno o más valores que se colocarán en un campo. Los valores se devuelven por el lenguaje propio a través del servicio un <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objeto. La <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objeto debe ser implementado por el servicio de lenguaje para admitir funciones de expansión.  
  
## <a name="providing-support-for-code-snippets"></a>Proporciona compatibilidad con fragmentos de código  
 Para habilitar la compatibilidad con fragmentos de código, debe proporcionar o instalar los fragmentos de código y debe proporcionar los medios para el usuario insertar los fragmentos de código. Hay tres pasos para habilitar la compatibilidad para fragmentos de código:  
  
1.  Instalar los archivos de fragmento de código.  
  
2.  Habilitación de fragmentos de código para el servicio de lenguaje.  
  
3.  Invocar la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto.  
  
### <a name="installing-the-snippet-files"></a>Instalar los archivos de fragmento de código  
 Todos los fragmentos de código para un idioma se almacenan como plantillas en archivos XML, normalmente una plantilla del fragmento por archivo. Para obtener más información sobre el esquema XML utilizada para las plantillas de fragmento de código, vea [referencia de esquema de fragmentos de código](../../ide/code-snippets-schema-reference.md). Cada plantilla de fragmento de código se identifica con un identificador de idioma. Este idioma identificador se especifica en el registro y se coloca en el `Language` atributo de la \<código > etiqueta en la plantilla.  
  
 Normalmente, hay dos ubicaciones donde se almacenan los archivos de plantilla de fragmento de código: 1) donde se instaló el idioma y (2) en la carpeta del usuario. Estas ubicaciones se agregan al registro hasta que el de Visual Studio **Administrador de fragmentos de código** puede encontrar los fragmentos de código. La carpeta del usuario es donde se almacenan los fragmentos de código creados por el usuario.  
  
 El diseño de carpeta habitual para los archivos de plantilla instalada de fragmento de código tiene el siguiente aspecto: *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets.  
  
 *[InstallRoot]*  es la carpeta que el idioma se instala en.  
  
 *[TestLanguage]*  es el nombre de su idioma como un nombre de carpeta.  
  
 *[LCID]*  es el identificador de configuración regional. Se trata de las versiones localizadas de forma de los fragmentos de código se almacenan. Por ejemplo, el identificador de configuración regional para inglés es 1033, por lo que *[LCID]* se sustituye por 1033.  
  
 Debe proporcionarse un archivo adicional y que es un archivo de índice, normalmente denominado SnippetsIndex.xml o ExpansionsIndex.xml (puede utilizar cualquier nombre de archivo válido termina en .xml). Este archivo normalmente se almacena en la *[InstallRoot]*\\ *[TestLanguage]* carpeta y especifica la ubicación exacta de la carpeta de fragmentos de código así como el identificador de idioma y el GUID del lenguaje servicio que utiliza los fragmentos de código. La ruta de acceso exacta del archivo de índice se coloca en el registro como se describe más adelante en "Instalar las entradas del registro". Este es un ejemplo de un archivo de SnippetsIndex.xml:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 El \<idioma > etiqueta Especifica el identificador de idioma (el `Lang` atributo) y el GUID del servicio de lenguaje.  
  
 En este ejemplo se da por supuesto que ha instalado el servicio de lenguaje en la carpeta de instalación de Visual Studio. % LCID % se sustituirá con el identificador de configuración regional actual. del usuario Varios \<SnippetDir > etiquetas se pueden agregar, uno para cada directorio diferente y la configuración regional. Además, una carpeta de fragmento de código puede contener subcarpetas, cada uno de los cuales se identifica en el archivo de índice con la \<SnippetSubDir > etiqueta que se incrusta en un \<SnippetDir > etiqueta.  
  
 Los usuarios también pueden crear sus propios fragmentos de código para su idioma. Normalmente se almacenan en la carpeta de configuración del usuario, por ejemplo *[TestDocs]* \Code fragmentos\\ *[TestLanguage]* \Test fragmentos de código, donde *[TestDocs]* es la ubicación de carpeta de configuración del usuario de Visual Studio.  
  
 Los siguientes elementos de sustitución pueden colocarse en la ruta de acceso almacenada en el \<DirPath > etiqueta en el archivo de índice.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|% LCID %|Identificador de configuración regional.|  
|% InstallRoot %|Carpeta de instalación raíz para Visual Studio, por ejemplo, C:\Program Files\Microsoft Visual Studio 8.|  
|% ProjDir %|Carpeta que contiene el proyecto actual.|  
|% ProjItem %|Carpeta que contiene el elemento de proyecto actual.|  
|% TestDocs %|Carpeta en la carpeta de configuración del usuario, por ejemplo, C:\Documents and Settings\\ *[username]* \My Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>Habilitación de fragmentos de código para el servicio de lenguaje  
 Puede habilitar los fragmentos de código para el servicio de lenguaje mediante la adición de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> de atributo para el VSPackage (vea [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obtener más información). El <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> y <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parámetros son opcionales, pero debe incluir el `SearchPaths` con el nombre de parámetro con el fin de informar a la **Administrador de fragmentos de código** de la ubicación de los fragmentos de código.  
  
 El siguiente es un ejemplo de cómo utilizar este atributo:  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### <a name="calling-the-expansion-provider"></a>Llamando al proveedor de expansión  
 El servicio de lenguaje controla la inserción de cualquier fragmento de código, así como la forma en que se invoca la inserción.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Llamando al proveedor de expansión para fragmentos de código  
 Hay dos maneras de invocar el proveedor de expansión: mediante un comando de menú o mediante un acceso directo de una lista de finalización.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Insertar un fragmento de código mediante un comando de menú  
 Para usar un comando de menú para mostrar el Explorador de fragmento de código, agregue un comando de menú y, a continuación, llame a la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> método en el <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interfaz en respuesta a ese comando de menú.  
  
1.  Agregue un comando y un botón al archivo .vsct. Encontrará instrucciones para hacer esto en [crear una extensión con un comando de menú](../../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Derivar una clase de la <xref:Microsoft.VisualStudio.Package.ViewFilter> clase e invalidar el <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> método para indicar la compatibilidad para el nuevo comando de menú. Este ejemplo siempre habilita el comando de menú.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3.  Invalidar el <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> método en el <xref:Microsoft.VisualStudio.Package.ViewFilter> clase para obtener la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto y llame al método el <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> método en ese objeto.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     Los siguientes métodos de la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> clase se denomina Visual Studio en el orden especificado durante el proceso de insertar el fragmento de código:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Después de la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> se llama al método, se ha insertado el fragmento de código y la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto se encuentra en un modo de edición especial utilizado para modificar un fragmento de código que acaba de insertar.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Insertar un fragmento de código mediante un acceso directo  
 Implementación de un acceso directo de una lista de finalización es mucho más complejo que implementar un comando de menú. En primer lugar debe agregar accesos directos de fragmento de código a la lista de finalización de palabras de IntelliSense. A continuación, debe detectar cuando se ha insertado un nombre de método abreviado de fragmento de código como resultado de la finalización. Por último, debe obtener el título del fragmento de código y la ruta de acceso con el nombre de método abreviado y pasar esa información a la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método en el <xref:Microsoft.VisualStudio.Package.ExpansionProvider> método.  
  
 Para agregar accesos directos de fragmento de código a la lista de finalización de palabras, agregarlos a la <xref:Microsoft.VisualStudio.Package.Declarations> objeto en su <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase. Debe asegurarse de que puede identificar el acceso directo como un nombre de fragmento de código. Para obtener un ejemplo, vea [Tutorial: obtener una lista de instalado fragmentos de código (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Puede detectar la inserción del acceso directo de fragmento de código en el <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> método de la <xref:Microsoft.VisualStudio.Package.Declarations> clase. Dado que el nombre del fragmento ya se ha insertado en el archivo de origen, debe quitarse cuando se inserta la expansión. El <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método toma un intervalo que describe el punto de inserción para el fragmento de código; si el intervalo incluye el nombre del fragmento completo en el archivo de origen, ese nombre se sustituye por el fragmento de código.  
  
 Esta es una versión de un <xref:Microsoft.VisualStudio.Package.Declarations> clase que controla la inserción de fragmento de código le proporcionado un nombre de método abreviado. Otros métodos en el <xref:Microsoft.VisualStudio.Package.Declarations> clase se han omitido para mayor claridad. Tenga en cuenta que el constructor de esta clase toma un <xref:Microsoft.VisualStudio.Package.LanguageService> objeto. Esto se puede pasar en desde su versión de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto (por ejemplo, la implementación de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase puede tardar la <xref:Microsoft.VisualStudio.Package.LanguageService> objeto en su constructor y pasar ese objeto en su `TestDeclarations` constructor de clase).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 Cuando el servicio de lenguaje Obtiene el nombre de método abreviado, se llama a la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> método para obtener el título de fragmento de nombre de archivo y el código. El servicio de lenguaje, a continuación, llama a la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método en la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> clase para insertar el fragmento de código. Se llaman a los métodos siguientes por Visual Studio en el orden especificado en el <xref:Microsoft.VisualStudio.Package.ExpansionProvider> clase durante el proceso de insertar el fragmento de código:  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 Para obtener más información sobre cómo obtener una lista de fragmentos de código instalados para el servicio de lenguaje, vea [Tutorial: obtener una lista de instalado fragmentos de código (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Implementación de la clase ExpansionFunction  
 Una función de expansión es una función con nombre que se incrusta en una plantilla del fragmento y devuelve uno o más valores que se colocarán en un campo. Con el fin de admitir las funciones de expansión en el servicio de lenguaje, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> clase e implemente el <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> método. Debe reemplazar el <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase para devolver una instancia nueva de la versión de la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> clase para cada función de expansión se admiten. Si admite una lista de valores posibles de una función de expansión, también debe invalidar el <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> método en la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> clase para devolver una lista de esos valores.  
  
 Una función de expansión que toma argumentos o necesita tener acceso a otros campos no debería estar asociada con un campo editable, como el proveedor de expansión podría no estar inicializado totalmente en el momento en que se llama a la función de expansión. Como resultado, la función de expansión no es capaz de obtener el valor de sus argumentos ni ningún otro campo.  
  
### <a name="example"></a>Ejemplo  
 Este es un ejemplo de cómo llama a una función de expansión simple `GetName` podría implementarse. Esta función de expansión anexa un número a un nombre de clase base cada vez que se crea una instancia de la función de expansión (que corresponde a cada vez que el fragmento de código asociado se inserta).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Fragmentos de código](../../ide/code-snippets.md)   
 [Tutorial: obtención de una lista de fragmentos de código instalados (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)