---
title: "Descendants (Propiedad din&#225;mica XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Descendants (Propiedad din&#225;mica XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtiene un indizador que se usa para recuperar todos los descendientes del elemento actual que coinciden con el nombre expandido especificado.  
  
## Sintaxis  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## Valor de propiedad\/valor devuelto  
 Un indizador del tipo `IEnumerable<XElement> Item(String expandedName)`.Este indizador toma el nombre expandido de los elementos descendientes especificados y devuelve los elementos secundarios coincidentes en una colección <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## Comentarios  
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> de la clase <xref:System.Xml.Linq.XContainer>.  
  
 Los elementos de la colección devuelta están en el orden del documento de origen XML.  
  
 Esta propiedad usa la ejecución aplazada.  
  
## Vea también  
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elementos](../designers/elements-xelement-dynamic-property.md)