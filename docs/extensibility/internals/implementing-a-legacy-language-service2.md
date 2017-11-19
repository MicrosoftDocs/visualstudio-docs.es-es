---
title: Implementar un Service2 de lenguaje heredado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24e847eb0f1d05717ab6b114921a66b04cd94922
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-a-legacy-language-service"></a>Implementar un servicio de lenguaje heredado
Para implementar un servicio de lenguaje mediante managed package framework (MPF), debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase e implementar los siguientes métodos y propiedades abstractos:  
  
-   El método <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>  
  
-   El método <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
-   El método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
-   La propiedad <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>  
  
 Vea las secciones correspondientes a continuación para obtener más información sobre la implementación de estos métodos y propiedades.  
  
 Para admitir características adicionales, el servicio de lenguaje que tenga que derivar una clase de una de las clases de servicio de lenguaje MPF; Por ejemplo, para admitir otros comandos de menú, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.ViewFilter> clase e invalidar algunos de los métodos de control de comandos (consulte <xref:Microsoft.VisualStudio.Package.ViewFilter> para obtener más información). La <xref:Microsoft.VisualStudio.Package.LanguageService> clase proporciona una serie de métodos que se llama para crear nuevas instancias de varias clases y reemplace el método de creación adecuada para proporcionar una instancia de la clase. Por ejemplo, debe invalidar el <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase para devolver una instancia de su propio <xref:Microsoft.VisualStudio.Package.ViewFilter> clase. Vea la sección "Crear instancias de clases personalizadas" para obtener más detalles.  
  
 El servicio de lenguaje también puede proporcionar sus propios iconos, que se utilizan en muchos lugares. Por ejemplo, cuando se muestra una lista de finalización de IntelliSense, cada elemento de la lista puede tener un icono asociado a ella, aunque se marque el elemento como un método, clase, espacio de nombres, propiedad, o lo que sea necesario para su idioma. Estos iconos se usan en todas las listas de IntelliSense, la **barra de navegación**y en el **lista de errores** ventana de tareas. Vea la sección "Servicio de lenguaje imágenes" a continuación para obtener más información.  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences (método)  
 El <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> método siempre devuelve la misma instancia de un <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase. Puede utilizar la base de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase si no necesita ninguna preferencia adicional para el servicio de lenguaje. Las clases de servicio de lenguaje MPF supone la presencia de al menos el base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra una implementación típica de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> método. Este ejemplo utiliza la base de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.  
  
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
 Este método devuelve una instancia de un <xref:Microsoft.VisualStudio.Package.IScanner> objeto que implementa un analizador de línea o un escáner usado para obtener los tokens, sus tipos y desencadenadores. Este analizador se utiliza en la <xref:Microsoft.VisualStudio.Package.Colorizer> clase coloración aunque también se puede utilizar el escáner para obtener los desencadenadores y tipos de token como un paso previo a una operación de análisis más complejo. Debe proporcionar la clase que implementa el <xref:Microsoft.VisualStudio.Package.IScanner> interfaz y se deben implementar todos los métodos en el <xref:Microsoft.VisualStudio.Package.IScanner> interfaz.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra una implementación típica de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método. El `TestScanner` la clase implementa la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz (no se muestra).  
  
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
 Analiza el archivo de origen en función de una serie de motivos diferentes. Este método recibe un <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto que describe qué cabe esperar de una determinada operación de análisis. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método invoca un analizador más complejo que determina la funcionalidad de token y el ámbito. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se utiliza en la compatibilidad con IntelliSense, así como la coincidencia de llaves. Incluso si no se admiten estas operaciones avanzadas, todavía debe devolver válido <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto y que requiere que se cree una clase que implementa el <xref:Microsoft.VisualStudio.Package.AuthoringScope> interfaz e implementar todos los métodos de esa interfaz. Puede devolver valores null en todos los métodos, pero la <xref:Microsoft.VisualStudio.Package.AuthoringScope> propio objeto no debe ser un valor null.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra una implementación mínima de la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método y <xref:Microsoft.VisualStudio.Package.AuthoringScope> (clase), suficiente para permitir que el servicio de lenguaje compilar y funcionando correctamente sin necesidad de admitir realmente cualquiera de las características más avanzadas.  
  
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
  
