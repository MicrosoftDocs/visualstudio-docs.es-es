---
title: Soporte para la ventana Autos en un servicio de lenguaje heredado ( Legacy Language Service) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704883"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Compatibilidad con la ventana Automático en un servicio de lenguaje heredado
La ventana **Automático** muestra expresiones como variables y parámetros que están en el ámbito cuando el programa que se está depurando está en pausa (ya sea debido a un punto de interrupción o una excepción). Las expresiones pueden incluir variables, locales o globales, y parámetros que se han cambiado en el ámbito local. La ventana **Autos** también puede incluir instancias de una clase, estructura o algún otro tipo. Cualquier cosa que un evaluador de expresiones pueda evaluar puede mostrarse potencialmente en la ventana **Automático.**

 El marco de paquete administrado (MPF) no proporciona compatibilidad directa con la ventana **Autos.** Sin embargo, <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> si invalida el método, puede devolver una lista de expresiones que se presentarán en la ventana **Automático.**

## <a name="implementing-support-for-the-autos-window"></a>Implementación de soporte para la ventana Autos
 Todo lo que necesita hacer para admitir la <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> ventana <xref:Microsoft.VisualStudio.Package.LanguageService> **Autos** es implementar el método en la clase. La implementación debe decidir, dada una ubicación en el archivo de origen, qué expresiones deben aparecer en la ventana **Automático.** El método devuelve una lista de cadenas en las que cada cadena representa una sola expresión. Un valor <xref:Microsoft.VisualStudio.VSConstants.S_OK> devuelto de indica que la <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> lista contiene expresiones, mientras que indica que no hay expresiones para mostrar.

 Las expresiones reales devueltas son los nombres de las variables o parámetros que aparecen en esa ubicación en el código. Estos nombres se pasan al evaluador de expresiones para obtener valores y tipos que, a continuación, se muestran en la ventana **Automático.**

### <a name="example"></a>Ejemplo
 En el ejemplo siguiente <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> se muestra una implementación del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método que <xref:Microsoft.VisualStudio.Package.ParseReason>obtiene una lista de expresiones del método mediante el motivo de análisis . Cada una de las expresiones se ajusta como una `TestVsEnumBSTR` que implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interfaz.

 Tenga en `GetAutoExpressionsCount` `GetAutoExpression` cuenta que los `TestAuthoringSink` métodos y son métodos personalizados en el objeto y se agregaron para admitir este ejemplo. Representan una forma en la `TestAuthoringSink` que se puede tener acceso <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> a las expresiones agregadas al objeto por el analizador (mediante una llamada al método) fuera del analizador.

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
