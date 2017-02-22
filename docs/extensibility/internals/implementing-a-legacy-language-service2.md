---
title: "Implementaci&#243;n de un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje [managed package framework], implementar"
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementaci&#243;n de un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Para implementar un servicio de mediante el \(MPF\) managed package, debe derivar una clase de la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> e implementar los métodos y las propiedades abstractos siguientes:  
  
-   Método <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>  
  
-   Método <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
-   Método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
-   La propiedad <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>  
  
 Vea las secciones adecuadas más adelante los detalles en implementar estos métodos y propiedades.  
  
 Para admitir características adicionales, el servicio de lenguaje puede tener que derivar una clase de una de las clases del servicio de lenguaje de MPF; por ejemplo, para admitir comandos de menú, debe derivar una clase de la clase de <xref:Microsoft.VisualStudio.Package.ViewFilter> y reemplazar a varios de comando que administra métodos \(vea <xref:Microsoft.VisualStudio.Package.ViewFilter> para obtener detalles\).  La clase de <xref:Microsoft.VisualStudio.Package.LanguageService> proporciona varios métodos que se llama para crear nuevas instancias de clases diferentes y reemplace el método adecuado de creación para proporcionar una instancia de la clase.  Por ejemplo, es necesario reemplazar el método de <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> en la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> para devolver una instancia de dispone de la clase de <xref:Microsoft.VisualStudio.Package.ViewFilter> .  Vea “crear instancias la sección clases personalizadas” para obtener más detalles.  
  
 El servicio de lenguaje puede proporcionar sus propios iconos, que se utilizan en muchos lugares.  Por ejemplo, cuando se muestra una lista de finalización de IntelliSense, cada elemento de la lista puede tener un icono asociado, marcando el elemento como un método, clase, espacio de nombres, propiedad, o lo que sea necesario para el idioma.  Estos iconos se utilizan en todas las listas de IntelliSense, **Barra de navegación**y, en la ventana de la tarea de **Lista de errores** .  Vea “lenguaje la sección de Service Imágenes” para los detalles.  
  
## método de GetLanguagePreferences  
 El método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> siempre devuelve la misma instancia de una clase de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  Puede utilizar la clase base de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> si no necesita ninguna preferencias adicional para el servicio de lenguaje.  Las clases de servicio de lenguaje de MPF supone la presencia al menos de la clase base de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  
  
### Ejemplo  
 En este ejemplo se muestra una implementación típica del método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> .  este ejemplo utiliza la clase base de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  
  
```c#  
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
  
## método de GetScanner  
 Este método devuelve una instancia de un objeto de <xref:Microsoft.VisualStudio.Package.IScanner> que implementa un analizador o un escáner línea\-orientado utilizado para obtener tokens y sus tipos y desencadenadores.  Este escáner se utiliza en la clase de <xref:Microsoft.VisualStudio.Package.Colorizer> para el color aunque el escáner se puede utilizar para obtener tipos y desencadenadores simbólicos como preludio a una operación más compleja de análisis.  Debe proporcionar la clase que implementa la interfaz de <xref:Microsoft.VisualStudio.Package.IScanner> y debe implementar todos los métodos de la interfaz de <xref:Microsoft.VisualStudio.Package.IScanner> .  
  
### Ejemplo  
 En este ejemplo se muestra una implementación típica del método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> .  La clase de `TestScanner` implementa la interfaz de <xref:Microsoft.VisualStudio.Package.IScanner> \(no se muestra\).  
  
```c#  
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
  
## método de ParseSource  
 Analiza el archivo de código fuente por varias razones.  Este método recibe un objeto de <xref:Microsoft.VisualStudio.Package.ParseRequest> que describa lo esperado de una operación determinada de análisis.  El método de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> invoca un analizador más complejo que determine la funcionalidad y el ámbito de token.  El método de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> se utiliza en compatibilidad con las operaciones de IntelliSense así como de la concordancia de.  Aunque no admite operaciones avanzadas, todavía debe devolver un objeto válido de <xref:Microsoft.VisualStudio.Package.AuthoringScope> y que requiere crear una clase que implemente la interfaz de <xref:Microsoft.VisualStudio.Package.AuthoringScope> e implementar todos los métodos de la interfaz.  Puede devolver valores nulos de todos los métodos pero el propio objeto de <xref:Microsoft.VisualStudio.Package.AuthoringScope> no debe ser un valor NULL.  
  
