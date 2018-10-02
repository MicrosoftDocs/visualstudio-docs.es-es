---
title: Coincidencia de llaves en un servicio de lenguaje heredado | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3a2267805681b092c7a48537e72e5f0ca0b3ecb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567132"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Coincidencia de llaves en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [coincidencia de llaves en un servicio de lenguaje heredado](https://docs.microsoft.com/visualstudio/extensibility/internals/brace-matching-in-a-legacy-language-service).  
  
Coincidencia de llaves ayuda a los desarrolladores realizar un seguimiento de elementos del lenguaje que deben ocurren juntos, como paréntesis y llaves. Cuando un desarrollador escribe una llave de cierre, se resalta la llave de apertura.  
  
 Puede comparar dos o tres elementos que se producen conjuntamente, denominados pares y triples. Triples son conjuntos de tres elementos que se producen conjuntamente. Por ejemplo, en C#, la `foreach` instrucción forms un triple: "`foreach()`","`{`", y "`}`". Los tres elementos se resaltan cuando se escribe la llave de cierre.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar la coincidencia de llaves, consulte [Tutorial: mostrar las llaves coincidentes](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
 El <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase admite ambos pares y triplica con el <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> y <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> métodos.  
  
## <a name="implementation"></a>Implementación  
 El servicio de lenguaje debe identificar todos los elementos coincidentes en el idioma y, a continuación, busque todos los pares coincidentes. Normalmente, esto se logra implementando <xref:Microsoft.VisualStudio.Package.IScanner> para detectar un idioma coincidente y, a continuación, usar el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método para que coincida con los elementos.  
  
 El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> llamadas de método del analizador para dividir la línea y devolver el token justo antes del símbolo de intercalación. El analizador indica que se ha encontrado un par de elementos de lenguaje estableciendo un valor de token de desencadenador de <xref:Microsoft.VisualStudio.Package.TokenTriggers> en el token actual. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método que llama a su vez la <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> método con el valor de la razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> para localizar el elemento de lenguaje correspondiente. Cuando se encuentra el elemento de lenguaje correspondiente, ambos elementos se resaltan.  
  
 Para obtener una descripción completa de cómo escribir una llave desencadena el resaltado de llaves, consulte la sección "Ejemplo de operación analizar" en el tema [analizador del servicio de lenguaje heredado y el analizador](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Habilitar la compatibilidad para la coincidencia de llaves  
 El <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo puede establecer el `MatchBraces`, `MatchBracesAtCaret`, y `ShowMatchingBrace` parámetros con nombre que se establecen las propiedades correspondientes de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase. También se pueden establecer propiedades de la preferencia de idioma por el usuario.  
  
|Entrada del registro|Property|Descripción|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Habilita la coincidencia de llaves|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Habilita la coincidencia de llaves como el símbolo de intercalación se mueve.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Resalta la llave correspondiente.|  
  
## <a name="matching-conditional-statements"></a>Hacer corresponder las instrucciones condicionales  
 Puede hacer coincidir como instrucciones condicionales, `if`, `else if`, y `else`, o `#if`, `#elif`, `#else`, `#endif`, en la misma manera que la coincidencia de delimitadores. Puede crear subclases el <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase y proporcionar un método que puede agregar texto abarca, así como delimitadores de la matriz interna de elementos coincidentes.  
  
## <a name="setting-the-trigger"></a>Configuración del desencadenador  
 En el ejemplo siguiente se muestra cómo detectar paréntesis coincidentes, entre llaves y corchetes y establecer el desencadenador para él en el analizador. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método en el <xref:Microsoft.VisualStudio.Package.Source> clase detecta el desencadenador y llama el analizador para encontrar la pareja coincidente (consulte la sección "Buscar la coincidencia" en este tema). En este ejemplo es solo con fines ilustrativos. Supone que el escáner contiene un método `GetNextToken` que identifica y devuelve los tokens de una línea de texto.  
  
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
  
## <a name="matching-the-braces"></a>Las llaves coincidentes  
 Este es un ejemplo simplificado para que coincida con el {} elementos de lenguaje, () y [] y agregar sus intervalos para la <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto. Este enfoque no es un enfoque recomendado para el análisis de código fuente; es solo con fines ilustrativos.  
  
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
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)   
 [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

