---
title: Coincidencia de llaves en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709818"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Coincidencia de llaves en un servicio de lenguaje heredado
La coincidencia de llaves ayuda al desarrollador a realizar un seguimiento de los elementos del lenguaje que deben producirse juntos, como paréntesis y llaves. Cuando un desarrollador introduce una llave de cierre, se resalta la llave de apertura.

 Puede hacer coincidir dos o tres elementos co-ocurrentes, llamados pares y triples. Los triples son conjuntos de tres elementos co-ocurrentes. Por ejemplo, en C-, `foreach` la `foreach()`instrucción forma un triple: , `{`, y `}`. Los tres elementos se resaltan cuando se escribe la llave de cierre.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva forma de implementar la coincidencia de llaves, consulte [Tutorial: Mostrar llaves coincidentes](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

 La <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase admite pares y <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> triples con los métodos y. <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A>

## <a name="implementation"></a>Implementación
 El servicio de lenguaje debe identificar todos los elementos coincidentes en el idioma y, a continuación, buscar todos los pares coincidentes. Esto se logra normalmente mediante la implementación <xref:Microsoft.VisualStudio.Package.IScanner> para <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> detectar un idioma coincidente y, a continuación, usar el método para que coincida con los elementos.

 El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método llama al analizador para tokenizar la línea y devolver el token justo antes del símbolo de intercalación. El analizador indica que se ha encontrado un par de <xref:Microsoft.VisualStudio.Package.TokenTriggers> elementos de lenguaje estableciendo un valor de desencadenador de token en el token actual. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> llama al método <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> que a su vez <xref:Microsoft.VisualStudio.Package.ParseReason> llama al método con el valor de motivo de análisis de para buscar el elemento de lenguaje coincidente. Cuando se encuentra el elemento de idioma coincidente, ambos elementos se resaltan.

 Para obtener una descripción completa de cómo escribir una llave desencadena el resaltado de llaves, consulte la sección Ejemplo de *operación* de análisis en el artículo Analizador y analizador de servicios de [lenguaje heredados](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Habilite la compatibilidad con la coincidencia de llaves
 El <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo puede establecer las entradas del Registro **MatchBraces**, **MatchBracesAtCaret**y <xref:Microsoft.VisualStudio.Package.LanguagePreferences> **ShowMatchingBrace** que establecen las propiedades correspondientes de la clase. El usuario también puede establecer las propiedades de preferencia de idioma.

|Entrada del Registro|Propiedad|Descripción|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Habilita la coincidencia de llaves.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Permite la coincidencia de llaves a medida que se mueve el intercalador.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Resalta la llave correspondiente.|

## <a name="match-conditional-statements"></a>Coincidir con las declaraciones condicionales
 Puede hacer coincidir instrucciones condicionales, `if`como , `else if`, y `else` `#if`, o , `#elif`, `#else`, `#endif`, , de la misma manera que los delimitadores coincidentes. Puede subclase <xref:Microsoft.VisualStudio.Package.AuthoringSink> de la clase y proporcionar un método que puede agregar intervalos de texto, así como delimitadores a la matriz interna de elementos coincidentes.

## <a name="set-the-trigger"></a>Ajuste el gatillo
 En el ejemplo siguiente se muestra cómo detectar paréntesis coincidentes, llaves y llaves cuadradas, y establecer el desencadenador para él en el escáner. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método <xref:Microsoft.VisualStudio.Package.Source> de la clase detecta el desencadenador y llama al analizador para buscar el par coincidente (consulte la sección *Buscar la coincidencia* en este artículo). Este ejemplo es solo para fines ilustrativos. Se supone que el analizador `GetNextToken` contiene un método que identifica y devuelve tokens de una línea de texto.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Coincide con los frenos
 Este es un ejemplo simplificado `{ }`para `( )`hacer `[ ]`coincidir los elementos <xref:Microsoft.VisualStudio.Package.AuthoringSink> de lenguaje , , y , y agregar sus intervalos al objeto. Este enfoque no es un enfoque recomendado para analizar el código fuente; es sólo para fines ilustrativos.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>Vea también
- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)
- [Analizador y analizador de servicios de lenguaje heredados](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
