---
title: Compatibilidad con fragmentos de código en un servicio de lenguaje heredado ( Legacy Language Service) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704908"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Compatibilidad con fragmentos de código en un servicio de lenguaje heredado
Un fragmento de código es un fragmento de código que se inserta en el archivo de origen. El propio fragmento de código es una plantilla basada en XML con un conjunto de campos. Estos campos se resaltan después de insertar el fragmento de código y pueden tener valores diferentes en función del contexto en el que se inserte el fragmento de código. Inmediatamente después de insertar el fragmento de código, el servicio de lenguaje puede dar formato al fragmento de código.

 El fragmento de código se inserta en un modo de edición especial que permite navegar por los campos del fragmento de código mediante la tecla TAB. Los campos pueden admitir menús desplegables de estilo IntelliSense. El usuario confirma el fragmento de código en el archivo de origen escribiendo la tecla ENTER o ESC. Para obtener más información sobre los fragmentos de código, consulte [Fragmentos](../../ide/code-snippets.md)de código .

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Tutorial: Implementación](../../extensibility/walkthrough-implementing-code-snippets.md)de fragmentos de código .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="managed-package-framework-support-for-code-snippets"></a>Compatibilidad con Managed Package Framework para fragmentos de código
 El marco de paquete administrado (MPF) admite la mayoría de la funcionalidad de fragmentos de código, desde leer la plantilla hasta insertar el fragmento de código y habilitar el modo de edición especial. El soporte se <xref:Microsoft.VisualStudio.Package.ExpansionProvider> administra a través de la clase.

 Cuando <xref:Microsoft.VisualStudio.Package.Source> se crea una <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> instancia de <xref:Microsoft.VisualStudio.Package.LanguageService> la clase, <xref:Microsoft.VisualStudio.Package.ExpansionProvider> se llama al <xref:Microsoft.VisualStudio.Package.LanguageService> método de la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> clase <xref:Microsoft.VisualStudio.Package.Source> para obtener un objeto (tenga en cuenta que la clase base siempre devuelve un nuevo objeto para cada objeto).

 El MPF no admite funciones de expansión. Una función de expansión es una función con nombre que está incrustada en una plantilla de fragmento de código y devuelve uno o varios valores que se colocarán en un campo. Los valores son devueltos por <xref:Microsoft.VisualStudio.Package.ExpansionFunction> el propio servicio de lenguaje a través de un objeto. El <xref:Microsoft.VisualStudio.Package.ExpansionFunction> servicio de lenguaje debe implementar el objeto para admitir funciones de expansión.

## <a name="providing-support-for-code-snippets"></a>Proporcionar soporte para fragmentos de código
 Para habilitar la compatibilidad con fragmentos de código, debe proporcionar o instalar los fragmentos de código y debe proporcionar los medios para que el usuario inserte esos fragmentos de código. Hay tres pasos para habilitar la compatibilidad con fragmentos de código:

1. Instalación de los archivos de fragmento de código.

2. Habilitar fragmentos de código para el servicio de lenguaje.

3. Invocar el <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto.

