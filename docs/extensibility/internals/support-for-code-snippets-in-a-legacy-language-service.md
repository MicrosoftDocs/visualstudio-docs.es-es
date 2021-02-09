---
title: Compatibilidad con fragmentos de código en un servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre cómo un servicio de lenguaje heredado admite fragmentos de código. Un fragmento de código es un fragmento de código que se inserta en el archivo de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 16f0df8a21621b93655935b3cfa27a4b62df63ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888152"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Compatibilidad con fragmentos de código en un servicio de lenguaje heredado
Un fragmento de código es un fragmento de código que se inserta en el archivo de código fuente. El propio fragmento es una plantilla basada en XML con un conjunto de campos. Estos campos se resaltan después de insertar el fragmento de código y pueden tener valores diferentes en función del contexto en el que se inserta el fragmento de código. Inmediatamente después de insertar el fragmento de código, el servicio de lenguaje puede dar formato al fragmento de código.

 El fragmento de código se inserta en un modo de edición especial que permite navegar por los campos del fragmento de código mediante la tecla TAB. Los campos pueden admitir los menús desplegables de estilo IntelliSense. El usuario confirma el fragmento de código en el archivo de origen escribiendo la tecla entrar o ESC. Para obtener más información acerca de los fragmentos de [código](../../ide/code-snippets.md), vea fragmentos de código.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información, vea [Tutorial: implementar fragmentos de código](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="managed-package-framework-support-for-code-snippets"></a>Compatibilidad con Managed Package Framework para fragmentos de código
 Managed Package Framework (MPF) admite la mayoría de las funciones de los fragmentos de código, desde la lectura de la plantilla hasta la inserción del fragmento de código y la habilitación del modo de edición especial. La compatibilidad se administra a través de la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> clase.

 Cuando <xref:Microsoft.VisualStudio.Package.Source> se crea una instancia de la clase, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> se llama al método de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase para obtener un <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto (tenga en cuenta que la <xref:Microsoft.VisualStudio.Package.LanguageService> clase base siempre devuelve un nuevo <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto para cada <xref:Microsoft.VisualStudio.Package.Source> objeto).

 MPF no admite funciones de expansión. Una función de expansión es una función con nombre que se incrusta en una plantilla de fragmento de código y devuelve uno o más valores que se van a colocar en un campo. El propio servicio de lenguaje devuelve los valores a través de un <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objeto. El <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objeto debe ser implementado por el servicio de lenguaje para admitir las funciones de expansión.

## <a name="providing-support-for-code-snippets"></a>Proporcionar compatibilidad con fragmentos de código
 Para habilitar la compatibilidad con fragmentos de código, debe proporcionar o instalar los fragmentos de código y debe proporcionar los medios para que el usuario los inserte. Hay tres pasos para habilitar la compatibilidad con los fragmentos de código:

1. Instalar los archivos de fragmento de código.

2. Habilitar fragmentos de código para el servicio de lenguaje.

3. Invocar el <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto.

### <a name="installing-the-snippet-files"></a>Instalar los archivos de fragmento de código
 Todos los fragmentos de código para un idioma se almacenan como plantillas en archivos XML, normalmente una plantilla de fragmento de código por cada archivo. Para obtener más información sobre el esquema XML utilizado para las plantillas de fragmentos de código, vea [referencia de esquemas de fragmentos de código](../../ide/code-snippets-schema-reference.md). Cada plantilla de fragmento de código se identifica con un identificador de idioma. Este identificador de idioma se especifica en el registro y se coloca en el `Language` atributo de la \<Code> etiqueta en la plantilla.

 Normalmente hay dos ubicaciones en las que se almacenan los archivos de plantilla de fragmento de código: 1) donde se instaló el idioma y 2) en la carpeta del usuario. Estas ubicaciones se agregan al registro para que el administrador de **fragmentos de código** de Visual Studio pueda encontrar los fragmentos de código. La carpeta del usuario es donde se almacenan los fragmentos de código creados por el usuario.

 El diseño de carpeta típico para los archivos de plantilla de fragmento de código instalado tiene el siguiente aspecto: *[InstallRoot]* \\ *[TestLanguage]* \Snippets \\ *[LCID]* \Snippets.

 *[InstallRoot]* es la carpeta en la que está instalado el idioma.

 *[TestLanguage]* es el nombre del idioma como un nombre de carpeta.

 *[LCID]* es el identificador de configuración regional. Esta es la forma en que se almacenan las versiones localizadas de los fragmentos de código. Por ejemplo, el ID. de configuración regional para inglés es 1033, por lo que *[LCID]* se sustituye por 1033.

 Se debe proporcionar un archivo adicional, que es un archivo de índice, normalmente denominado SnippetsIndex.xml o ExpansionsIndex.xml (puede usar cualquier nombre de archivo válido que termine en. xml). Normalmente, este archivo se almacena en la carpeta *[InstallRoot]* \\ *[TestLanguage]* y especifica la ubicación exacta de la carpeta de fragmentos de código, así como el identificador de idioma y el GUID del servicio de lenguaje que usa los fragmentos de código. La ruta de acceso exacta del archivo de índice se coloca en el registro como se describe más adelante en "instalación de las entradas del registro". A continuación se muestra un ejemplo de un archivo SnippetsIndex.xml:

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

 La \<Language> etiqueta especifica el identificador de idioma (el `Lang` atributo) y el GUID del servicio de lenguaje.

 En este ejemplo se da por supuesto que ha instalado el servicio de lenguaje en la carpeta de instalación de Visual Studio. % LCID% se reemplaza por el ID. de configuración regional actual del usuario. \<SnippetDir>Se pueden agregar varias etiquetas, una para cada directorio y configuración regional diferentes. Además, una carpeta de fragmentos de código puede contener subcarpetas, cada una de las cuales se identifica en el archivo de índice con la \<SnippetSubDir> etiqueta que está incrustada en una \<SnippetDir> etiqueta.

 Los usuarios también pueden crear sus propios fragmentos de código para su idioma. Normalmente, estos se almacenan en la carpeta de configuración del usuario, por ejemplo *[TestDocs]* fragmentos de \Code \\ *[TestLanguage]* \test fragmentos de código, donde *[TestDocs]* es la ubicación de la carpeta de configuración del usuario para Visual Studio.

 Los siguientes elementos de sustitución se pueden colocar en la ruta de acceso almacenada en la \<DirPath> etiqueta en el archivo de índice.

