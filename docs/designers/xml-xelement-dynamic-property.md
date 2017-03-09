---
title: "Xml (Propiedad din&#225;mica XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Xml"
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Xml (Propiedad din&#225;mica XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtiene el contenido XML sin formato del elemento.  
  
## Sintaxis  
  
```  
elem.Xml  
```  
  
## Valor de propiedad y valor devuelto  
 Un <xref:System.String> que representa el contenido XML sin formato del elemento.  
  
## Comentarios  
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> de la clase <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con el parámetro `SaveOptions` establecido en <xref:System.Xml.Linq.SaveOptions>.  
  
## Vea también  
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valor](../designers/value-xelement-dynamic-property.md)