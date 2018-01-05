---
title: 'CA1059: Los miembros no deben exponer determinados tipos concretos | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eae9070d76312fa4840f2cf8724a74a2cde4f7b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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