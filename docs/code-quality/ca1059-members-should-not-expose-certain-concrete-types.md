---
title: 'CA1059: Los miembros no deben exponer determinados tipos concretos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78a5ab72d838cbac21208940bd43aec370777183
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Los miembros no deben exponer determinados tipos concretos
|||  
|-|-|  
|TypeName|MembersShouldNotExposeCertainConcreteTypes|  
|Identificador de comprobación|CA1059|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un miembro visible externamente es un tipo concreto o expone determinados tipos concretos a través de uno de sus parámetros o valor devuelto. Actualmente, esta regla informa sobre la exposición de los siguientes tipos concretos:  
  
-   Un tipo derivado de <xref:System.Xml.XmlNode?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Un tipo concreto es un tipo que tiene una implementación completa y, por consiguiente, se pueden crear instancias de él. Para permitir un uso extendido del miembro, reemplace el tipo concreto por la interfaz sugerida. Esto permite que el miembro acepte cualquier tipo que implementa la interfaz o utilizarse donde se espera un tipo que implementa la interfaz.  
  
 En la tabla siguiente se enumera los tipos concretos específicos y sus reemplazos sugeridos.  
  
|Tipo concreto|Replacement|  
|-------------------|-----------------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Mediante la interfaz, desacopla al miembro de una implementación específica de un origen de datos XML.|  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el tipo concreto por la interfaz sugerida.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir un mensaje de esta regla si se necesita la funcionalidad específica que proporciona el tipo concreto.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1011: Considere pasar los tipos base como parámetros](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)