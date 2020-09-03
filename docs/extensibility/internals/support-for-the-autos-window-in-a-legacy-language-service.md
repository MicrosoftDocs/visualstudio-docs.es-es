---
title: Compatibilidad con la ventana automático en un servicio de lenguaje heredado | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704883"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Compatibilidad con la ventana Automático en un servicio de lenguaje heredado
La ventana **automático** muestra expresiones como variables y parámetros que están en el ámbito cuando se pausa el programa que se está depurando (ya sea debido a un punto de interrupción o una excepción). Las expresiones pueden incluir variables, locales o globales, y parámetros que se han cambiado en el ámbito local. La ventana **automático** también puede incluir la creación de instancias de una clase, una estructura o algún otro tipo. Cualquier cosa que un evaluador de expresiones pueda evaluar puede mostrarse en la ventana **automático** .

 Managed Package Framework (MPF) no proporciona compatibilidad directa para la ventana **automático** . Sin embargo, si reemplaza el <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> método, puede devolver una lista de expresiones que se van a presentar en la ventana **automático** .

## <a name="implementing-support-for-the-autos-window"></a>Implementar la compatibilidad con la ventana automático
 Todo lo que necesita para admitir la ventana **automático** es implementar el <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. La implementación debe decidir, dada una ubicación en el archivo de código fuente, qué expresiones deben aparecer en la ventana **automático** . El método devuelve una lista de cadenas en las que cada cadena representa una sola expresión. Un valor devuelto de <xref:Microsoft.VisualStudio.VSConstants.S_OK> indica que la lista contiene expresiones, mientras <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> que indica que no hay expresiones para mostrar.

 Las expresiones reales devueltas son los nombres de las variables o los parámetros que aparecen en esa ubicación en el código. Estos nombres se pasan al evaluador de expresiones para obtener los valores y los tipos que se muestran en la ventana **automático** .

### <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una implementación del <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> método que obtiene una lista de expresiones del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método mediante el motivo del análisis <xref:Microsoft.VisualStudio.Package.ParseReason> . Cada una de las expresiones se ajusta como un `TestVsEnumBSTR` que implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interfaz.

 Tenga en cuenta que los `GetAutoExpressionsCount` `GetAutoExpression` métodos y son métodos personalizados en el `TestAuthoringSink` objeto y se agregaron para admitir este ejemplo. Representan una manera en la que se puede tener acceso a las expresiones agregadas al `TestAuthoringSink` objeto por el analizador (llamando al <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> método) fuera del analizador.

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
