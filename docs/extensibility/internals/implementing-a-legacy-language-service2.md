---
title: Implementación de un servicio de lenguaje heredado2 | Microsoft Docs
description: Obtenga información sobre cómo implementar un servicio de lenguaje heredado que admita características extendidas del servicio de lenguaje mediante el marco de paquetes administrados (MPF). Parte 2 de 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fca2548ddb0c8281241b14de0ec470cfe22db1a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900127"
---
# <a name="implementing-a-legacy-language-service-2"></a>Implementación de un servicio de lenguaje heredado 2
Para implementar un servicio de lenguaje mediante el marco de paquetes administrados (MPF), debe derivar una clase de la clase e implementar los siguientes métodos <xref:Microsoft.VisualStudio.Package.LanguageService> y propiedades abstractos:

- El método <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- El método <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- El método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- La propiedad <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Consulte las secciones adecuadas a continuación para obtener más información sobre la implementación de estos métodos y propiedades.

  Para admitir características adicionales, es posible que el servicio de lenguaje tenga que derivar una clase de una de las clases de servicio de lenguaje MPF; Por ejemplo, para admitir comandos de menú adicionales, debe derivar una clase de la clase e invalidar varios de los métodos de control de <xref:Microsoft.VisualStudio.Package.ViewFilter> comandos (consulte <xref:Microsoft.VisualStudio.Package.ViewFilter> para obtener más información). La clase proporciona una serie de métodos a los que se llama para crear nuevas instancias de varias clases y se invalida el método de creación adecuado para proporcionar una instancia <xref:Microsoft.VisualStudio.Package.LanguageService> de la clase . Por ejemplo, debe invalidar el método <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> de la clase para devolver una instancia de su propia <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ViewFilter> clase. Consulte la sección "Creación de instancias de clases personalizadas" para obtener más detalles.

  El servicio de lenguaje también puede proporcionar sus propios iconos, que se usan en muchos lugares. Por ejemplo, cuando se muestra una lista de finalización de IntelliSense, cada elemento de la lista puede tener un icono asociado, marcando el elemento como un método, clase, espacio de nombres, propiedad o lo que sea necesario para el lenguaje. Estos iconos se usan en todas las listas de IntelliSense, la **barra de navegación** y en la ventana de la tarea Lista **de** errores. Consulte la sección "Imágenes de servicio de lenguaje" a continuación para obtener más información.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences (método)
 El <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> método siempre devuelve la misma instancia de una <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase. Puede usar la clase base si no necesita ninguna preferencia <xref:Microsoft.VisualStudio.Package.LanguagePreferences> adicional para el servicio de lenguaje. Las clases del servicio de lenguaje MPF asumen la presencia de al menos la clase <xref:Microsoft.VisualStudio.Package.LanguagePreferences> base.

### <a name="example"></a>Ejemplo
 En este ejemplo se muestra una implementación típica del <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> método . En este ejemplo se usa la clase <xref:Microsoft.VisualStudio.Package.LanguagePreferences> base .

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

## <a name="getscanner-method"></a>GetScanner (método)
 Este método devuelve una instancia de un objeto que implementa un analizador o analizador orientado a líneas que se usa para obtener tokens y sus <xref:Microsoft.VisualStudio.Package.IScanner> tipos y desencadenadores. Este analizador se usa en la clase para la coloración, aunque el analizador también se puede usar para obtener tipos de token y desencadenadores como preludio de una operación de <xref:Microsoft.VisualStudio.Package.Colorizer> análisis más compleja. Debe proporcionar la clase que implementa la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz y debe implementar todos los métodos en la interfaz <xref:Microsoft.VisualStudio.Package.IScanner> .

### <a name="example"></a>Ejemplo
 En este ejemplo se muestra una implementación típica del <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método . La `TestScanner` clase implementa la interfaz <xref:Microsoft.VisualStudio.Package.IScanner> (no se muestra).

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

