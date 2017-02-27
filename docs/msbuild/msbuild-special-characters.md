---
title: "Caracteres especiales de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "escape"
  - "caracteres de escape"
  - "caracteres de escape de MSBuild"
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# Caracteres especiales de MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reserva algunos caracteres para un uso especial en contextos concretos.  Solo tiene que usar estos caracteres como identificadores de escape si desea utilizarlos literalmente en el contexto en el que se reservan.  Por ejemplo, un asterisco tiene un significado especial únicamente en los atributos `Include` y `Exclude` de una definición de elemento y en llamadas a `CreateItem`.  Si desea que un asterisco aparezca como un asterisco en uno de esos contextos, debe utilizarlo como identificador de escape.  En los demás contextos, simplemente escriba el asterisco donde desea que aparezca.  
  
 Para usar como identificador de escape un carácter especial, use la sintaxis %*xx*, donde *xx* representa el valor hexadecimal ASCII del carácter.  Para obtener más información, vea [Cómo: Utilizar caracteres de escape especiales en MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## Caracteres especiales  
 La tabla siguiente enumera los caracteres especiales de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]:  
  
|**Carácter**|**ASCII**|**Uso reservado**|  
|------------------|---------------|-----------------------|  
|%|%25|Referencia a metadatos|  
|$|%24|Referencia a propiedades|  
|@|%40|Referencia a listas de elementos|  
|'|%27|Condiciones y otras expresiones|  
|;|%3B|Separador de listas|  
|?|%3F|Carácter comodín para su uso en nombres de archivo en los atributos `Include` y `Exclude`|  
|\*|%2A|Carácter comodín para su uso en nombres de archivo en los atributos `Include` y `Exclude`|  
  
## Vea también  
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)   
 [elementos](../msbuild/msbuild-items.md)