### Ejemplo  
 En este ejemplo se muestra una implementación mínima del método de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> y la clase de <xref:Microsoft.VisualStudio.Package.AuthoringScope> , suficiente para permitir que el servicio de lenguaje compile y ejecute realmente admitir características más avanzadas cualquiera de los.  
  
```c#  
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
  
## propiedad Name  
 Esta propiedad devuelve el nombre del servicio de lenguaje.  Éste debe ser el mismo nombre determinado cuando el servicio de lenguaje se registró.  Este nombre se utiliza en varios lugares, el más prominente es la clase de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> donde el nombre se utiliza para tener acceso al registro.  El nombre devuelto por esta propiedad no debe localizar mientras se utiliza en el registro de la entrada del Registro y los nombres de clave.  
  
### Ejemplo  
 En este ejemplo se muestra una posible implementación de la propiedad de <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> .  Observe que el nombre aquí se pone en el código: el nombre real se debe obtener de un archivo de recursos para que pueda ser utilizado en registrar un servicio de \(vea [Registrar un servicio de lenguaje](../../extensibility/internals/registering-a-legacy-language-service1.md)\).  
  
```c#  
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
  
## Crear instancias de clases personalizadas  
 Los siguientes métodos en clases especificadas se pueden invalidar para proporcionar las instancias de dispone de versiones de cada clase.  
  
### en la clase de LanguageService  
  
