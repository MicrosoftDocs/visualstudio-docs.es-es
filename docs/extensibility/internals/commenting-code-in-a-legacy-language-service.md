---
title: Comentario de código en un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec42d81a2d472cec5f96cbeec416801c22465834
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342046"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Código de comentario en un servicio de lenguaje heredado
Normalmente, los lenguajes de programación proporcionan un medio para anotar o comentar el código. Un comentario es una sección de texto que proporciona información adicional sobre el código, pero se omite durante la compilación o interpretación.

 Las clases de framework (MPF) de paquetes administrados proporcionan compatibilidad para comentar y quitar comentario de texto seleccionado.

## <a name="comment-styles"></a>Estilos de comentario
Hay dos estilos generales del comentario:

1. Comentarios en línea, donde es el comentario en una sola línea.

2. Comentarios del bloque, donde el comentario puede incluir varias líneas.

Comentarios de línea suelen tengan un carácter inicial (o caracteres), mientras que los comentarios del bloque tiene los caracteres inicial y final. Por ejemplo, en C#, un comentario de línea comienza con `//`, e inicia un comentario de bloque con `/*` y termina con `*/`.

Cuando el usuario selecciona el comando **selección con comentarios** desde el **editar** > **avanzadas** el comando de menú, se enruta a la <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> método en el <xref:Microsoft.VisualStudio.Package.Source> clase. Cuando el usuario selecciona el comando **selección sin comentarios**, el comando se enruta a la <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> método.

## <a name="support-code-comments"></a>Comentarios del código de soporte técnico
 Puede tener los comentarios del código de lenguaje servicio soporte técnico por medio de la `EnableCommenting` con el nombre de parámetro de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Esto establece la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> propiedad de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase. Para obtener más información acerca de cómo establecer las características del servicio de lenguaje, consulte [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md).

 También debe invalidar el <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> método devuelva un <xref:Microsoft.VisualStudio.Package.CommentInfo> estructura con los caracteres de comentario para su idioma. C#-caracteres de comentario de línea de estilo son el valor predeterminado.

### <a name="example"></a>Ejemplo
 Este es un ejemplo de implementación de la <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> método.

```csharp
using Microsoft.VisualStudio.Package;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override CommentInfo GetCommentFormat() {
            CommentInfo info = new CommentInfo();
            info.LineStart       = "//";
            info.BlockStart      = "/*";
            info.BlockEnd        = "*/";
            info.UseLineComments = true;
            return info;
        }
    }
}
```

## <a name="see-also"></a>Vea también
- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)