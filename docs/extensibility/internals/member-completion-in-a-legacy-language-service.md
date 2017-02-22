---
title: "Finalizaci&#243;n de miembro en un servicio de lenguaje heredado | Microsoft Docs"
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
  - "IntelliSense, información sobre herramientas de finalización de miembro"
  - "Finalización de miembro, los auxiliares en servicios de lenguaje [managed package framework]"
  - "Servicios de lenguaje [managed package framework], miembro de finalización de IntelliSense"
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Finalizaci&#243;n de miembro en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La finalización de IntelliSense miembro es una información sobre herramientas que muestra una lista de posibles miembros de un ámbito determinado, como una clase, estructura, enumeración o espacio de nombres. Por ejemplo, en C\#, si el usuario escribe "this" seguido por un punto, se presenta una lista de todos los miembros de la clase o estructura en el ámbito actual en una lista desde la que el usuario puede seleccionar.  
  
 El marco de trabajo de paquete administrado \(MPF\) proporciona compatibilidad con la información sobre herramientas y la administración de la lista en la información sobre herramientas; todo lo que se necesita es la cooperación del analizador para proporcionar los datos que aparecen en la lista.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Extender el Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## ¿Cómo funciona?  
 Éstas son las dos maneras en que se muestra una lista de miembros utilizando las clases MPF:  
  
-   Colocar el símbolo de intercalación en el identificador o después de un carácter de terminación de miembro y seleccionando **lista de miembros** desde el **IntelliSense** menú.  
  
-   El <xref:Microsoft.VisualStudio.Package.IScanner> analizador detecta un carácter de terminación de miembro y establece un desencadenador de token de <xref:Microsoft.VisualStudio.Package.TokenTriggers> para ese carácter.  
  
 Un carácter de terminación de miembro indica que un miembro de una clase, estructura o enumeración es seguir. Por ejemplo, en C\# o Visual Basic, el carácter de finalización de miembro es una `.`, mientras que en C\+\+ el carácter es un `.` o un `->`. El valor del desencadenador se establece cuando se examina el carácter de selección de miembro.  
  
### El comando de la lista de miembros de IntelliSense  
 El <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando inicia una llamada a la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase y <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método, a su vez, llama la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analizador de método con la razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 El analizador determina el contexto de la posición actual, así como el token en o inmediatamente antes de la posición actual. Según este token, se presenta una lista de declaraciones. Por ejemplo, en C\#, si coloca el símbolo de intercalación en un miembro de clase y seleccione **lista de miembros**, obtendrá una lista de todos los miembros de la clase. Si coloca el símbolo de intercalación después del punto que sigue a una variable de objeto, obtendrá una lista de todos los miembros de la clase que el objeto representa. Tenga en cuenta que si el símbolo de intercalación se coloca en un miembro cuando se muestra la lista de miembros, seleccione a un miembro de la lista reemplaza al miembro que está el símbolo de intercalación con uno de la lista.  
  
### El desencadenador de Token  
 El <xref:Microsoft.VisualStudio.Package.TokenTriggers> desencadenador inicia una llamada a la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método en el <xref:Microsoft.VisualStudio.Package.Source> clase y el <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método, a su vez, llama el analizador con el motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> \(si el desencadenador de token también incluye el <xref:Microsoft.VisualStudio.Package.TokenTriggers> marca, el motivo de análisis es <xref:Microsoft.VisualStudio.Package.ParseReason> que combina la selección de miembros y resaltado de llaves\).  
  
 El analizador determina el contexto de la actual posición, así como lo ha escrito antes de que el miembro seleccione caracteres. De esta información, el analizador crea una lista de todos los miembros del ámbito solicitado. Esta lista de declaraciones se almacena en la <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto devuelto desde el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método. Si se devuelven todas las declaraciones, se muestra la información sobre herramientas de finalización de miembro. La información sobre herramientas está administrado por una instancia de la <xref:Microsoft.VisualStudio.Package.CompletionSet> clase.  
  
## Habilitar la compatibilidad para la finalización de miembro  
 Debe tener el `CodeSense` entrada del registro se establece en 1 para admitir cualquier operación de IntelliSense. Esta entrada del registro se puede establecer con un parámetro con nombre que se pasa a la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo de usuario asociado con el paquete de idioma. Las clases de servicio de lenguaje leen el valor de esta entrada del registro desde el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad en la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.  
  
 Si el escáner devuelve el desencadenador de token de <xref:Microsoft.VisualStudio.Package.TokenTriggers>, y el analizador devuelve una lista de declaraciones, a continuación, se muestra la lista de finalización de miembro.  
  
## Finalización de miembros auxiliares en el escáner  
 El analizador debe ser capaz de detectar un carácter de terminación de miembro y establezca el desencadenador de token <xref:Microsoft.VisualStudio.Package.TokenTriggers> al analizar ese carácter.  
  
### Ejemplo  
 Este es un ejemplo simplificado de detectar el carácter de terminación de miembro y la correspondiente <xref:Microsoft.VisualStudio.Package.TokenTriggers> marca. En este ejemplo es sólo con fines ilustrativos. Se supone que el escáner contiene un método `GetNextToken` que identifica y devuelve símbolos \(tokens\) de una línea de texto. El código de ejemplo simplemente establece el desencadenador cada vez que detecta el tipo de carácter.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## Finalización de miembros auxiliares en el analizador  
 Finalización de miembro, la <xref:Microsoft.VisualStudio.Package.Source> clase llamadas el <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método. La lista debe implementar en una clase que se deriva la <xref:Microsoft.VisualStudio.Package.Declarations> clase. Consulte la <xref:Microsoft.VisualStudio.Package.Declarations> clase para obtener más información acerca de los métodos que debe implementar.  
  
 El analizador se denomina con <xref:Microsoft.VisualStudio.Package.ParseReason> o <xref:Microsoft.VisualStudio.Package.ParseReason> cuando se escribe un carácter de selección de miembro. La ubicación en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto es inmediatamente después de que el miembro seleccione caracteres. El analizador debe recopilar los nombres de todos los miembros que pueden aparecer en una lista de miembros en ese momento determinado en el código fuente. A continuación, el analizador debe analizar la línea actual para determinar el alcance que el usuario desea asociado con el carácter de selección de miembro.  
  
 Este ámbito se basa en el tipo del identificador para el miembro seleccionar caracteres. Por ejemplo, en C\#, dada la variable miembro `languageService` que tiene un tipo de `LanguageService`, escriba **languageService.** genera una lista de todos los miembros de la `LanguageService` clase. También en C\#, escriba **esto.** genera una lista de todos los miembros de la clase en el ámbito actual.  
  
### Ejemplo  
 En el ejemplo siguiente se muestra una forma de rellenar un <xref:Microsoft.VisualStudio.Package.Declarations> lista. Este código supone que el analizador crea una declaración y lo agrega a la lista mediante una llamada a un `AddDeclaration` método en la `TestAuthoringScope` clase.  
  
```c#  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```