### <a name="installing-the-snippet-files"></a>Instalación de los archivos de fragmento de código
 Todos los fragmentos de código de un idioma se almacenan como plantillas en archivos XML, normalmente una plantilla de fragmento de código por archivo. Para obtener más información sobre el esquema XML utilizado para las plantillas de fragmento de código, vea Referencia de esquema de [fragmentos](../../ide/code-snippets-schema-reference.md)de código . Cada plantilla de fragmento de código se identifica con un identificador de idioma. Este identificador de idioma se especifica en `Language` el registro \<y se coloca en el atributo de la etiqueta Code> de la plantilla.

 Normalmente hay dos ubicaciones donde se almacenan los archivos de plantilla de fragmento de código: 1) donde se instaló el idioma y 2) en la carpeta del usuario. Estas ubicaciones se agregan al registro para que el Administrador de **fragmentos** de código de Visual Studio pueda encontrar los fragmentos de código. La carpeta del usuario es donde se almacenan los fragmentos creados por el usuario.

 El diseño típico de la carpeta para los archivos de plantilla de fragmento\\de código instalados tiene este aspecto: *[InstallRoot]*\\ *[TestLanguage]*?Snippets *[LCID]*.

 *[InstallRoot]* es la carpeta en la que está instalado el idioma.

 *[TestLanguage]* es el nombre de su idioma como nombre de carpeta.

 *[LCID]* es el ID de configuración regional. Así es como se almacenan las versiones localizadas de los fragmentos de código. Por ejemplo, el ID de configuración regional para inglés es 1033, por lo que *[LCID]* se reemplaza por 1033.

 Se debe proporcionar un archivo adicional y que es un archivo de índice, normalmente denominado SnippetsIndex.xml o ExpansionsIndex.xml (puede usar cualquier nombre de archivo válido que termine en .xml). Este archivo se almacena normalmente en la carpeta *[InstallRoot]*\\ *[TestLanguage]* y especifica la ubicación exacta de la carpeta de fragmentos de código, así como el identificador de idioma y el GUID del servicio de lenguaje que usa los fragmentos de código. La ruta exacta del archivo de índice se coloca en el registro como se describe más adelante en "Instalación de las entradas del registro". A continuación se muestra un ejemplo de un archivo SnippetsIndex.xml:

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

 La \<etiqueta Language> especifica el `Lang` identificador de idioma (el atributo) y el GUID del servicio de lenguaje.

 En este ejemplo se supone que ha instalado el servicio de lenguaje en la carpeta de instalación de Visual Studio. %LCID% se sustituye por el id de configuración regional actual del usuario. Se \<pueden agregar varias etiquetas de> SnippetDir, una para cada directorio y configuración regional diferentes. Además, una carpeta de fragmento de código puede contener subcarpetas, cada una de las cuales se identifica en el archivo de índice con la \<etiqueta de> SnippetSubDir que está incrustada en una \<etiqueta de> SnippetDir.

 Los usuarios también pueden crear sus propios fragmentos de código para su idioma. Normalmente se almacenan en la carpeta de configuración del usuario, por\\ejemplo *[TestDocs]*, fragmentos de código *[TestLanguage]*, donde *[TestDocs]* es la ubicación de la carpeta de configuración del usuario para Visual Studio.

 Los siguientes elementos de sustitución se \<pueden colocar en la ruta de acceso almacenada en la etiqueta de> DirPath en el archivo de índice.