## <a name="parsesource-method"></a>ParseSource (método)
 Analiza el archivo de origen en función de una serie de motivos diferentes. A este método se le <xref:Microsoft.VisualStudio.Package.ParseRequest> da un objeto que describe lo que se espera de una operación de análisis determinada. El método invoca un analizador más complejo que determina la funcionalidad y el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ámbito del token. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se usa para admitir las operaciones de IntelliSense, así como para la coincidencia de llaves. Incluso si no admite estas operaciones avanzadas, debe devolver un objeto válido y eso requiere que cree una clase que implemente la interfaz e implemente todos los métodos en <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringScope> esa interfaz. Puede devolver valores NULL de todos los métodos, pero <xref:Microsoft.VisualStudio.Package.AuthoringScope> el propio objeto no debe ser un valor NULL.

### <a name="example"></a>Ejemplo
 En este ejemplo se muestra una implementación mínima del método y la clase , suficiente para permitir que el servicio de lenguaje compile y funcione sin admitir realmente ninguna de las <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> características más avanzadas.

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
 Esta propiedad devuelve el nombre del servicio de lenguaje. Debe ser el mismo nombre especificado cuando se registró el servicio de lenguaje. Este nombre se usa en varios lugares, el más destacado de los cuales es la clase donde se usa el nombre <xref:Microsoft.VisualStudio.Package.LanguagePreferences> para acceder al registro. El nombre devuelto por esta propiedad no debe localizarse, ya que se usa en el Registro para la entrada del Registro y los nombres de clave.

### <a name="example"></a>Ejemplo
 En este ejemplo se muestra una posible implementación de la <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> propiedad . Tenga en cuenta que el nombre aquí está codificado de forma codificada: el nombre real debe obtenerse de un archivo de recursos para que se pueda usar en el registro de un servicio de lenguaje (consulte Registro de un servicio de lenguaje [heredado).](../../extensibility/internals/registering-a-legacy-language-service1.md)

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
 Los métodos siguientes de las clases especificadas se pueden invalidar para proporcionar instancias de sus propias versiones de cada clase.

### <a name="in-the-languageservice-class"></a>En la clase LanguageService

|Método|Clase devuelta|Descripción|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Para admitir adiciones personalizadas a la vista de texto.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Para admitir propiedades de documento personalizadas.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Para admitir la **barra de navegación**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Para admitir funciones en plantillas de fragmentos de código.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Para admitir fragmentos de código (este método normalmente no se invalida).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Para admitir la personalización de <xref:Microsoft.VisualStudio.Package.ParseRequest> la estructura (este método normalmente no se invalida).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Para admitir el formato del código fuente, la especificación de caracteres de comentario y la personalización de firmas de método.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Para admitir comandos de menú adicionales.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Para admitir el resaltado de sintaxis (este método normalmente no se invalida).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Para admitir el acceso a las preferencias de idioma. Este método debe implementarse, pero puede devolver una instancia de la clase base.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Para proporcionar un analizador utilizado para identificar tipos de tokens en una línea. Este método debe implementarse y <xref:Microsoft.VisualStudio.Package.IScanner> debe derivarse de .|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Para proporcionar un analizador utilizado para identificar la funcionalidad y el ámbito en todo un archivo de código fuente. Este método debe implementarse y debe devolver una instancia de la versión de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase . Si lo único que desea admitir es el resaltado de sintaxis (que requiere el analizador devuelto por el método ), no puede hacer nada en este método que no sea devolver una versión de la clase cuyos métodos devuelven valores <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> NULL.|

### <a name="in-the-source-class"></a>En la clase Source

|Método|Clase devuelta|Descripción|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Para personalizar la presentación de listas de finalización de IntelliSense (este método normalmente no se invalida).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Para admitir marcadores en la lista de tareas Lista de errores; en concreto, compatibilidad con características más allá de abrir el archivo y saltar a la línea que produjo el error.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Para personalizar la presentación de información sobre herramientas de información de parámetros de IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Para admitir código de comentarios.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Para recopilar información durante la operación de análisis.|

### <a name="in-the-authoringscope-class"></a>En la clase AuthoringScope

|Método|Clase devuelta|Descripción|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Proporciona una lista de declaraciones como miembros o tipos. Este método debe implementarse, pero puede devolver un valor NULL. Si este método devuelve un objeto válido, el objeto debe ser una instancia de la versión de la <xref:Microsoft.VisualStudio.Package.Declarations> clase .|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Proporciona una lista de firmas de método para un contexto determinado. Este método debe implementarse, pero puede devolver un valor NULL. Si este método devuelve un objeto válido, el objeto debe ser una instancia de la versión de la <xref:Microsoft.VisualStudio.Package.Methods> clase .|

