---
title: "Validaci&#243;n de puntos de interrupci&#243;n en un servicio de lenguaje heredado | Microsoft Docs"
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
  - "validación de punto de interrupción"
  - "Servicios de lenguaje [managed package framework], validación de punto de interrupción"
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Validaci&#243;n de puntos de interrupci&#243;n en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un punto de interrupción indica que la ejecución del programa se detiene en un punto determinado mientras se está ejecutando en un depurador.  Un usuario puede colocar un punto de interrupción en cualquier línea del archivo de código fuente, ya que el editor no conoce qué constituye una ubicación válida para un punto de interrupción.  Cuando se inicia el depurador, todos los puntos de interrupción marcados \(denominados pendientes los puntos de interrupción\) se enlazan a la ubicación correcta del programa en ejecución.  Al mismo tiempo los puntos de interrupción se validan para asegurarse que marcan ubicaciones válidas en el código.  Por ejemplo, un punto de interrupción en un comentario no es válido, porque no hay código en esa ubicación en el código fuente.  El depurador deshabilita los puntos de interrupción no válidos.  
  
 Puesto que el servicio de lenguaje conoce el código fuente que se muestra, puede validar los puntos de interrupción antes de que arranquen el depurador.  Puede invalidar el método de <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> para devolver un intervalo que especifica una ubicación válida para un punto de interrupción.  La ubicación del punto de interrupción todavía se valida cuando se inicia el depurador, pero notifica al usuario de puntos de interrupción no válidos sin esperar a que el depurador para cargar.  
  
## La implementación de soporte para validar los puntos de interrupción  
  
-   El método de <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> tiene la posición del punto de interrupción.  La implementación debe decidir si la ubicación es válida, e indicar esto devolviendo un intervalo de texto que identifique el código asociado a la posición de línea el punto de interrupción.  
  
-   <xref:Microsoft.VisualStudio.VSConstants.S_OK> return si la ubicación es válida, o <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> si no es válido.  
  
-   Si el punto de interrupción es válido el intervalo de texto aparecerá resaltada junto con el punto de interrupción.  
  
-   Si el punto de interrupción es no válido, un mensaje de error aparece en la barra de estado.  
  
### Ejemplo  
 En este ejemplo se muestra una implementación del método de <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> que llama al analizador para obtener el intervalo de código \(si existe\) en la ubicación especificada.  
  
 Este ejemplo supone que ha agregado un método de `GetCodeSpan` a la clase de <xref:Microsoft.VisualStudio.Package.AuthoringSink> que valida el intervalo de texto y devuelve `true` si es una ubicación válida de punto de interrupción.  
  
```c#  
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
  
## Vea también  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)