---
title: "Atributo (Propiedad din&#225;mica XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Atributo (Propiedad din&#225;mica XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtiene un indizador que se usa para recuperar la instancia del atributo que se corresponde con el nombre expandido especificado.  
  
## Sintaxis  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## Valor de propiedad\/valor devuelto  
 Un indizador del tipo `XAttribute Item(String expandedName)`.Este indizador toma el nombre expandido del atributo especificado y devuelve el elemento <xref:System.Xml.Linq.XAttribute> correspondiente, o bien `null` si no existe ningún atributo con el nombre especificado.  
  
## Comentarios  
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XElement.Attribute%2A> de la clase <xref:System.Xml.Linq.XElement?displayProperty=fullName>.  
  
## Vea también  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valor](../designers/value-xattribute-dynamic-property.md)