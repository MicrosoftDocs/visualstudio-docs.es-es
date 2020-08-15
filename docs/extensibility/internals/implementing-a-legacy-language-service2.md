---
title: Implementación de un service2 de lenguaje heredado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df44b92cdf311689397a062b127d4c3e514a15e6
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238704"
---
# <a name="implementing-a-legacy-language-service-2"></a>Implementación de un servicio de lenguaje heredado 2
Para implementar un servicio de lenguaje con Managed Package Framework (MPF), debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase e implementar los siguientes métodos y propiedades abstractos:

- El método <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- El método <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- El método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- La propiedad <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Vea las secciones correspondientes a continuación para obtener más información sobre la implementación de estos métodos y propiedades.

  Para admitir características adicionales, el servicio de lenguaje puede tener que derivar una clase de una de las clases de servicio del lenguaje MPF; por ejemplo, para admitir comandos de menú adicionales, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.ViewFilter> clase e invalidar algunos de los métodos de control de comandos (vea <xref:Microsoft.VisualStudio.Package.ViewFilter> para obtener más detalles). La <xref:Microsoft.VisualStudio.Package.LanguageService> clase proporciona una serie de métodos a los que se llama para crear nuevas instancias de varias clases e invalidar el método de creación adecuado para proporcionar una instancia de la clase. Por ejemplo, debe invalidar el <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase para devolver una instancia de su propia <xref:Microsoft.VisualStudio.Package.ViewFilter> clase. Vea la sección "creación de instancias de clases personalizadas" para obtener más detalles.

  El servicio de lenguaje también puede proporcionar sus propios iconos, que se usan en muchos lugares. Por ejemplo, cuando se muestra una lista de finalización de IntelliSense, cada elemento de la lista puede tener un icono asociado, marcando el elemento como un método, clase, espacio de nombres, propiedad o lo que sea necesario para su lenguaje. Estos iconos se utilizan en todas las listas de IntelliSense, en la **barra de navegación**y en la ventana de tareas de **lista de errores** . Vea la sección "imágenes del servicio de lenguaje" más adelante para obtener más información.

## <a name="getlanguagepreferences-method"></a>Método GetLanguagePreferences
 El <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> método siempre devuelve la misma instancia de una <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase. Puede usar la clase base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> si no necesita ninguna preferencia adicional para su servicio de lenguaje. Las clases de servicio del lenguaje MPF suponen la presencia de al menos la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase base.

### <a name="example"></a>Ejemplo
 En este ejemplo se muestra una implementación típica del <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> método. En este ejemplo se utiliza la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase base.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>Método GetScanner
 Este método devuelve una instancia de un <xref:Microsoft.VisualStudio.Package.IScanner> objeto que implementa un analizador o analizador orientado a líneas que se usa para obtener tokens y sus tipos y desencadenadores. Este escáner se usa en la <xref:Microsoft.VisualStudio.Package.Colorizer> clase para la coloración, aunque el escáner también se puede usar para obtener tipos de token y desencadenadores como un preparativo de una operación de análisis más compleja. Debe proporcionar la clase que implementa la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz y debe implementar todos los métodos en la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz.

### <a name="example"></a>Ejemplo
 En este ejemplo se muestra una implementación típica del <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método. La `TestScanner` clase implementa la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz (no se muestra).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>Método ParseSource
 Analiza el archivo de código fuente en función de una serie de motivos diferentes. A este método se le proporciona un <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto que describe lo que se espera de una operación de análisis determinada. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método invoca un analizador más complejo que determina la funcionalidad y el ámbito de los tokens. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se usa en la compatibilidad con las operaciones de IntelliSense y con la coincidencia de llaves. Aunque no admita dichas operaciones avanzadas, debe devolver un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto válido y que requiera que cree una clase que implemente la <xref:Microsoft.VisualStudio.Package.AuthoringScope> interfaz e implemente todos los métodos en esa interfaz. Puede devolver valores NULL de todos los métodos, pero el <xref:Microsoft.VisualStudio.Package.AuthoringScope> propio objeto no debe ser un valor null.

