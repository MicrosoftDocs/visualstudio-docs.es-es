---
title: Finalización de miembros en un servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre cómo funciona la información sobre herramientas de finalización de miembros de IntelliSense en un servicio de lenguaje heredado y cómo es compatible con Managed Package Framework (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5279b3a96cb9658b968a5d51bbd8b1c2a41862b6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095139"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Finalización de miembros en un servicio de lenguaje heredado

La finalización de los miembros de IntelliSense es una información sobre herramientas que muestra una lista de los miembros posibles de un ámbito determinado, como una clase, estructura, enumeración o espacio de nombres. Por ejemplo, en C#, si el usuario escribe "this" seguido de un punto, se muestra una lista de todos los miembros de la clase o estructura en el ámbito actual en una lista de la que el usuario puede seleccionar.

Managed Package Framework (MPF) proporciona compatibilidad para la información sobre herramientas y la administración de la lista en la información sobre herramientas. todo lo que se necesita es la cooperación desde el analizador para proporcionar los datos que aparecen en la lista.

Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información, vea [extender el editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="how-it-works"></a>Cómo funciona

A continuación se muestran las dos formas en las que se muestra una lista de miembros mediante las clases MPF:

- Colocar el símbolo de intercalación en un identificador o después de un carácter de finalización de miembro y seleccionar **los miembros** de la lista en el menú de **IntelliSense** .

- El <xref:Microsoft.VisualStudio.Package.IScanner> analizador detecta un carácter de finalización de miembro y establece un desencadenador de token de [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) para ese carácter.

Un carácter de finalización de miembro indica que debe seguir un miembro de una clase, estructura o enumeración. Por ejemplo, en C# o Visual Basic el carácter de finalización de miembro es un `.` , mientras que en C++ el carácter es `.` o `->` . El valor del desencadenador se establece cuando se examina el carácter de selección de miembro.

### <a name="the-intellisense-member-list-command"></a>Comando de lista de miembros de IntelliSense

El <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando inicia una llamada al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase y <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> , a su vez, llama al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador de métodos con el motivo de análisis de [ParseReason. DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

El analizador determina el contexto de la posición actual, así como el token situado debajo o inmediatamente anterior a la posición actual. En función de este token, se presenta una lista de declaraciones. Por ejemplo, en C#, si coloca el símbolo de intercalación en un miembro de clase y selecciona **lista de miembros**, obtendrá una lista de todos los miembros de la clase. Si coloca el símbolo de intercalación después de un punto que sigue a una variable de objeto, obtendrá una lista de todos los miembros de la clase que representa el objeto. Tenga en cuenta que si el símbolo de intercalación se coloca en un miembro cuando se muestra la lista de miembros, al seleccionar un miembro de la lista se reemplaza el miembro en el que se encuentra el símbolo de intercalación con el de la lista.

### <a name="the-token-trigger"></a>Desencadenador de token

El desencadenador [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) inicia una llamada al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase y el <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método, a su vez, llama al analizador con el motivo de análisis de [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Si el desencadenador de token también incluye la marca [TokenTriggers. MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) , el motivo de análisis es [ParseReason. MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), que combina la selección de miembros y el resaltado de llaves.

El analizador determina el contexto de la posición actual, así como lo que se ha escrito antes del carácter de selección de miembro. A partir de esta información, el analizador crea una lista de todos los miembros del ámbito solicitado. Esta lista de declaraciones se almacena en el <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto que se devuelve desde el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método. Si se devuelven declaraciones, se muestra la información sobre herramientas de finalización de miembros. La información sobre herramientas está administrada por una instancia de la <xref:Microsoft.VisualStudio.Package.CompletionSet> clase.

## <a name="enable-support-for-member-completion"></a>Habilitar la compatibilidad con la finalización de miembros

Debe tener la `CodeSense` entrada del registro establecida en 1 para admitir cualquier operación de IntelliSense. Esta entrada del registro se puede establecer con un parámetro con nombre que se pasa al <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo de usuario asociado al paquete de idioma. Las clases del servicio de lenguaje leen el valor de esta entrada del registro de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad en la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.

Si el escáner devuelve el desencadenador de token de [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)y el analizador devuelve una lista de declaraciones, se muestra la lista de finalización de miembros.

## <a name="support-member-completion-in-the-scanner"></a>Compatibilidad con la finalización de miembros en el escáner

El escáner debe ser capaz de detectar un carácter de finalización de miembro y establecer el desencadenador de token de [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) cuando se analiza ese carácter.

### <a name="scanner-example"></a>Ejemplo de escáner

Este es un ejemplo simplificado de la detección del carácter de finalización de miembro y el establecimiento de la <xref:Microsoft.VisualStudio.Package.TokenTriggers> marca adecuada. Este ejemplo se utiliza únicamente con fines ilustrativos. Se supone que el escáner contiene un método `GetNextToken` que identifica y devuelve tokens de una línea de texto. El código de ejemplo simplemente establece el desencadenador cada vez que ve el tipo de carácter correcto.

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

## <a name="support-member-completion-in-the-parser"></a>Compatibilidad con la finalización de miembros en el analizador

Para la finalización de miembros, la <xref:Microsoft.VisualStudio.Package.Source> clase llama al <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método. Debe implementar la lista en una clase que se deriva de la <xref:Microsoft.VisualStudio.Package.Declarations> clase. Vea la <xref:Microsoft.VisualStudio.Package.Declarations> clase para obtener más información sobre los métodos que debe implementar.

Se llama al analizador con [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) o [ParseReason. MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) cuando se escribe un carácter de selección de miembro. La ubicación especificada en el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto está inmediatamente después del carácter de selección de miembro. El analizador debe recopilar los nombres de todos los miembros que pueden aparecer en una lista de miembros en ese punto concreto del código fuente. Después, el analizador debe analizar la línea actual para determinar el ámbito que el usuario desea asociar con el carácter de selección de miembro.

Este ámbito se basa en el tipo del identificador antes del carácter de selección de miembro. Por ejemplo, en C#, dada la variable miembro `languageService` que tiene un tipo de `LanguageService` , escribiendo **languageService.** genera una lista de todos los miembros de la `LanguageService` clase. También en C#, escribiendo **esto.** genera una lista de todos los miembros de la clase en el ámbito actual.

### <a name="parser-example"></a>Ejemplo de analizador

En el ejemplo siguiente se muestra una manera de rellenar una <xref:Microsoft.VisualStudio.Package.Declarations> lista. En este código se supone que el analizador crea una declaración y la agrega a la lista llamando a un `AddDeclaration` método en la `TestAuthoringScope` clase.

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
