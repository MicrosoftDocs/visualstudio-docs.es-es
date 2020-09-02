---
title: Comentario de código en un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1405456ca9a6ba00926c82bcc7959ea36d26c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160906"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Comentario de código en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los lenguajes de programación proporcionan normalmente un medio para anotar o comentar el código. Un comentario es una sección de texto que proporciona información adicional sobre el código, pero que se omite durante la compilación o la interpretación.  
  
 Las clases de Managed Package Framework (MPF) proporcionan compatibilidad para comentar y quitar comentarios del texto seleccionado.  
  
## <a name="comment-styles"></a>Estilos de comentario  
 Hay dos estilos generales de Comentario:  
  
1. Comentarios de línea, donde el comentario está en una sola línea.  
  
2. Los comentarios de bloque, donde el comentario puede incluir varias líneas.  
  
   Los comentarios de línea suelen tener un carácter de inicio (o caracteres), mientras que los comentarios de bloque tienen caracteres de inicio y fin. Por ejemplo, en C#, un Comentario de línea comienza con//y un Comentario de bloque comienza con/* y termina con \* /.  
  
   Cuando el usuario selecciona la **selección de comentarios** del comando en el menú **Editar**  ->  **Opciones avanzadas** , el comando se enruta al <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase. Cuando el usuario selecciona el comando sin **marcar la selección**, el comando se enruta al <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> método.  
  
## <a name="supporting-code-comments"></a>Comentarios de código auxiliares  
 Puede hacer que su servicio de lenguaje admita los comentarios de código por medio del `EnableCommenting` parámetro con nombre de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Esto establece la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> propiedad de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase. Para obtener más información sobre cómo establecer las características de servicce de idioma, consulte [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
 También debe invalidar el <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> método para devolver una <xref:Microsoft.VisualStudio.Package.CommentInfo> estructura con los caracteres de comentario para su idioma. Los caracteres de comentario de línea de estilo C# son el valor predeterminado.  
  
### <a name="example"></a>Ejemplo  
 A continuación se muestra un ejemplo de implementación del <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> método.  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)
