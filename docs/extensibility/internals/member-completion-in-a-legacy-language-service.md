---
title: Finalizaciones de miembros en un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56ad09f2b158c7d23bf40bbafbdba3a9435926e4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948393"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Finalización de miembros en un servicio de lenguaje heredado

La finalización de miembros de IntelliSense es una información sobre herramientas que muestra una lista de posibles miembros de un ámbito determinado, como una clase, estructura, enumeración o espacio de nombres. Por ejemplo, en C#, si el usuario escribe "this" seguido por un punto, se presenta una lista de todos los miembros de la clase o estructura en el ámbito actual en una lista desde el que el usuario puede seleccionar.

Managed package framework (MPF) proporciona compatibilidad con la información sobre herramientas y la administración de la lista en la información sobre herramientas; todo lo que se necesita es la cooperación del analizador para suministrar los datos que aparecen en la lista.

Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información, consulte [ampliación del Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.

## <a name="how-it-works"></a>Cómo funciona

Éstas son las dos maneras en que se muestra una lista de miembros mediante las clases MPF:

- Colocar el símbolo de intercalación en un identificador o después de un carácter de finalización de miembro y seleccionando **lista de miembros** desde el **IntelliSense** menú.

- El <xref:Microsoft.VisualStudio.Package.IScanner> analizador detecta un carácter de finalización de miembros y establece un token de desencadenador de [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) para ese carácter.

Un carácter de finalización de miembro indica que un miembro de una clase, estructura o enumeración es seguir. Por ejemplo, en C# o Visual Basic, el carácter de finalización de miembro es un `.`, mientras que en C++ el carácter es un `.` o `->`. El valor del desencadenador se establece cuando se analiza el carácter de selección de miembro.

### <a name="the-intellisense-member-list-command"></a>El comando de la lista de miembros de IntelliSense

El <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando inicia una llamada a la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método en el <xref:Microsoft.VisualStudio.Package.Source> clase y el <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método, a su vez, llama a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador de método con el motivo de análisis de [ParseReason.DisplayMemberList ](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

El analizador determina el contexto de la posición actual, así como el token bajo o inmediatamente antes de la posición actual. Según este token, se presenta una lista de declaraciones. Por ejemplo, en C#, si coloca el símbolo de intercalación en un miembro de clase y seleccione **lista de miembros**, obtendrá una lista de todos los miembros de la clase. Si coloca el símbolo de intercalación después del punto que sigue a una variable de objeto, obtener una lista de todos los miembros de la clase que el objeto representa. Tenga en cuenta que si el símbolo de intercalación se coloca en un miembro cuando se muestra la lista de miembros, al seleccionar a un miembro de la lista reemplaza al miembro que está el símbolo de intercalación con el que aparece en la lista.

### <a name="the-token-trigger"></a>El Token de desencadenador

El [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) desencadenador inicia una llamada a la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método en el <xref:Microsoft.VisualStudio.Package.Source> clase y el <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método, llama a su vez, el analizador con el motivo de análisis de [ ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Si el token desencadenador también incluye el [TokenTriggers.MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) marca, el motivo por el análisis es [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), que combina la selección de miembros y el resaltado de llaves .

El analizador determina el contexto de la actual posición, así como lo escribió antes de que el miembro seleccionar carácter. De esta información, el analizador crea una lista de todos los miembros del ámbito solicitado. Esta lista de declaraciones se almacena en el <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto que se devuelve desde el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método. Si se devuelven todas las declaraciones, se muestra la información sobre herramientas de finalización de miembros. La información sobre herramientas está administrado por una instancia de la <xref:Microsoft.VisualStudio.Package.CompletionSet> clase.

## <a name="enable-support-for-member-completion"></a>Habilitar la compatibilidad de finalizaciones de miembros

Debe tener el `CodeSense` entrada del registro se establece en 1 para admitir cualquier operación de IntelliSense. Esta entrada del registro se puede establecer con un parámetro con nombre pasado a la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo de usuario asociado con el paquete de idioma. Las clases de servicio de lenguaje leer el valor de esta entrada del registro desde el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad en el <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.

Si el escáner devuelve el token de desencadenador de [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)y el analizador devuelve una lista de declaraciones, a continuación, se muestra la lista de finalización de miembros.

## <a name="support-member-completion-in-the-scanner"></a>Admite la finalización de miembros en el analizador

El analizador debe ser capaz de detectar un carácter de finalización de miembros y establezca el desencadenador de token [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) cuando se analiza ese carácter.

### <a name="scanner-example"></a>Ejemplo de analizador

Este es un ejemplo simplificado de detectar el carácter de finalización de miembros y la correspondiente <xref:Microsoft.VisualStudio.Package.TokenTriggers> marca. En este ejemplo es solo con fines ilustrativos. Supone que el escáner contiene un método `GetNextToken` que identifica y devuelve los tokens de una línea de texto. El código de ejemplo simplemente establece el desencadenador cada vez que detecta el tipo correcto de caracteres.

```csharp
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

## <a name="support-member-completion-in-the-parser"></a>Admite la finalización de miembros en el analizador

Para la finalización de miembro, el <xref:Microsoft.VisualStudio.Package.Source> clase llama a la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método. Debe implementar la lista en una clase que se deriva el <xref:Microsoft.VisualStudio.Package.Declarations> clase. Consulte la <xref:Microsoft.VisualStudio.Package.Declarations> clase para obtener más información acerca de los métodos que debe implementar.

El analizador se denomina con [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) o [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) cuando se escribe un carácter de selección de miembro. La ubicación proporcionada el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto es inmediatamente después de que el miembro seleccionar carácter. El analizador debe recopilar los nombres de todos los miembros que pueden aparecer en una lista de miembros en ese momento determinado en el código fuente. A continuación, el analizador debe analizar la línea actual para determinar el ámbito que el usuario desea asociado al carácter de selección de miembro.

Este ámbito se basa en el tipo del identificador antes de que el miembro seleccionar carácter. Por ejemplo, en C#, dada la variable miembro `languageService` que tiene un tipo de `LanguageService`, escriba **languageService.** genera una lista de todos los miembros de la `LanguageService` clase. También en C#, escriba **esto.** genera una lista de todos los miembros de la clase en el ámbito actual.

### <a name="parser-example"></a>Ejemplo de analizador

El ejemplo siguiente muestra una forma de rellenar un <xref:Microsoft.VisualStudio.Package.Declarations> lista. Este código supone que el analizador crea una declaración y lo agrega a la lista mediante una llamada a un `AddDeclaration` método en el `TestAuthoringScope` clase.

```csharp
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