## <a name="name-property"></a>Propiedad de nombre  
 Esta propiedad devuelve el nombre del servicio de lenguaje. Debe ser el mismo nombre que especificó cuando se registró el servicio de lenguaje. Este nombre se utiliza en varios lugares, es más destacada de los cuales el <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase donde el nombre se utiliza para tener acceso al registro. No se debe localizar el nombre devuelto por esta propiedad como se utiliza en el registro para la entrada del registro y los nombres de clave.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra una posible implementación de la <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> propiedad. Tenga en cuenta que aquí el nombre codificado de forma rígida: el nombre real se debe obtener de un archivo de recursos, por lo que puede usarse para registrar un servicio de lenguaje (vea [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
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
  
|Método|Clase devueltas|Descripción|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Para admitir las adiciones personalizadas a la vista de texto.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Para admitir las propiedades de documento personalizadas.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Para admitir la **barra de navegación**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Para admitir las funciones en las plantillas de fragmento de código.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Para admitir los fragmentos de código (se invalida este método normalmente no).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Para admitir la personalización de la <xref:Microsoft.VisualStudio.Package.ParseRequest> estructura (se invalida este método normalmente no).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Para que admita formato código fuente, especificar caracteres de comentario y personalizar las firmas de método.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Para admitir otros comandos de menú.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Para admitir el resaltado de sintaxis (se invalida este método normalmente no).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Para admitir el acceso a las preferencias de idioma. Este método se debe implementar, pero puede devolver una instancia de la clase base.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Para proporcionar un analizador usado para identificar los tipos de símbolos (tokens) en una línea. Este método se debe implementar y <xref:Microsoft.VisualStudio.Package.IScanner> debe derivarse de.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Para proporcionar un analizador utilizado para identificar la funcionalidad y ámbito a lo largo de un archivo de código fuente. Este método debe implementarse y debe devolver una instancia de la versión de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase. Si todo lo que desea admitir están resaltado de sintaxis (que requiere el <xref:Microsoft.VisualStudio.Package.IScanner> analizador devuelto desde el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método), puede hacer nada en este método que no sea devuelto una versión de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase cuyos métodos todas devuelven valores null.|  
  
### <a name="in-the-source-class"></a>En la clase de origen  
  
|Método|Clase devueltas|Descripción|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Para personalizar la visualización de listas de finalización de IntelliSense (se invalida este método normalmente no).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Para admitir marcadores en la lista de tareas de la lista de errores; en concreto, compatibilidad con las características más allá de abrir el archivo y saltar a la línea que produjo el error.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Para personalizar la presentación de parámetro de IntelliSense información sobre herramientas.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Para admitir los comentarios del código.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Para recopilar información durante la operación de análisis.|  
  
### <a name="in-the-authoringscope-class"></a>En la clase AuthoringScope  
  
|Método|Clase devueltas|Descripción|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Proporciona una lista de declaraciones de miembros o tipos. Este método se debe implementar, pero puede devolver un valor null. Si este método devuelve un objeto válido, el objeto debe ser una instancia de la versión de la <xref:Microsoft.VisualStudio.Package.Declarations> clase.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Proporciona una lista de firmas de método para un contexto determinado. Este método se debe implementar, pero puede devolver un valor null. Si este método devuelve un objeto válido, el objeto debe ser una instancia de la versión de la <xref:Microsoft.VisualStudio.Package.Methods> clase.|  
  
## <a name="language-service-images"></a>Imágenes del servicio de lenguaje  
 Para proporcionar una lista de iconos que se usará en el servicio de lenguaje, invalidar la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase y devolver un <xref:System.Windows.Forms.ImageList> que contiene los iconos. La base de <xref:Microsoft.VisualStudio.Package.LanguageService> clase carga un conjunto predeterminado de iconos. Puesto que especifica el índice de imagen exacta en los lugares que necesitan iconos, cómo organizar su propia lista de imágenes es suya.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>Imágenes que se utilizan en las listas de finalización de IntelliSense  
 Para listas de finalización de IntelliSense, el índice de imagen se especifica para cada elemento de la <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> método de la <xref:Microsoft.VisualStudio.Package.Declarations> (clase), que debe reemplazar si desea proporcionar un índice de imágenes. El valor devuelto de la <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> método es un índice en la lista de imágenes proporcionado a la <xref:Microsoft.VisualStudio.Package.CompletionSet> procedentes de constructor de clase y que es la misma lista de imágenes la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> (clase) (puede cambiar qué lista de imágenes para usar para la <xref:Microsoft.VisualStudio.Package.CompletionSet> si invalida la <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase para proporcionar una lista de imágenes diferentes).  
  
### <a name="images-used-in-the-navigation-bar"></a>Imágenes que se utilizan en la barra de navegación  
 El **barra de navegación** muestra listas de tipos y miembros y se utiliza para una navegación rápida, puede mostrar iconos. Estos iconos se obtienen de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase y no se puede invalidar específicamente para el **barra de navegación**. Los índices usados para cada elemento en los cuadros combinados se especifican cuando se llenan las listas que representa los cuadros combinados el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método en el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> clase (vea [compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Estos índices de la imagen se obtienen de algún modo del analizador, normalmente a través de la versión de la <xref:Microsoft.VisualStudio.Package.Declarations> clase. ¿Cómo se obtienen los índices es decisión suya.  
  
### <a name="images-used-in-the-error-list-task-window"></a>Imágenes que se utilizan en la ventana de tareas de la lista de errores  
 Cada vez que la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador (método) (vea [analizador del servicio de lenguaje heredado y el analizador](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) encuentra un error y pasa ese error para la <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> método en el <xref:Microsoft.VisualStudio.Package.AuthoringSink> (clase), el error se produce en el  **Lista de errores** ventana de tareas. Un icono puede ser asociado a cada elemento que aparece en la ventana de la tarea y ese icono procede de la misma lista de imágenes procedente de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. El comportamiento predeterminado de las clases MPF es no mostrar una imagen con el mensaje de error. Sin embargo, puede invalidar este comportamiento, derive una clase de la <xref:Microsoft.VisualStudio.Package.Source> clase e invalidar el <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> método. En ese método, se crea un nuevo <xref:Microsoft.VisualStudio.Package.DocumentTask> objeto. Antes de devolver ese objeto, puede usar el <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> propiedad en la <xref:Microsoft.VisualStudio.Package.DocumentTask> objeto para establecer el índice de imagen. Esto tendría un aspecto similar al ejemplo siguiente. Tenga en cuenta que `TestIconImageIndex` es una enumeración que enumera todos los iconos y es específica de este ejemplo. Puede tener una manera diferente de identificación de iconos en el servicio de lenguaje.  
  
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
            TastPriority      priority,  
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
  
## <a name="the-default-image-list-for-a-language-service"></a>La lista de imágenes de forma predeterminada para un servicio de lenguaje  
 La lista de imágenes predeterminado proporcionada con las clases de servicio de lenguaje MPF base contiene una serie de iconos asociados a los elementos del lenguaje más comunes. La mayor parte de estos iconos están organizadas en conjuntos de seis variaciones, correspondiente a los conceptos de acceso del público, interno, friend, protegida, privada y acceso directo. Por ejemplo, puede tener iconos diferentes para un método dependiendo de si es pública, protegida o privada.  
  
 La siguiente enumeración especifica nombres típicos para cada conjunto de iconos y el índice asociado. Por ejemplo, en función de la enumeración, se puede especificar el índice de imagen para un método protegido como `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Puede cambiar los nombres de esta enumeración según sea necesario.  
  
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
 [Implementar un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Introducción al servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)   
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)