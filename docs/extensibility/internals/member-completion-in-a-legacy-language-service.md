---
title: Finalización de miembros en un servicio de idiomas heredados Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707193"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Finalización de miembros en un servicio de lenguaje heredado

La finalización de miembros de IntelliSense es una información sobre herramientas que muestra una lista de posibles miembros de un ámbito determinado, como una clase, estructura, enumeración o espacio de nombres. Por ejemplo, en C-, si el usuario escribe "this" seguido de un punto, se presenta una lista de todos los miembros de la clase o estructura en el ámbito actual en una lista desde la que el usuario puede seleccionar.

El marco de paquete administrado (MPF) proporciona compatibilidad con la información sobre herramientas y la administración de la lista en la información sobre herramientas; todo lo que se necesita es la cooperación del analizador para proporcionar los datos que aparecen en la lista.

Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Ampliación del editor y](../../extensibility/extending-the-editor-and-language-services.md)los servicios de lenguaje .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="how-it-works"></a>Cómo funciona

Las siguientes son las dos formas en que se muestra una lista de miembros utilizando las clases MPF:

- Colocar el intercalador en un identificador o después de un carácter de finalización de miembro y seleccionar **Miembros** de lista en el menú **IntelliSense.**

- El <xref:Microsoft.VisualStudio.Package.IScanner> analizador detecta un carácter de finalización de miembro y establece un desencadenador de token de [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) para ese carácter.

Un carácter de finalización de miembro indica que un miembro de una clase, estructura o enumeración debe seguir. Por ejemplo, en C o Visual Basic, `.`el carácter de finalización `.` de `->`miembro es un , mientras que en C++el carácter es a o un archivo . El valor del desencadenador se establece cuando se escanea el carácter de selección de miembro.

### <a name="the-intellisense-member-list-command"></a>El comando de lista de miembros de IntelliSense

El <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando inicia una <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> llamada al <xref:Microsoft.VisualStudio.Package.Source> método <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> en la clase y <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> el método, a su vez, llama al analizador de métodos con el motivo de análisis de [ParseReason.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

El analizador determina el contexto de la posición actual, así como el token por debajo o inmediatamente antes de la posición actual. En función de este token, se presenta una lista de declaraciones. Por ejemplo, en C-, si coloca el intercalador en un miembro de clase y selecciona **Miembros**de lista , obtendrá una lista de todos los miembros de la clase. Si coloca el intercalador después de un período que sigue a una variable de objeto, obtendrá una lista de todos los miembros de la clase que representa el objeto. Tenga en cuenta que si el intercalador se coloca en un miembro cuando se muestra la lista de miembros, al seleccionar un miembro de la lista se reemplaza el miembro en el que se encuentra el intercalador por el de la lista.

### <a name="the-token-trigger"></a>El disparador de tokens

El desencadenador [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) inicia una <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> llamada <xref:Microsoft.VisualStudio.Package.Source> al método <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> de la clase y el método, a su vez, llama al analizador con el motivo de análisis de [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Si el desencadenador de token también incluye la marca [TokenTriggers.MatchBraces,](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) el motivo de análisis es [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), que combina la selección de miembros y el resaltado de llaves.

El analizador determina el contexto de la posición actual, así como lo que se ha escrito antes del carácter de selección de miembro. A partir de esta información, el analizador crea una lista de todos los miembros del ámbito solicitado. Esta lista de declaraciones <xref:Microsoft.VisualStudio.Package.AuthoringScope> se almacena en <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> el objeto que se devuelve desde el método. Si se devuelve nifique alguna declaración, se muestra la información sobre la herramienta de finalización de miembros. La información sobre herramientas se <xref:Microsoft.VisualStudio.Package.CompletionSet> administra mediante una instancia de la clase.

## <a name="enable-support-for-member-completion"></a>Habilitar soporte para la finalización de miembros

Debe tener `CodeSense` la entrada del Registro establecida en 1 para admitir cualquier operación de IntelliSense. Esta entrada del Registro se puede establecer <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> con un parámetro con nombre pasado al atributo de usuario asociado al paquete de idioma. Las clases de servicio de lenguaje <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> leen <xref:Microsoft.VisualStudio.Package.LanguagePreferences> el valor de esta entrada del Registro de la propiedad de la clase.

Si el analizador devuelve el desencadenador de token de [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)y el analizador devuelve una lista de declaraciones, se muestra la lista de finalización de miembros.

## <a name="support-member-completion-in-the-scanner"></a>Finalización de miembros de soporte en el escáner

El analizador debe ser capaz de detectar un carácter de finalización de miembro y establecer el desencadenador de token de [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) cuando se analiza ese carácter.

### <a name="scanner-example"></a>Ejemplo de escáner

Este es un ejemplo simplificado de detectar el <xref:Microsoft.VisualStudio.Package.TokenTriggers> carácter de finalización de miembro y establecer la marca adecuada. Este ejemplo es solo para fines ilustrativos. Se supone que el analizador `GetNextToken` contiene un método que identifica y devuelve tokens de una línea de texto. El código de ejemplo simplemente establece el desencadenador cada vez que ve el tipo correcto de carácter.

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

## <a name="support-member-completion-in-the-parser"></a>Finalización de miembros de apoyo en el analizador

Para la finalización del miembro, la <xref:Microsoft.VisualStudio.Package.Source> clase llama al <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método. Debe implementar la lista en una clase <xref:Microsoft.VisualStudio.Package.Declarations> que se deriva de la clase. Consulte <xref:Microsoft.VisualStudio.Package.Declarations> la clase para obtener más información sobre los métodos que debe implementar.

Se llama al analizador con [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) o [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) cuando se escribe un carácter de selección de miembro. La ubicación proporcionada <xref:Microsoft.VisualStudio.Package.ParseRequest> en el objeto es inmediatamente después de que el miembro seleccione el carácter. El analizador debe recopilar los nombres de todos los miembros que pueden aparecer en una lista de miembros en ese punto concreto del código fuente. A continuación, el analizador debe analizar la línea actual para determinar el ámbito que el usuario desea asociar con el carácter de selección de miembro.

Este ámbito se basa en el tipo del identificador antes de que el miembro seleccione el carácter. Por ejemplo, en C-, `languageService` dada la variable `LanguageService`miembro que tiene un tipo de , escribir **languageService.** produce una lista de todos `LanguageService` los miembros de la clase. También en C, escribiendo **esto.** produce una lista de todos los miembros de la clase en el ámbito actual.

### <a name="parser-example"></a>Ejemplo de analizador

En el ejemplo siguiente se <xref:Microsoft.VisualStudio.Package.Declarations> muestra una forma de rellenar una lista. Este código supone que el analizador construye una declaración y la `AddDeclaration` agrega `TestAuthoringScope` a la lista llamando a un método en la clase.

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
