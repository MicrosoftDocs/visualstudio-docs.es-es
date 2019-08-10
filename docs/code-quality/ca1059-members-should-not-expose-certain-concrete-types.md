---
title: 'CA1059: Los miembros no deben exponer algunos tipos concretos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f24881d04599677c5d45c93fc940286f115d593
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922509"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Los miembros no deben exponer algunos tipos concretos

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|Identificador de comprobación|CA1059|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un miembro visible externamente es un determinado tipo concreto o expone determinados tipos concretos a través de uno de sus parámetros o valor devuelto. Actualmente, esta regla notifica la exposición de los siguientes tipos concretos:

- Tipo derivado de <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
Un tipo concreto es un tipo que tiene una implementación completa y, por consiguiente, se pueden crear instancias de él. Para permitir el uso generalizado del miembro, reemplace el tipo concreto por la interfaz sugerida. Esto permite que el miembro acepte cualquier tipo que implemente la interfaz o se use donde se espera un tipo que implementa la interfaz.

En la tabla siguiente se enumeran los tipos concretos específicos y sus reemplazos sugeridos.

|Tipo concreto|Replacement|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName><br /><br /> El uso de la interfaz desacopla el miembro de una implementación concreta de un origen de datos XML.|

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie el tipo concreto a la interfaz sugerida.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir un mensaje de esta regla si se requiere la funcionalidad específica que proporciona el tipo concreto.

## <a name="related-rules"></a>Reglas relacionadas
[CA1011: Considere la posibilidad de pasar los tipos base como parámetros](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)