|Elemento|Descripción|
|-------------|-----------------|
|LCID|Id. de configuración regional.|
|InstallRoot|Carpeta de instalación raíz de Visual Studio, por ejemplo, C:\Archivos de Programa\microsoft Visual Studio 8.|
|%ProjDir%|Carpeta que contiene el proyecto actual.|
|%ProjItem%|Carpeta que contiene el elemento de proyecto actual.|
|%TestDocs%|En la carpeta de configuración del usuario, por ejemplo, C:\Documents and Settings \\ *[username]* \Mis documentos\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Habilitar fragmentos de código para el servicio de lenguaje
 Puede habilitar fragmentos de código para el servicio de lenguaje agregando el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> atributo a su VSPackage (consulte [registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obtener más información). Los <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parámetros y son opcionales, pero debe incluir el `SearchPaths` parámetro con nombre para informar al administrador de **fragmentos de código** de la ubicación de los fragmentos de código.

 El siguiente es un ejemplo de cómo usar este atributo:

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
 Hay dos maneras de invocar el proveedor de expansión: mediante el uso de un comando de menú o mediante un acceso directo de una lista de finalización.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Insertar un fragmento de código mediante un comando de menú
 Para usar un comando de menú para mostrar el explorador de fragmentos de código, agregue un comando de menú y, a continuación, llame al <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> método en la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interfaz en respuesta a ese comando de menú.

1. Agregue un comando y un botón al archivo. Vsct. Puede encontrar instrucciones para hacerlo en [crear una extensión con un comando de menú](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Derive una clase de la <xref:Microsoft.VisualStudio.Package.ViewFilter> clase e invalide el <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> método para indicar la compatibilidad con el nuevo comando de menú. Este ejemplo siempre habilita el comando de menú.

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

3. Invalide el <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> método en la <xref:Microsoft.VisualStudio.Package.ViewFilter> clase para obtener el <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto y llamar al <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> método en ese objeto.

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

     Visual Studio llama a los siguientes métodos de la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> clase en el orden especificado durante el proceso de inserción del fragmento de código:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Una vez <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> llamado el método, se ha insertado el fragmento de código y el <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto está en un modo de edición especial que se usa para modificar un fragmento de código que se acaba de insertar.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Insertar un fragmento de código mediante un método abreviado
 La implementación de un acceso directo de una lista de finalización es mucho más complicada que la implementación de un comando de menú. Primero debe agregar accesos directos a fragmentos de código a la lista de finalización de palabras de IntelliSense. A continuación, debe detectar cuándo se ha insertado un nombre de acceso directo del fragmento de código como resultado de la finalización. Por último, debe obtener el título y la ruta del fragmento de código con el nombre de acceso directo y pasar esa información al <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método en el <xref:Microsoft.VisualStudio.Package.ExpansionProvider> método.

 Para agregar accesos directos a fragmentos de código a la lista de finalización de palabras, agréguelos al <xref:Microsoft.VisualStudio.Package.Declarations> objeto en la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase. Debe asegurarse de que puede identificar el acceso directo como un nombre de fragmento de código. Para obtener un ejemplo, vea [Tutorial: obtener una lista de fragmentos de código instalados (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Puede detectar la inserción del acceso directo del fragmento de código en el <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> método de la <xref:Microsoft.VisualStudio.Package.Declarations> clase. Dado que el nombre del fragmento de código ya se ha insertado en el archivo de código fuente, se debe quitar al insertar la expansión. El <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método toma un intervalo que describe el punto de inserción para el fragmento de código; si el intervalo incluye todo el nombre del fragmento de código en el archivo de código fuente, ese nombre se reemplaza por el fragmento de código.

 Esta es una versión de una <xref:Microsoft.VisualStudio.Package.Declarations> clase que controla la inserción de fragmentos de código dado un nombre de acceso directo. Se han omitido otros métodos de la <xref:Microsoft.VisualStudio.Package.Declarations> clase para mayor claridad. Tenga en cuenta que el constructor de esta clase toma un <xref:Microsoft.VisualStudio.Package.LanguageService> objeto. Esto puede pasarse desde su versión del <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto (por ejemplo, la implementación de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase podría tomar el <xref:Microsoft.VisualStudio.Package.LanguageService> objeto en su constructor y pasar ese objeto a su `TestDeclarations` constructor de clase).

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

 Cuando el servicio de lenguaje obtiene el nombre de acceso directo, llama al <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> método para obtener el nombre de archivo y el título del fragmento de código. Después, el servicio de lenguaje llama al <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método de la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> clase para insertar el fragmento de código. Visual Studio llama a los métodos siguientes en el orden especificado en la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> clase durante el proceso de inserción del fragmento de código:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Para obtener más información sobre cómo obtener una lista de fragmentos de código instalados para el servicio de lenguaje, vea [Tutorial: obtener una lista de fragmentos de código instalados (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Implementar la clase ExpansionFunction
 Una función de expansión es una función con nombre que se incrusta en una plantilla de fragmento de código y devuelve uno o más valores que se van a colocar en un campo. Para admitir las funciones de expansión en el servicio de lenguaje, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> clase e implementar el <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> método. A continuación, debe reemplazar el <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase para devolver una nueva instancia de la versión de la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> clase para cada función de expansión que admita. Si admite una lista de valores posibles de una función de expansión, también debe invalidar el <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> método en la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> clase para devolver una lista de esos valores.

 Una función de expansión que toma argumentos o necesita acceder a otros campos no debe estar asociada a un campo editable, ya que es posible que el proveedor de expansión no se inicialice por completo en el momento en que se llama a la función de expansión. Como resultado, la función de expansión no puede obtener el valor de sus argumentos o de cualquier otro campo.

### <a name="example"></a>Ejemplo
 A continuación se muestra un ejemplo de cómo se puede implementar una función de expansión simple `GetName` . Esta función de expansión anexa un número a un nombre de clase base cada vez que se crea una instancia de la función de expansión (que corresponde a cada vez que se inserta el fragmento de código asociado).

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
- [Tutorial: Obtención de una lista de los fragmentos de código instalados (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
