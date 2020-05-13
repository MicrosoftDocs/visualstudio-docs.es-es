---
title: Implementación de un servicio de lenguaje heredado2 Microsoft Docs
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
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707675"
---
# <a name="implementing-a-legacy-language-service"></a>Implementación de un servicio de lenguaje heredado
Para implementar un servicio de lenguaje mediante el marco de paquete <xref:Microsoft.VisualStudio.Package.LanguageService> administrado (MPF), debe derivar una clase de la clase e implementar los siguientes métodos y propiedades abstractas:

- El método <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- El método <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- El método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- La propiedad <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Consulte las secciones correspondientes a continuación para obtener más información sobre la implementación de estos métodos y propiedades.

  Para admitir características adicionales, el servicio de lenguaje puede tener que derivar una clase de una de las clases de servicio de lenguaje MPF; por ejemplo, para admitir comandos de menú <xref:Microsoft.VisualStudio.Package.ViewFilter> adicionales, debe derivar una clase <xref:Microsoft.VisualStudio.Package.ViewFilter> de la clase e invalidar varios de los métodos de control de comandos (consulte para obtener más información). La <xref:Microsoft.VisualStudio.Package.LanguageService> clase proporciona una serie de métodos que se llaman para crear nuevas instancias de varias clases y se reemplaza el método de creación adecuado para proporcionar una instancia de la clase. Por ejemplo, debe invalidar <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> el <xref:Microsoft.VisualStudio.Package.LanguageService> método de la clase <xref:Microsoft.VisualStudio.Package.ViewFilter> para devolver una instancia de su propia clase. Consulte la sección "Instantáneas de clases personalizadas" para obtener más detalles.

  Su servicio de idiomas también puede proporcionar sus propios iconos, que se utilizan en muchos lugares. Por ejemplo, cuando se muestra una lista de finalización de IntelliSense, cada elemento de la lista puede tener un icono asociado, marcando el elemento como un método, clase, espacio de nombres, propiedad o lo que sea necesario para su idioma. Estos iconos se utilizan en todas las listas de IntelliSense, la barra de **navegación**y en la ventana de tareas **Lista** de errores. Consulte la sección "Imágenes del servicio de lenguaje" a continuación para obtener más información.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences Método
 El <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> método siempre devuelve la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> misma instancia de una clase. Puede utilizar la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase base si no necesita ninguna preferencia adicional para su servicio de idiomas. Las clases de servicio de lenguaje MPF asumen la presencia de al menos la clase base. <xref:Microsoft.VisualStudio.Package.LanguagePreferences>

### <a name="example"></a>Ejemplo
 En este ejemplo se <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> muestra una implementación típica del método. En este ejemplo <xref:Microsoft.VisualStudio.Package.LanguagePreferences> se utiliza la clase base.

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

## <a name="getscanner-method"></a>GetScanner Método
 Este método devuelve una <xref:Microsoft.VisualStudio.Package.IScanner> instancia de un objeto que implementa un analizador o analizador orientado a líneas que se utiliza para obtener tokens y sus tipos y desencadenadores. Este escáner se <xref:Microsoft.VisualStudio.Package.Colorizer> utiliza en la clase para la coloración, aunque el escáner también se puede utilizar para obtener tipos de token y desencadenadores como preludio de una operación de análisis más compleja. Debe proporcionar la clase que <xref:Microsoft.VisualStudio.Package.IScanner> implementa la interfaz y <xref:Microsoft.VisualStudio.Package.IScanner> debe implementar todos los métodos en la interfaz.

### <a name="example"></a>Ejemplo
 En este ejemplo se <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> muestra una implementación típica del método. La `TestScanner` clase implementa <xref:Microsoft.VisualStudio.Package.IScanner> la interfaz (no se muestra).

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

## <a name="parsesource-method"></a>ParseSource Método
 Analiza el archivo de origen en función de varias razones diferentes. A este método <xref:Microsoft.VisualStudio.Package.ParseRequest> se le da un objeto que describe lo que se espera de una operación de análisis determinada. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método invoca un analizador más complejo que determina la funcionalidad y el ámbito del token. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se utiliza en soporte para las operaciones de IntelliSense, así como la coincidencia de llaves. Incluso si no admite estas operaciones avanzadas, <xref:Microsoft.VisualStudio.Package.AuthoringScope> debe devolver un objeto válido y eso <xref:Microsoft.VisualStudio.Package.AuthoringScope> requiere crear una clase que implemente la interfaz e implemente todos los métodos en esa interfaz. Puede devolver valores null de <xref:Microsoft.VisualStudio.Package.AuthoringScope> todos los métodos, pero el propio objeto no debe ser un valor nulo.

