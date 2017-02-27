---
title: "Element (Propiedad din&#225;mica XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Element"
apitype: "Assembly"
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Element (Propiedad din&#225;mica XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtiene un indizador que se utiliza para recuperar la instancia del elemento secundario que se corresponde con el nombre expandido especificado.  
  
## Sintaxis  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## Valor de propiedad\/valor devuelto  
 Un indizador del tipo `XElement Item(String expandedName)`.Este indizador toma un parámetro de nombre expandido y devuelve el <xref:System.Xml.Linq.XElement> correspondiente, o bien `null` si no existe ningún elemento con el nombre especificado.  
  
## Comentarios  
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XContainer.Element%2A> de la clase <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.  
  
## Vea también  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elementos](../designers/elements-xelement-dynamic-property.md)