---
title: Caracteres especiales de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa1e52e61f4003a9495e1bff5bd64e4edc40a323
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078659"
---
# <a name="msbuild-special-characters"></a>Caracteres especiales de MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reserva algunos caracteres para usos especiales en contextos concretos. Para usar dichos caracteres literalmente en el contexto en el que están reservados, debe aplicarles secuencias de escape. Por ejemplo, un asterisco tiene un significado especial solo en los atributos `Include` y `Exclude` de una definición de elemento y en las llamadas a `CreateItem`. Si quiere que aparezca como un asterisco en uno de estos contextos, debe aplicarle una secuencia de escape. En todos los demás contextos, simplemente escriba el asterisco donde quiera que aparezca.  
  
 Para aplicar una secuencia de escape a un carácter especial, use la sintaxis %\<xx>, donde \<xx> representa el valor hexadecimal ASCII del carácter. Para obtener más información, vea [Cómo: Utilizar caracteres de escape especiales en MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Caracteres especiales  
 En la tabla siguiente se muestran los caracteres especiales de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]:  
  
|**Carácter**|**ASCII**|**Uso reservado**|  
|-------------------|---------------|------------------------|  
|%|%25|Referencia a metadatos|  
|$|%24|Referencia a propiedades|  
|@|%40|Referencia a listas de elementos|  
|'|%27|Condiciones y otras expresiones|  
|;|%3B|Separador de lista|  
|?|%3F|Carácter comodín para nombres de archivo en atributos `Include` y `Exclude`|  
|*|%2A|Carácter comodín para nombres de archivo en atributos `Include` y `Exclude`|  
  
## <a name="see-also"></a>Vea también  
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)   
 [Elementos](../msbuild/msbuild-items.md)