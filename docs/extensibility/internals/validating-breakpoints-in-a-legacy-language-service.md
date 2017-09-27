---
title: "Validación de los puntos de interrupción en un servicio de lenguaje heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2a87c22948e710a3b95ee7f79b31626794dc7708
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Validación de los puntos de interrupción en un servicio de lenguaje heredado
Un punto de interrupción indica que debe detenerse la ejecución del programa en un momento determinado, mientras se está ejecutando en un depurador. Un usuario puede colocar un punto de interrupción en cualquier línea en el archivo de origen, ya que el editor no tiene ningún conocimiento de lo que constituye una ubicación válida para un punto de interrupción. Cuando se inicia el depurador, todos los puntos de interrupción marcadas (denominados interrupción pendientes) están enlazados a la ubicación adecuada en el programa en ejecución. Al mismo tiempo que los puntos de interrupción se validan para asegurarse de que marcan ubicaciones de código válido. Por ejemplo, un punto de interrupción en un comentario no es válido, porque no hay ningún código en esa ubicación en el código fuente. El depurador deshabilita los puntos de interrupción no válidos.  
  
 Puesto que el servicio de lenguaje se conoce sobre el código fuente que se muestren, puede validar los puntos de interrupción antes de que el depurador se inicia. Puede invalidar el <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> método para devolver un intervalo de especificar una ubicación válida para un punto de interrupción. La ubicación de punto de interrupción todavía se valida cuando se inicia el depurador, pero se notifica al usuario de puntos de interrupción no válido sin esperar a que el depurador puede cargar.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implementar la compatibilidad para validar los puntos de interrupción  
  
-   El <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> método se aplica a la posición del punto de interrupción. Su implementación debe decidir si la ubicación es válida e indicar esto mediante la devolución de un intervalo de texto que identifica el código asociado a la posición de línea que el punto de interrupción.  
  
-   Devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> si la ubicación es válida, o <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> si no es válido.  
  
-   Si el punto de interrupción es válida del intervalo de texto se resalta junto con el punto de interrupción.  
  
-   Si el punto de interrupción no es válida, aparece un mensaje de error en la barra de estado.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra una implementación de la <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> método al que llama el analizador para obtener el intervalo de código (si existe) en la ubicación especificada.  
  
 En este ejemplo se da por supuesto que ha agregado un `GetCodeSpan` método a la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase que valida el intervalo de texto y devuelve `true` si es una ubicación de punto de interrupción válido.  
  
```csharp  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
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
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
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
  
## <a name="see-also"></a>Vea también  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)