### <a name="example"></a>Ejemplo
 En este ejemplo se muestra una implementación mínima del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método y la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase, suficiente para permitir que el servicio de lenguaje se compile y funcione sin admitir realmente ninguna de las características más avanzadas.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Propiedad Name
 Esta propiedad devuelve el nombre del servicio de lenguaje. Debe ser el mismo nombre que se especificó cuando se registró el servicio de lenguaje. Este nombre se usa en varios lugares, lo más destacado de los cuales es la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase donde se usa el nombre para tener acceso al registro. El nombre devuelto por esta propiedad no debe estar localizado, ya que se utiliza en el registro para la entrada y los nombres de clave del registro.

### <a name="example"></a>Ejemplo
 En este ejemplo se muestra una posible implementación de la <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> propiedad. Tenga en cuenta que el nombre aquí está codificado de forma rígida: el nombre real debe obtenerse de un archivo de recursos para que se pueda usar en el registro de un servicio de lenguaje (consulte [registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>Crear instancias de clases personalizadas
 Los siguientes métodos de las clases especificadas se pueden invalidar para proporcionar instancias de sus propias versiones de cada clase.

### <a name="in-the-languageservice-class"></a>En la clase LanguageService

|Método|Clase devuelta|Descripción|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Para admitir adiciones personalizadas a la vista de texto.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Para admitir las propiedades personalizadas del documento.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Para admitir la **barra de navegación**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Para admitir funciones en plantillas de fragmentos de código.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Para admitir fragmentos de código (este método normalmente no se invalida).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Para admitir la personalización de la <xref:Microsoft.VisualStudio.Package.ParseRequest> estructura (este método normalmente no se invalida).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Es para admitir el formato del código fuente, la especificación de caracteres de comentario y la personalización de firmas de método.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Para admitir comandos de menú adicionales.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Para admitir el resaltado de sintaxis (este método normalmente no se invalida).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Para admitir el acceso a las preferencias de idioma. Este método se debe implementar, pero puede devolver una instancia de la clase base.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Para proporcionar un analizador que se usa para identificar tipos de tokens en una línea. Este método debe implementarse y <xref:Microsoft.VisualStudio.Package.IScanner> debe derivarse de.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Para proporcionar un analizador que se usa para identificar la funcionalidad y el ámbito en todo un archivo de código fuente. Este método debe implementarse y debe devolver una instancia de la versión de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase. Si todo lo que desea es compatible con el resaltado de sintaxis (que requiere el <xref:Microsoft.VisualStudio.Package.IScanner> analizador devuelto desde el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método), no puede hacer nada en este método distinto de devolver una versión de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase cuyos métodos devuelven valores NULL.|

### <a name="in-the-source-class"></a>En la clase de origen

|Método|Clase devuelta|Descripción|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Para personalizar la presentación de las listas de finalización de IntelliSense (este método no suele reemplazarse).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Para admitir marcadores en el Lista de errores lista de tareas; en concreto, se admiten las características más allá de abrir el archivo y saltar a la línea que causó el error.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Para personalizar la presentación de la información sobre herramientas de información de parámetros de IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Para admitir el código de comentario.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Para recopilar información durante la operación de análisis.|

### <a name="in-the-authoringscope-class"></a>En la clase AuthoringScope

|Método|Clase devuelta|Descripción|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Proporciona una lista de declaraciones como miembros o tipos. Este método se debe implementar, pero puede devolver un valor null. Si este método devuelve un objeto válido, el objeto debe ser una instancia de la versión de la <xref:Microsoft.VisualStudio.Package.Declarations> clase.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Proporciona una lista de firmas de método para un contexto determinado. Este método se debe implementar, pero puede devolver un valor null. Si este método devuelve un objeto válido, el objeto debe ser una instancia de la versión de la <xref:Microsoft.VisualStudio.Package.Methods> clase.|

## <a name="language-service-images"></a>Imágenes de servicio de lenguaje
 Para proporcionar una lista de los iconos que se van a usar en el servicio de lenguaje, invalide el <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase y devuelva un objeto <xref:System.Windows.Forms.ImageList> que contenga los iconos. La <xref:Microsoft.VisualStudio.Package.LanguageService> clase base carga un conjunto predeterminado de iconos. Dado que se especifica el índice exacto de la imagen en los lugares en los que se necesitan iconos, la forma en que se organiza su propia lista de imágenes es totalmente suya.

### <a name="images-used-in-intellisense-completion-lists"></a>Imágenes usadas en las listas de finalización de IntelliSense
 En el caso de las listas de finalización de IntelliSense, el índice de imagen se especifica para cada elemento en el <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> método de la <xref:Microsoft.VisualStudio.Package.Declarations> clase, que se debe invalidar si se desea proporcionar un índice de imagen. El valor devuelto desde el <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> método es un índice de la lista de imágenes que <xref:Microsoft.VisualStudio.Package.CompletionSet> se proporciona al constructor de clase y que es la misma lista de imágenes devuelta por el <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase (puede cambiar la lista de imágenes que se va a usar para <xref:Microsoft.VisualStudio.Package.CompletionSet> si invalida el <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase para proporcionar una lista de imágenes diferente).

### <a name="images-used-in-the-navigation-bar"></a>Imágenes usadas en la barra de navegación
 La **barra de navegación** muestra las listas de tipos y miembros, y se usa para la navegación rápida puede mostrar iconos. Estos iconos se obtienen del <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase y no se pueden invalidar específicamente para la **barra de navegación**. Los índices usados para cada elemento en los cuadros combinados se especifican cuando las listas que representan los cuadros combinados se rellenan en el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> clase (vea [compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Estos índices de imagen se obtienen de algún modo desde el analizador, normalmente a través de la versión de la <xref:Microsoft.VisualStudio.Package.Declarations> clase. La forma en que se obtienen los índices es totalmente suya.

### <a name="images-used-in-the-error-list-task-window"></a>Imágenes que se usan en la ventana de tareas de Lista de errores
 Siempre que el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador de métodos (vea [analizador y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) encuentra un error y pasa ese error al <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> método de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase, el error se muestra en la ventana de **lista de errores** tarea. Se puede asociar un icono a cada elemento que aparece en la ventana de tareas y ese icono proviene de la misma lista de imágenes devuelta por el <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. El comportamiento predeterminado de las clases MPF es no mostrar una imagen con el mensaje de error. Sin embargo, puede invalidar este comportamiento derivando una clase de la <xref:Microsoft.VisualStudio.Package.Source> clase e invalidando el <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> método. En ese método, se crea un nuevo <xref:Microsoft.VisualStudio.Package.DocumentTask> objeto. Antes de devolver ese objeto, puede usar la <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> propiedad en el <xref:Microsoft.VisualStudio.Package.DocumentTask> objeto para establecer el índice de la imagen. Esto tendría un aspecto similar al del ejemplo siguiente. Tenga en cuenta que `TestIconImageIndex` es una enumeración que enumera todos los iconos y que es específica de este ejemplo. Puede tener una manera diferente de identificar iconos en el servicio de lenguaje.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>La lista de imágenes predeterminada para un servicio de lenguaje
 La lista de imágenes predeterminada suministrada con las clases de servicio de lenguaje MPF base contiene varios iconos asociados a los elementos de lenguaje más comunes. La mayor parte de estos iconos se organiza en conjuntos de seis variaciones, correspondientes a los conceptos de acceso de Public, Internal, Friend, Protected, Private y Shortcut. Por ejemplo, puede tener iconos diferentes para un método en función de si es público, protegido o privado.

 La enumeración siguiente especifica nombres típicos para cada conjunto de iconos y especifica el índice asociado. Por ejemplo, en función de la enumeración, puede especificar el índice de la imagen para un método protegido como `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . Puede cambiar los nombres en esta enumeración según sea necesario.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>Vea también
- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)
- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