### <a name="example"></a>Ejemplo
 En este ejemplo se <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> muestra una <xref:Microsoft.VisualStudio.Package.AuthoringScope> implementación mínima del método y la clase, suficiente para permitir que el servicio de lenguaje compile y funcione sin admitir realmente ninguna de las características más avanzadas.

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
 Esta propiedad devuelve el nombre del servicio de lenguaje. Debe tener el mismo nombre que se indica cuando se registró el servicio de lenguaje. Este nombre se utiliza en varios lugares, el <xref:Microsoft.VisualStudio.Package.LanguagePreferences> más destacado de los cuales es la clase donde se utiliza el nombre para acceder al registro. El nombre devuelto por esta propiedad no debe estar localizado, ya que se utiliza en el registro para la entrada del Registro y los nombres de clave.

### <a name="example"></a>Ejemplo
 En este ejemplo se <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> muestra una posible implementación de la propiedad. Tenga en cuenta que el nombre aquí está codificado de forma rígida: el nombre real debe obtenerse de un archivo de recursos para que se pueda utilizar en el registro de un servicio de lenguaje (consulte Registro de un servicio de [lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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

## <a name="instantiating-custom-classes"></a>Creación de instancias de clases personalizadas
 Los siguientes métodos en las clases especificadas se pueden invalidar para proporcionar instancias de sus propias versiones de cada clase.

### <a name="in-the-languageservice-class"></a>En la clase LanguageService

|Método|Clase devuelta|Descripción|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Para admitir adiciones personalizadas a la vista de texto.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Para admitir propiedades de documento personalizadas.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Para admitir la **barra de navegación**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Para admitir funciones en plantillas de fragmento de código.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Para admitir fragmentos de código (normalmente no se invalida este método).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Para admitir la <xref:Microsoft.VisualStudio.Package.ParseRequest> personalización de la estructura (este método normalmente no se invalida).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Para admitir el formato de código fuente, especificar caracteres de comentario y personalizar las firmas de método.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Para admitir comandos de menú adicionales.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Para admitir el resaltado de sintaxis (este método normalmente no se invalida).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Para admitir el acceso a las preferencias de idioma. Este método debe implementarse, pero puede devolver una instancia de la clase base.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Proporcionar un analizador utilizado para identificar tipos de tokens en una línea. Este método debe implementarse y <xref:Microsoft.VisualStudio.Package.IScanner> debe derivarse de.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Proporcionar un analizador utilizado para identificar la funcionalidad y el ámbito en todo un archivo de origen. Este método debe implementarse y debe devolver una <xref:Microsoft.VisualStudio.Package.AuthoringScope> instancia de la versión de la clase. Si todo lo que desea admitir es resaltado <xref:Microsoft.VisualStudio.Package.IScanner> de sintaxis <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (que requiere el analizador devuelto desde el <xref:Microsoft.VisualStudio.Package.AuthoringScope> método), no puede hacer nada en este método que no sea devolver una versión de la clase cuyos métodos devuelven valores null.|

### <a name="in-the-source-class"></a>En la clase Source

|Método|Clase devuelta|Descripción|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Para personalizar la visualización de las listas de finalización de IntelliSense (este método normalmente no se invalida).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Para admitir marcadores en la lista de tareas Lista de errores; específicamente, soporte para características más allá de abrir el archivo y saltar a la línea que causó el error.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Para personalizar la visualización de Información de parámetros de IntelliSense Info ToolTips.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Para admitir el código de comentarios.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Para recopilar información durante la operación de análisis.|

### <a name="in-the-authoringscope-class"></a>En la clase AuthoringScope

|Método|Clase devuelta|Descripción|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Proporciona una lista de declaraciones como miembros o tipos. Este método debe implementarse, pero puede devolver un valor nulo. Si este método devuelve un objeto válido, el objeto <xref:Microsoft.VisualStudio.Package.Declarations> debe ser una instancia de la versión de la clase.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Proporciona una lista de firmas de método para un contexto determinado. Este método debe implementarse, pero puede devolver un valor nulo. Si este método devuelve un objeto válido, el objeto <xref:Microsoft.VisualStudio.Package.Methods> debe ser una instancia de la versión de la clase.|

## <a name="language-service-images"></a>Imágenes del servicio de lenguaje
 Para proporcionar una lista de iconos que se usarán en todo el servicio de lenguaje, invalide el <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase y devuelva un <xref:System.Windows.Forms.ImageList> que contenga los iconos. La <xref:Microsoft.VisualStudio.Package.LanguageService> clase base carga un conjunto predeterminado de iconos. Puesto que especifica el índice de imagen exacto en aquellos lugares que necesitan iconos, la forma de organizar su propia lista de imágenes depende totalmente de usted.

### <a name="images-used-in-intellisense-completion-lists"></a>Imágenes utilizadas en las listas de finalización de IntelliSense
 Para las listas de finalización de IntelliSense, <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> se especifica <xref:Microsoft.VisualStudio.Package.Declarations> el índice de imagen para cada elemento del método de la clase, que debe invalidar si desea proporcionar un índice de imagen. El valor devuelto <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> por el método es un <xref:Microsoft.VisualStudio.Package.CompletionSet> índice en la lista de imágenes proporcionada <xref:Microsoft.VisualStudio.Package.LanguageService> al constructor de clase y que <xref:Microsoft.VisualStudio.Package.CompletionSet> es la <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> misma <xref:Microsoft.VisualStudio.Package.Source> lista de imágenes devuelta por el <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método de la clase (puede cambiar la lista de imágenes que se usará para el if invalidar el método en la clase para proporcionar una lista de imágenes diferente).

### <a name="images-used-in-the-navigation-bar"></a>Imágenes utilizadas en la barra de navegación
 La barra de **navegación** muestra listas de tipos y miembros y se utiliza para la navegación rápida puede mostrar iconos. Estos iconos se obtienen <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> del <xref:Microsoft.VisualStudio.Package.LanguageService> método de la clase y no se pueden invalidar específicamente para la barra de **navegación**. Los índices utilizados para cada elemento de los cuadros combinados se especifican <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> cuando las <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> listas que representan los cuadros combinados se rellenan en el método de la clase (consulte Compatibilidad con la barra de navegación en un servicio de [lenguaje heredado).](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md) Estos índices de imagen se obtienen de alguna manera <xref:Microsoft.VisualStudio.Package.Declarations> del analizador, normalmente a través de la versión de la clase. La forma en que se obtienen los índices depende totalmente de usted.

### <a name="images-used-in-the-error-list-task-window"></a>Imágenes utilizadas en la ventana de tareas Lista de errores
 Siempre <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> que el analizador de métodos (consulte [Analizador y analizador](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)de legacy <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> Language Service <xref:Microsoft.VisualStudio.Package.AuthoringSink> ) encuentra un error y pasa ese error al método de la clase, el error se notifica en la ventana de tareas **Lista** de errores. Un icono se puede asociar a cada elemento que aparece en la ventana de <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> tareas y <xref:Microsoft.VisualStudio.Package.LanguageService> ese icono proviene de la misma lista de imágenes devuelta desde el método de la clase. El comportamiento predeterminado de las clases MPF es no mostrar una imagen con el mensaje de error. Sin embargo, puede invalidar este comportamiento <xref:Microsoft.VisualStudio.Package.Source> derivando una <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> clase de la clase y reemplazando el método. En ese método, se <xref:Microsoft.VisualStudio.Package.DocumentTask> crea un nuevo objeto. Antes de devolver ese objeto, <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> puede <xref:Microsoft.VisualStudio.Package.DocumentTask> utilizar la propiedad del objeto para establecer el índice de imagen. Esto se vería algo parecido al siguiente ejemplo. Tenga `TestIconImageIndex` en cuenta que es una enumeración que enumera todos los iconos y es específica de este ejemplo. Es posible que tenga una forma diferente de identificar iconos en su servicio de idiomas.

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

## <a name="the-default-image-list-for-a-language-service"></a>La lista de imágenes predeterminadas para un servicio de lenguaje
 La lista de imágenes predeterminada proporcionada con las clases de servicio de lenguaje MPF base contiene una serie de iconos asociados con los elementos de lenguaje más comunes. La mayor parte de estos iconos están dispuestos en conjuntos de seis variaciones, correspondientes a los conceptos de acceso de público, interno, amigo, protegido, privado y acceso directo. Por ejemplo, puede tener diferentes iconos para un método dependiendo de si es público, protegido o privado.

 La enumeración siguiente especifica los nombres típicos para cada conjunto de elementos y especifica el índice asociado. Por ejemplo, en función de la enumeración, puede `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`especificar el índice de imagen para un método protegido como . Puede cambiar los nombres de esta enumeración como desee.

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
