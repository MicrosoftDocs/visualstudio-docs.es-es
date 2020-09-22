---
title: Coincidencia de llaves en un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d6d7243c8032b22f9abe89021af138f638729011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842462"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Coincidencia de llaves en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La coincidencia de llaves ayuda al desarrollador a realizar un seguimiento de los elementos del lenguaje que deben aparecer juntos, como paréntesis y llaves. Cuando un desarrollador escribe una llave de cierre, se resalta la llave de apertura.  
  
 Puede hacer coincidir dos o tres elementos coincidentes, denominados pares y triples. Los triples son conjuntos de tres elementos coexistentes. Por ejemplo, en C#, la `foreach` instrucción forma tres: " `foreach()` ", " `{` " y " `}` ". Los tres elementos se resaltan cuando se escribe la llave de cierre.  
  
 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar la coincidencia de llaves, vea [Tutorial: Mostrar llaves coincidentes](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.  
  
 La <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase admite pares y triples con los <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> métodos y <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> .  
  
## <a name="implementation"></a>Implementación  
 El servicio de lenguaje debe identificar todos los elementos coincidentes en el idioma y, a continuación, buscar todos los pares coincidentes. Esto se logra normalmente implementando <xref:Microsoft.VisualStudio.Package.IScanner> para detectar un lenguaje coincidente y usando después el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método para buscar coincidencias con los elementos.  
  
 El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método llama al escáner para acortar la línea y devolver el token justo delante del símbolo de intercalación. El analizador indica que se ha encontrado un par de elementos de lenguaje mediante el establecimiento de un valor de desencadenador de tokens de <xref:Microsoft.VisualStudio.Package.TokenTriggers> en el token actual. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método llama al <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método que, a su vez, llama al <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> método con el valor de la razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> para buscar el elemento de lenguaje coincidente. Cuando se encuentra el elemento de lenguaje coincidente, ambos elementos se resaltan.  
  
 Para obtener una descripción completa de cómo al escribir una llave se activa el resaltado de llaves, consulte la sección "operación de análisis de ejemplo" en el tema [analizador y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Habilitar la compatibilidad con la coincidencia de llaves  
 El <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo puede establecer los `MatchBraces` `MatchBracesAtCaret` `ShowMatchingBrace` parámetros con nombre, y que establecen las propiedades correspondientes de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase. El usuario también puede establecer las propiedades de preferencias de idioma.  
  
|Entrada del Registro|Propiedad|Descripción|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Habilita la coincidencia de llaves|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Habilita la coincidencia de llaves a medida que se mueve el símbolo de intercalación.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Resalta la llave correspondiente.|  
  
## <a name="matching-conditional-statements"></a>Instrucciones condicionales coincidentes  
 Puede hacer coincidir las instrucciones condicionales, como `if` , `else if` y `else` , o `#if` , `#elif` ,, `#else` `#endif` , de la misma manera que los delimitadores coincidentes. Puede subclaser la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase y proporcionar un método que pueda agregar intervalos de texto y delimitadores a la matriz interna de elementos coincidentes.  
  
## <a name="setting-the-trigger"></a>Establecer el desencadenador  
 En el ejemplo siguiente se muestra cómo detectar paréntesis coincidentes, llaves y corchetes, y cómo establecer el desencadenador en el escáner. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método de la <xref:Microsoft.VisualStudio.Package.Source> clase detecta el desencadenador y llama al analizador para encontrar el par coincidente (consulte la sección "buscar la coincidencia" de este tema). Este ejemplo se utiliza únicamente con fines ilustrativos. Se supone que el escáner contiene un método `GetNextToken` que identifica y devuelve tokens de una línea de texto.  
  
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
  
## <a name="matching-the-braces"></a>Coincidencia de llaves  
 Este es un ejemplo simplificado para hacer coincidir los elementos del lenguaje {}, () y [], y agregar sus intervalos al <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto. Este enfoque no es un enfoque recomendado para analizar código fuente. solo es para fines ilustrativos.  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)   
 [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
