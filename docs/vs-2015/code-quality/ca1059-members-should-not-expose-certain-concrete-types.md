---
title: 'CA1059: Los miembros no deben exponer algunos tipos concretos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 894b4c22aaab2b0cce81053e6466b791a50b089a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816890"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Los miembros no deben exponer determinados tipos concretos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Un tipo concreto es un tipo que tiene una implementación completa y, por consiguiente, se pueden crear instancias de él. Para permitir un uso extendido del miembro, reemplace el tipo concreto por la interfaz sugerida. Esto permite que el miembro que acepte cualquier tipo que implementa la interfaz o usarse donde se espera un tipo que implementa la interfaz.

 En la tabla siguiente se enumera los tipos concretos específicos y sus reemplazos sugeridos.

|Tipo concreto|Replacement|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Mediante la interfaz desacopla al miembro de una implementación específica de un origen de datos XML.|

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el tipo concreto a la interfaz sugerida.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir un mensaje de esta regla si se necesita la funcionalidad específica que proporciona el tipo concreto.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1011: Considere pasar los tipos base como parámetros](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)



