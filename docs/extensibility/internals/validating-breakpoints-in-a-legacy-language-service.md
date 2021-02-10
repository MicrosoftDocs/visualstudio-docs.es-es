---
title: Validando puntos de interrupción en un servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre cómo puede invalidar el método ValidateBreakpointLocation en un servicio de lenguaje heredado para validar los puntos de interrupción antes de que se inicie el depurador.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 593663c4906cc669c52336ffe6689e8de9fcde48
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941598"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Validación de puntos de interrupción en un servicio de lenguaje heredado
Un punto de interrupción indica que la ejecución del programa se debe detener en un punto determinado mientras se ejecuta en un depurador. Un usuario puede colocar un punto de interrupción en cualquier línea del archivo de código fuente, ya que el editor no tiene ningún conocimiento de lo que constituye una ubicación válida para un punto de interrupción. Cuando se inicia el depurador, todos los puntos de interrupción marcados (denominados puntos de interrupción pendientes) se enlazan a la ubicación adecuada en el programa en ejecución. Al mismo tiempo, los puntos de interrupción se validan para asegurarse de que marcan ubicaciones de código válidas. Por ejemplo, un punto de interrupción en un comentario no es válido, ya que no hay ningún código en esa ubicación en el código fuente. El depurador deshabilita los puntos de interrupción no válidos.

 Dado que el servicio de lenguaje conoce el código fuente que se muestra, puede validar los puntos de interrupción antes de que se inicie el depurador. Puede invalidar el <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> método para devolver un intervalo que especifique una ubicación válida para un punto de interrupción. La ubicación del punto de interrupción todavía se valida cuando se inicia el depurador, pero se notifica al usuario de puntos de interrupción no válidos sin esperar a que se cargue el depurador.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementar compatibilidad para validar puntos de interrupción

- Al <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> método se le asigna la posición del punto de interrupción. La implementación debe decidir si la ubicación es válida o no, e indicar Esto devolviendo un intervalo de texto que identifique el código asociado a la posición de línea del punto de interrupción.

- Devuelve <xref:Microsoft.VisualStudio.VSConstants.S_OK> si la ubicación es válida o <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> si no es válida.

- Si el punto de interrupción es válido, el intervalo de texto se resalta junto con el punto de interrupción.

- Si el punto de interrupción no es válido, aparece un mensaje de error en la barra de estado.

### <a name="example"></a>Ejemplo
 En este ejemplo se muestra una implementación del <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> método que llama al analizador para obtener el intervalo de código (si existe) en la ubicación especificada.

 En este ejemplo se da por supuesto que ha agregado un `GetCodeSpan` método a la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase que valida el intervalo de texto y devuelve `true` si es una ubicación de punto de interrupción válida.

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
- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)