## <a name="language-service-images"></a>Imágenes de Language Service
 Para proporcionar una lista de iconos que se usarán en todo el servicio de lenguaje, invalide el método de la clase y devuelva un elemento <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> que contenga los <xref:System.Windows.Forms.ImageList> iconos. La clase base <xref:Microsoft.VisualStudio.Package.LanguageService> carga un conjunto predeterminado de iconos. Puesto que especifica el índice exacto de la imagen en los lugares que necesitan iconos, la forma de organizar su propia lista de imágenes es totalmente suya.

### <a name="images-used-in-intellisense-completion-lists"></a>Imágenes usadas en listas de finalización de IntelliSense
 Para las listas de finalización de IntelliSense, se especifica el índice de imagen para cada elemento del método de la clase , que debe invalidar si desea proporcionar un <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.Declarations> índice de imagen. El valor devuelto por el método es un índice en la lista de imágenes proporcionada al constructor de clase y que es la misma lista de imágenes devuelta por el método de la clase (puede cambiar la lista de imágenes que se va a usar para si invalida el método de la clase para proporcionar una lista de <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.CompletionSet> imágenes <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.CompletionSet> <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> <xref:Microsoft.VisualStudio.Package.Source> diferente).

### <a name="images-used-in-the-navigation-bar"></a>Imágenes usadas en la barra de navegación
 La **barra de navegación** muestra listas de tipos y miembros y se usa para la navegación rápida puede mostrar iconos. Estos iconos se obtienen del método de la clase y no se pueden invalidar <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> específicamente para la **barra de navegación**. Los índices usados para cada elemento de los cuadros combinados se especifican cuando las listas que representan los cuadros combinados se rellenan en el método de la clase (vea Compatibilidad con la barra de navegación en un servicio de lenguaje <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> [heredado).](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md) Estos índices de imagen se obtienen de algún modo del analizador, normalmente a través de la versión de la <xref:Microsoft.VisualStudio.Package.Declarations> clase . La forma en que se obtienen los índices es totalmente su parte.

### <a name="images-used-in-the-error-list-task-window"></a>Imágenes usadas en la ventana de la tarea Lista de errores
 Cada vez que el analizador de métodos (vea Analizador y analizador de servicios de lenguaje heredado) encuentra un error y lo pasa al método de la clase , el error se notifica en la ventana de la tarea Lista de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> [](../../extensibility/internals/legacy-language-service-parser-and-scanner.md) <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> errores.  Se puede asociar un icono a cada elemento que aparece en la ventana de tareas y ese icono procede de la misma lista de imágenes devuelta por el método <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase . El comportamiento predeterminado de las clases MPF es no mostrar una imagen con el mensaje de error. Sin embargo, puede invalidar este comportamiento derivando una clase de la clase e <xref:Microsoft.VisualStudio.Package.Source> invalidando el <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> método . En ese método, se crea un nuevo <xref:Microsoft.VisualStudio.Package.DocumentTask> objeto . Antes de devolver ese objeto, puede usar la <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> propiedad en el objeto para establecer el índice de <xref:Microsoft.VisualStudio.Package.DocumentTask> imagen. Esto tendría un aspecto parecido al del ejemplo siguiente. Tenga en `TestIconImageIndex` cuenta que es una enumeración que enumera todos los iconos y es específica de este ejemplo. Es posible que tenga una manera diferente de identificar iconos en el servicio de lenguaje.

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
 La lista de imágenes predeterminada proporcionada con las clases base del servicio de lenguaje MPF contiene una serie de iconos asociados a los elementos de lenguaje más comunes. La mayor parte de estos iconos se organizan en conjuntos de seis variaciones, correspondientes a los conceptos de acceso público, interno, de confianza, protegido, privado y acceso directo. Por ejemplo, puede tener iconos diferentes para un método en función de si es público, protegido o privado.

 La enumeración siguiente especifica nombres típicos para cada conjunto de iconos y especifica el índice asociado. Por ejemplo, en función de la enumeración , puede especificar el índice de imagen para un método protegido como `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . Puede cambiar los nombres de esta enumeración según sea necesario.

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

## <a name="see-also"></a>Consulta también
- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)
- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