|Método|clase devuelta|Descripción|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|para admitir adiciones personalizadas a la vista de texto.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Para admitir propiedades personalizadas.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|para admitir **Barra de navegación**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Para admitir funciones en plantillas de fragmento de código.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Para admitir los fragmentos de código \(este método no se invalida normalmente\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Para admitir la personalización de la estructura de <xref:Microsoft.VisualStudio.Package.ParseRequest> \(este método no se invalida normalmente\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Para admitir el código fuente de formato, especificando los caracteres de comentario, y personalizar las firmas de método.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Para admitir comandos de menú.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Para admitir el resaltado de la sintaxis \(este método no se invalida normalmente\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|para admitir el acceso a las preferencias de idioma.  este método se debe implementar pero puede devolver una instancia de la clase base.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Para proporcionar un analizador utilizado para identificar tipos de tokens en una línea.  Este método debe ser implementado y <xref:Microsoft.VisualStudio.Package.IScanner> debe derivarse de.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|para proporcionar un analizador utilizado para identificar funcionalidad y ámbito en un archivo de código fuente completo.  Este método se debe implementar y debe devolver una instancia de la clase de <xref:Microsoft.VisualStudio.Package.AuthoringScope> .  Si todo lo que desea admitir es el resaltado de sintaxis \(que requiere el analizador de <xref:Microsoft.VisualStudio.Package.IScanner> devuelto del método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> \), no puede hacer nada en este método distinto de retorno una versión de los métodos de la clase de <xref:Microsoft.VisualStudio.Package.AuthoringScope> cuyos todos los valores nulos return.|  
  
### En la clase de origen  
  
|Método|clase devuelta|Descripción|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Para personalizar la presentación de las listas de finalización de IntelliSense \(este método no se invalida normalmente\).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Para admitir a los marcadores de la lista de tareas de la lista de errores; específicamente, compatibilidad con las características más allá de abrir el archivo y de saltar a la línea que produjo el error.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Para personalizar la presentación de información sobre herramientas de la información de parámetros de IntelliSense.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|para admitir código de comentario.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Para recopilar información durante la operación de análisis.|  
  
### en la clase de AuthoringScope  
  
|Método|clase devuelta|Descripción|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Proporciona una lista de declaraciones como miembros o tipos.  Este método se debe implementar pero puede devolver un valor NULL.  Si este método devuelve un objeto válido, el objeto debe ser una instancia de la clase de <xref:Microsoft.VisualStudio.Package.Declarations> .|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Proporciona una lista de firmas de método para un contexto especificado.  Este método se debe implementar pero puede devolver un valor NULL.  Si este método devuelve un objeto válido, el objeto debe ser una instancia de la clase de <xref:Microsoft.VisualStudio.Package.Methods> .|  
  
## Imágenes del servicio de lenguaje  
 Para proporcionar una lista de iconos que se utilizarán en el servicio de lenguaje, invalide el método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> en la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> y devuelve <xref:System.Windows.Forms.ImageList> que contiene iconos.  Las cargas de clase bases de <xref:Microsoft.VisualStudio.Package.LanguageService> un conjunto predeterminado de iconos.  Puesto que especifica el índice exacto de la imagen en esos lugares que necesitan iconos, cómo se organiza posee la lista de imágenes depende plenamente para usted.  
  
### imágenes utilizadas en las listas de finalización de IntelliSense  
 Para las listas de finalización de IntelliSense, el índice de la imagen se especifica para cada elemento del método de <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> de la clase de <xref:Microsoft.VisualStudio.Package.Declarations> , que debe reemplazar si desea proporcionar un índice de la imagen.  El valor devuelto del método de <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> es un índice en la lista de imágenes proporcionada al constructor de clase de <xref:Microsoft.VisualStudio.Package.CompletionSet> y es la misma lista de imágenes devuelto del método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> en la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> \(puede cambiar que lista de imagen a utilizar para <xref:Microsoft.VisualStudio.Package.CompletionSet> si reemplaza el método de <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> en la clase de <xref:Microsoft.VisualStudio.Package.Source> para proporcionar otra imagen lista\).  
  
### imágenes utilizadas en la barra de navegación  
 **Barra de navegación** muestra listas de tipos y miembros y se utiliza para la navegación rápida puede mostrar iconos.  Estos iconos se obtienen del método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> en la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> y no se pueden reemplazar específicamente para **Barra de navegación**.  Los índices utilizados para cada elemento en los cuadros combinados se especifica cuando las listas que representan los cuadros combinados se completan el método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> en la clase de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> \(vea [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)\).  Estos índices de imagen se obtienen de algún modo del analizador, normalmente a través de la versión de la clase de <xref:Microsoft.VisualStudio.Package.Declarations> .  Cómo se recopilan los índices depende plenamente para usted.  
  
### imágenes utilizadas en la ventana de la tarea de la lista de errores  
 Siempre que el analizador del método de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(vea [Escáneres y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)\) encuentra un error y pase ese error al método de <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> en la clase de <xref:Microsoft.VisualStudio.Package.AuthoringSink> , el error se notifica en la ventana de la tarea de **Lista de errores** .  Un icono puede estar asociado a cada elemento que aparece en la ventana de tarea y que aprovechan el icono de la misma lista de imágenes devuelto del método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> en la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> .  el comportamiento predeterminado de las clases de MPF es no mostrar una imagen con el mensaje de error.  Sin embargo, puede invalidar este comportamiento derivando una clase de la clase de <xref:Microsoft.VisualStudio.Package.Source> e invalidando el método de <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> .  En ese método, se crea un nuevo objeto de <xref:Microsoft.VisualStudio.Package.DocumentTask> .  Antes de devolver ese objeto, puede utilizar la propiedad de <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> en el objeto de <xref:Microsoft.VisualStudio.Package.DocumentTask> para establecer el índice de la imagen.  Esto será similar al ejemplo siguiente.  Observe que `TestIconImageIndex` es una enumeración que enumera todos los iconos y es específico para este ejemplo.  Puede tener una forma diferente de identificar iconos en el servicio de lenguaje.  
  
```c#  
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
  
## La Imagen predeterminado enumerado para un lenguaje Service  
 La lista predeterminada de imagen proporcionada con las clases de servicio de lenguaje de base MPF contiene varios iconos asociados con los elementos del lenguaje más comunes.  La mayor parte de estos iconos se organizan en conjuntos de seis variaciones, correspondientes a los conceptos de acceso de public, internal, de confianza, protegido, de private, y de acceso directo.  Por ejemplo, puede hacer iconos diferentes para un método dependiendo de si es público, proteger o private.  
  
 La siguiente enumeración especifica los nombres comunes de cada icono establecido y especifica el índice asociado.  Por ejemplo, en función de la enumeración, puede especificar el índice de la imagen de un método protegido como `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`.  Puede cambiar los nombres en esta enumeración como desee.  
  
```c#  
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
  
## Vea también  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)   
 [Registrar un servicio de lenguaje](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Escáneres y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)