|Elemento|Descripción|
|-------------|-----------------|
|%LCID%|Id. de configuración regional.|
|%InstallRoot%|Carpeta de instalación raíz para Visual Studio, por ejemplo, C:-Archivos de programa-Microsoft Visual Studio 8.|
|%ProjDir%|Carpeta que contiene el proyecto actual.|
|%ProjItem%|Carpeta que contiene el elemento de proyecto actual.|
|%TestDocs%|Carpeta en la carpeta de configuración del usuario, por\\ejemplo, C:-Documents and Settings *[nombre de usuario]*.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Habilitación de fragmentos de código para su servicio de lenguaje
 Puede habilitar fragmentos de código para <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> el servicio de lenguaje agregando el atributo al VSPackage (consulte Registrar un servicio de [lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obtener más información). Los <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parámetros y son opcionales, pero debe incluir el `SearchPaths` parámetro con nombre para informar al Administrador de **fragmentos** de código de la ubicación de los fragmentos de código.

 A continuación se muestra un ejemplo de cómo utilizar este atributo:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Llamar al proveedor de expansión
 El servicio de lenguaje controla la inserción de cualquier fragmento de código, así como la forma en que se invoca la inserción.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Llamar al proveedor de expansión para fragmentos de código
 Hay dos maneras de invocar el proveedor de expansión: mediante un comando de menú o mediante un acceso directo de una lista de finalización.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Insertar un fragmento de código mediante un comando de menú
 Para utilizar un comando de menú para mostrar el explorador <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> de fragmentos de código, agregue un comando de menú y, a continuación, llame al método en la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interfaz en respuesta a ese comando de menú.

1. Agregue un comando y un botón al archivo .vsct. Puede encontrar instrucciones para hacerlo en Creación de [una extensión con un comando](../../extensibility/creating-an-extension-with-a-menu-command.md)de menú .

2. Derive una clase <xref:Microsoft.VisualStudio.Package.ViewFilter> de la <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> clase e invalide el método para indicar compatibilidad con el nuevo comando de menú. Este ejemplo siempre habilita el comando menu.

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

3. Invalide <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> el <xref:Microsoft.VisualStudio.Package.ViewFilter> método de <xref:Microsoft.VisualStudio.Package.ExpansionProvider> la clase <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> para obtener el objeto y llame al método en ese objeto.

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

     Visual Studio llama <xref:Microsoft.VisualStudio.Package.ExpansionProvider> a los siguientes métodos de la clase en el orden especificado durante el proceso de inserción del fragmento de código:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Después <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> de llamar al método, se <xref:Microsoft.VisualStudio.Package.ExpansionProvider> ha insertado el fragmento de código y el objeto está en un modo de edición especial utilizado para modificar un fragmento de código que se acaba de insertar.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Insertar un fragmento de código mediante un acceso directo
 La implementación de un acceso directo desde una lista de finalización es mucho más implicada que la implementación de un comando de menú. Primero debe agregar accesos directos de fragmento de código a la lista de finalización de palabras de IntelliSense. A continuación, debe detectar cuándo se ha insertado un nombre de acceso directo de fragmento de código como resultado de la finalización. Por último, debe obtener el título y la ruta de <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> acceso <xref:Microsoft.VisualStudio.Package.ExpansionProvider> del fragmento de código mediante el nombre de acceso directo y pasar esa información al método en el método.

 Para agregar accesos directos de fragmento de <xref:Microsoft.VisualStudio.Package.Declarations> código <xref:Microsoft.VisualStudio.Package.AuthoringScope> a la lista de finalización de palabras, agréguelos al objeto de la clase. Debe asegurarse de que puede identificar el acceso directo como un nombre de fragmento de código. Para obtener un ejemplo, vea [Tutorial: Obtener una lista de fragmentos de código instalados (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Puede detectar la inserción del <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> acceso directo <xref:Microsoft.VisualStudio.Package.Declarations> del fragmento de código en el método de la clase. Dado que el nombre del fragmento de código ya se ha insertado en el archivo de origen, debe quitarse cuando se inserta la expansión. El <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método toma un intervalo que describe el punto de inserción del fragmento de código; si el intervalo incluye el nombre completo del fragmento de código en el archivo de origen, ese nombre se reemplaza por el fragmento de código.

 Esta es una <xref:Microsoft.VisualStudio.Package.Declarations> versión de una clase que controla la inserción de fragmentos de código dado un nombre de acceso directo. Otros métodos <xref:Microsoft.VisualStudio.Package.Declarations> de la clase se han omitido para mayor claridad. Tenga en cuenta que el <xref:Microsoft.VisualStudio.Package.LanguageService> constructor de esta clase toma un objeto. Esto se puede pasar desde <xref:Microsoft.VisualStudio.Package.AuthoringScope> la versión del objeto <xref:Microsoft.VisualStudio.Package.AuthoringScope> (por ejemplo, la implementación de la clase podría tomar el <xref:Microsoft.VisualStudio.Package.LanguageService> objeto en su constructor y pasar ese objeto al constructor de `TestDeclarations` clase).

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

 Cuando el servicio de lenguaje obtiene el <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> nombre de acceso directo, llama al método para obtener el nombre de archivo y el título del fragmento de código. A continuación, el <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> servicio <xref:Microsoft.VisualStudio.Package.ExpansionProvider> de lenguaje llama al método de la clase para insertar el fragmento de código. Visual Studio llama a los métodos siguientes <xref:Microsoft.VisualStudio.Package.ExpansionProvider> en el orden especificado de la clase durante el proceso de inserción del fragmento de código:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Para obtener más información sobre cómo obtener una lista de fragmentos de código instalados para el servicio de lenguaje, vea [Tutorial: Obtener una lista de fragmentos de código instalados (implementación heredada).](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

## <a name="implementing-the-expansionfunction-class"></a>Implementación de la clase ExpansionFunction
 Una función de expansión es una función con nombre que está incrustada en una plantilla de fragmento de código y devuelve uno o varios valores que se colocarán en un campo. Para admitir funciones de expansión en el servicio <xref:Microsoft.VisualStudio.Package.ExpansionFunction> de lenguaje, <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> debe derivar una clase de la clase e implementar el método. A continuación, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> debe invalidar <xref:Microsoft.VisualStudio.Package.LanguageService> el método de la clase para <xref:Microsoft.VisualStudio.Package.ExpansionFunction> devolver una nueva instancia de la versión de la clase para cada función de expansión que admita. Si admite una lista de valores posibles de una <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> función <xref:Microsoft.VisualStudio.Package.ExpansionFunction> de expansión, también debe invalidar el método de la clase para devolver una lista de esos valores.

 Una función de expansión que toma argumentos o necesita tener acceso a otros campos no debe asociarse a un campo editable, ya que es posible que el proveedor de expansión no se inicialice completamente en el momento en que se llama a la función de expansión. Como resultado, la función de expansión no puede obtener el valor de sus argumentos ni de ningún otro campo.

### <a name="example"></a>Ejemplo
 Este es un ejemplo de cómo `GetName` se puede implementar una función de expansión simple llamada. Esta función de expansión anexa un número a un nombre de clase base cada vez que se crea una instancia de la función de expansión (que corresponde a cada vez que se inserta el fragmento de código asociado).

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
- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)
- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Fragmentos de código](../../ide/code-snippets.md)
- [Tutorial: Obtención de una lista de fragmentos de código instalados (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
