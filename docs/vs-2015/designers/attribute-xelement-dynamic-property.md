---
title: Attribute (Propiedad dinámica de XElement) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 750e84a386360880cf30e76fc0157145820c654c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574934"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (Propiedad dinámica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Attribute (propiedad dinámica de XElement)](https://docs.microsoft.com/visualstudio/designers/attribute-xelement-dynamic-property).  
  
Obtiene un indizador que se usa para recuperar la instancia del atributo que se corresponde con el nombre expandido especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Un indizador del tipo `XAttribute Item(String expandedName)`. Este indizador toma el nombre expandido del atributo especificado y devuelve el elemento <xref:System.Xml.Linq.XAttribute> correspondiente, o bien `null` si no existe ningún atributo con el nombre especificado.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XElement.Attribute%2A> de la clase <xref:System.Xml.Linq.XElement?displayProperty=fullName>.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valor](../designers/value-xattribute-dynamic-property.md)



