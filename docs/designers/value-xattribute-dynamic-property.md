---
title: "Value (propiedad din&#225;mica XAttribute) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XAttribute.Value"
apitype: "Assembly"
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Value (propiedad din&#225;mica XAttribute)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtiene o establece el valor del atributo XML.  
  
## Sintaxis  
  
```  
attrib.Value   
```  
  
## Valor de propiedad y valor devuelto  
 <xref:System.String> que contiene el valor de este atributo.  
  
## Excepciones  
  
|Tipo de excepción|Condición|  
|-----------------------|---------------|  
|<xref:System.ArgumentNullException>|Cuando se establece, el parámetro `value` es `null`.|  
  
## Comentarios  
 Esta propiedad es equivalente a la propiedad <xref:System.Xml.Linq.XAttribute.Value%2A> de la clase <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, pero su propiedad dinámica también admite las notificaciones de cambio.  
  
## Vea también  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Propiedades dinámicas de la clase XAttribute](../designers/xattribute-class-dynamic-properties.md)   
 [Atributo](../designers/attribute-xelement-dynamic-property.md)