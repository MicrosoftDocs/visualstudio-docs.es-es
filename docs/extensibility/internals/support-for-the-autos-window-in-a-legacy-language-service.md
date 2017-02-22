---
title: "Compatibilidad con la ventana autom&#225;tico en un servicio de lenguaje heredado | Microsoft Docs"
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
  - "Servicios de lenguaje [managed package framework], ventana automático"
  - "Ventana automático, auxiliares en servicios de lenguaje [managed package framework]"
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Compatibilidad con la ventana autom&#225;tico en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La ventana de **Automtico** muestra expresiones como variables y parámetros que estén en el ámbito cuando se pausa el programa que se depura \(debido a un punto de interrupción o a una excepción\).  las expresiones pueden incluir variables, local o global, y los parámetros que se han cambiado en el ámbito local.  La ventana de **Automtico** también puede incluir instancias de una clase, de la estructura, o de algún otro tipo.  Todo lo que un evaluador de expresiones puede evaluar se podría mostrar en la ventana de **Automtico** .  
  
 El \(MPF\) managed package no proporciona compatibilidad directa para la ventana de **Automtico** .  Sin embargo, si reemplaza el método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> , puede devolver una lista de expresiones que se mostrarán en la ventana de **Automtico** .  
  
## Implementar la compatibilidad para la ventana de Automático  
 Lo único que debe hacer para admitir la ventana de **Automtico** es implementar el método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> en la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> .  La implementación debe decidir, dada una ubicación en el archivo de código fuente, que las expresiones deben aparecer en la ventana de **Automtico** .  El método devuelve una lista de cadenas en las que cada cadena representa una sola expresión.  un valor devuelto de <xref:Microsoft.VisualStudio.VSConstants.S_OK> indica que la lista contiene expresiones, mientras que <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> indica que no hay expresiones a mostrar.  
  
 Las expresiones reales devueltas son los nombres de las variables o los parámetros que aparecen en esa ubicación en el código.  Estos nombres se pasan al evaluador de expresiones para obtener los valores y los tipos que se muestran en la ventana de **Automtico** .  
  
### Ejemplo  
 El ejemplo siguiente se muestra una implementación del método de <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> que obtiene una lista de expresiones del método de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> mediante la razón <xref:Microsoft.VisualStudio.Package.ParseReason>de análisis.  Cada una de las expresiones se encapsula como `TestVsEnumBSTR` que implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> .  
  
 Observe que los métodos de `GetAutoExpressionsCount` y de `GetAutoExpression` son métodos personalizados en el objeto de `TestAuthoringSink` se agregó para admitir este ejemplo.  Representan una manera en que las expresiones agregadas al objeto de `TestAuthoringSink` el analizador \(llamando al método de <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> \) se pueden lograr fuera del analizador.  
  
```c#  
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