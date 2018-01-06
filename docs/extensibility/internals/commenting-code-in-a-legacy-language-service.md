---
title: "Comentarios del código en un servicio de lenguaje heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e6dfeb31ab062d5182b56ba450450d41a6dab807
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Comentarios del código en un servicio de lenguaje heredado
Normalmente, los lenguajes de programación proporcionan un medio para anotar o marque como comentario el código. Un comentario es una sección de texto que proporciona información adicional sobre el código, pero se omite durante la compilación o interpretación.  
  
 Las clases de managed package framework (MPF) proporcionan compatibilidad para comentario y eliminar el comentario de texto seleccionado.  
  
## <a name="comment-styles"></a>Estilos de comentario  
 Hay dos estilos generales de comentario:  
  
1.  Comentarios de línea, donde es el comentario en una sola línea.  
  
2.  Comentarios del bloque, donde el comentario puede incluir varias líneas.  
  
 Comentarios de una línea suele tengan un carácter inicial (o caracteres), mientras los comentarios del bloque caracteres inicial y final. Por ejemplo, en C#, una línea de comentario comienza con / /, e inicia un bloque de comentarios con / * y termina con \*/.  
  
 Cuando el usuario selecciona el comando **selección con comentarios** desde el **editar** -> **avanzadas** el comando de menú, se enruta a la <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> método en el <xref:Microsoft.VisualStudio.Package.Source> clase. Cuando el usuario selecciona el comando **selección sin comentarios**, el comando se enruta a la <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> método.  
  
## <a name="supporting-code-comments"></a>Comentarios de código auxiliar  
 Puede tener sus comentarios de código de lenguaje servicio soporte por medio de la `EnableCommenting` con el nombre de parámetro de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Esto establece la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> propiedad de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase. Para obtener más información sobre la configuración de idioma servicce características, vea [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 También debe invalidar el <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> método para devolver un <xref:Microsoft.VisualStudio.Package.CommentInfo> estructura con los caracteres de comentario para el lenguaje. C#-caracteres de comentario de línea de estilo están el valor predeterminado.  
  
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
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)