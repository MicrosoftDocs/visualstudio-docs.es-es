---
title: "CA1059: Los miembros no deben exponer determinados tipos concretos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
helpviewer_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1059: Los miembros no deben exponer determinados tipos concretos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MembersShouldNotExposeCertainConcreteTypes|  
|Identificador de comprobación|CA1059|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un miembro visible externamente es de un tipo concreto o expone determinados tipos concretos a través de uno de sus parámetros o valores devueltos.  Actualmente, esta regla informa sobre la exposición de los tipos concretos siguientes:  
  
-   Tipo derivado de <xref:System.Xml.XmlNode?displayProperty=fullName>.  
  
## Descripción de la regla  
 Un tipo concreto es un tipo que tiene una implementación completa y, por consiguiente, se pueden crear instancias de él.  Para permitir un uso extendido del miembro, reemplace el tipo concreto por la interfaz sugerida.  Esto permite que el miembro acepte cualquier tipo que implemente la interfaz o que se utilice en aquellos puntos donde se espere un tipo que implementa la interfaz.  
  
 La tabla siguiente muestra los tipos concretos específicos y sus reemplazos sugeridos.  
  
|Tipo concreto|Reemplazo|  
|-------------------|---------------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Al utilizar la interfaz, se desacopla el miembro de una implementación específica de un origen de datos XML.|  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el tipo concreto por la interfaz sugerida.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir un mensaje de esta regla si se necesita la funcionalidad concreta prestada por el tipo concreto.  
  
## Reglas relacionadas  
 [CA1011: Considere pasar los tipos base como parámetros](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)