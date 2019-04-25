---
title: Compatibilidad con la ventana automático en un servicio de lenguaje heredado | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 01d2046d7693b23865555abb06962dead4a435ae
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988380"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Compatibilidad con la ventana Automático en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El **automático** ventana muestra expresiones como las variables y parámetros que están en ámbito cuando el programa que se está depurando está en pausa (ya sea debido a un punto de interrupción o una excepción). Las expresiones pueden incluir variables locales o globales y los parámetros que se han cambiado en el ámbito local. El **automático** ventana también puede incluir las creaciones de instancias de una clase, estructura o algún otro tipo. Todo lo que un evaluador de expresiones puede evaluar potencialmente puede mostrarse en el **automático** ventana.  
  
 Managed package framework (MPF) no proporciona compatibilidad directa para la **automático** ventana. Sin embargo, si invalida el <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> método, puede devolver una lista de expresiones que se presentará en la **automático** ventana.  
  
## <a name="implementing-support-for-the-autos-window"></a>Implementar la compatibilidad de la ventana automático  
 Todo lo que necesita hacer para admitir la **automático** ventana consiste en implementar la <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase. La implementación debe decidir, dada una ubicación en el archivo de origen, las expresiones deben aparecer en el **automático** ventana. El método devuelve una lista de cadenas donde cada cadena representa una única expresión. Un valor devuelto de <xref:Microsoft.VisualStudio.VSConstants.S_OK> indica que la lista contiene expresiones, aunque <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> indica que no hay ninguna expresión para mostrar.  
  
 Las expresiones reales devueltas son los nombres de variables o parámetros que aparecen en esa ubicación en el código. Estos nombres se pasan al evaluador para obtener los valores y tipos que se muestran a continuación, en el **automático** ventana.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra una implementación de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> método que obtiene una lista de expresiones de la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> con el motivo por el análisis del método <xref:Microsoft.VisualStudio.Package.ParseReason>. Cada una de las expresiones se empaqueta como un `TestVsEnumBSTR` que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interfaz.  
  
 Tenga en cuenta que el `GetAutoExpressionsCount` y `GetAutoExpression` métodos son métodos personalizados en el `TestAuthoringSink` de objetos y se agregaron para admitir este ejemplo. Representan una manera en que las expresiones de agregado a la `TestAuthoringSink` objeto por el analizador (mediante una llamada a la <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> método) se puede tener acceso fuera del analizador.  
  
```csharp  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```
