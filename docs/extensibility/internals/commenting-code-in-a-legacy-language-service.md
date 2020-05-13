---
title: Código de comentarios en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709435"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Código de comentarios en un servicio de lenguaje heredado
Los lenguajes de programación suelen proporcionar un medio para anotar o comentar el código. Un comentario es una sección de texto que proporciona información adicional sobre el código, pero se omite durante la compilación o interpretación.

 Las clases de marco de paquete administrado (MPF) proporcionan compatibilidad para comentar y quitar los comentarios del texto seleccionado.

## <a name="comment-styles"></a>Estilos de comentario
Hay dos estilos generales de comentario:

1. Comentarios de línea, donde el comentario está en una sola línea.

2. Bloquear comentarios, donde el comentario puede incluir varias líneas.

Los comentarios de línea suelen tener un carácter inicial (o caracteres), mientras que los comentarios de bloque tienen caracteres inicial y final. Por ejemplo, en C-, un `//`comentario de línea `/*` comienza con `*/`, y un comentario de bloque comienza con y termina con .

Cuando el usuario selecciona el comando Selección de **comentarios** en <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> el menú <xref:Microsoft.VisualStudio.Package.Source> **Editar** > **avanzada,** el comando se enruta al método de la clase. Cuando el usuario selecciona el comando **Anular comentario**selección <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> , el comando se enruta al método.

## <a name="support-code-comments"></a>Comentarios del código de soporte
 Puede hacer que su servicio de lenguaje `EnableCommenting` admita <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> comentarios de código mediante el parámetro con nombre del archivo . Esto establece <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propiedad de la clase. Para obtener más información acerca de cómo establecer características de servicio de lenguaje, vea [Registrar un servicio](../../extensibility/internals/registering-a-legacy-language-service1.md)de lenguaje heredado .

 También debe invalidar <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> el método <xref:Microsoft.VisualStudio.Package.CommentInfo> para devolver una estructura con los caracteres de comentario para el idioma. Los caracteres de comentario de línea de estilo de C-style son el valor predeterminado.

### <a name="example"></a>Ejemplo
 Este es un ejemplo <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> de implementación del método.

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
