---
title: "Comentarios de c&#243;digo en un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comentarios, auxiliares en servicios de lenguaje [managed package framework]"
  - "Servicios de lenguaje [managed package framework], código de comentarios"
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Comentarios de c&#243;digo en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los lenguajes de programación proporcionan normalmente significan anotar o comentario el código.  Un comentario es una sección de texto que proporciona información adicional sobre el código pero se omite durante la compilación o la interpretación.  
  
 Las clases de managed package \(MPF\) proporcionan compatibilidad para comentar y quitando el comentario del texto seleccionado.  
  
## Estilos de comentario  
 Hay dos estilos generales de comentario:  
  
1.  Comentarios de la línea, donde es el comentario de una sola línea.  
  
2.  Bloquea los comentarios, donde el comentario puede incluir varias líneas.  
  
 Los comentarios de la línea tienen normalmente un carácter inicial \(o caracteres\), mientras que los comentarios del bloque tienen caracteres de inicio y de fin.  Por ejemplo, en C\#, un comentario de la línea empieza con \/\/, y comienza a un comentario de bloque con\/\* y termina con \*.  
  
 Cuando el usuario selecciona el comando **Selección con comentarios** de **Editar** \- el menú de \> **AVANZADAS** , el comando se enrutan al método de <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> en la clase de <xref:Microsoft.VisualStudio.Package.Source> .  Cuando el usuario selecciona el comando **Selección sin comentarios**, enrutan al comando al método de <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> .  
  
## Admitir comentarios de código  
 Puede tener los comentarios de código de compatibilidad del servicio de lenguaje mediante el parámetro con nombre de `EnableCommenting` de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .  esto establece la propiedad de <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> de la clase de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  Para obtener más información sobre las características de servicce de lenguaje de valor, vea [Registrar un servicio de lenguaje](../../extensibility/internals/registering-a-legacy-language-service1.md)\).  
  
 También debe reemplazar el método de <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> para devolver una estructura de <xref:Microsoft.VisualStudio.Package.CommentInfo> con caracteres de comentario del lenguaje.  los caracteres de comentario de la línea de C\#\-estilo son el valor predeterminado.  
  
### Ejemplo  
 A continuación se muestra una aplicación de ejemplo del método de <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> .  
  
```c#  
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
  
## Vea también  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrar un servicio de lenguaje](../../extensibility/internals/registering-a-legacy-language-service1.md)