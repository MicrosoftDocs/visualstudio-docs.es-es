---
title: 'CA1409: los tipos visibles com se deben poder crear | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: feb50f576fbff656acaa10b70bb4d8adbca1d6c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602391"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Los tipos visibles COM se deben poder crear
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|Identificador de comprobación|CA1409|
|Categoría|Microsoft. Interoperability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo de referencia que está marcado específicamente como visible para el modelo de objetos componentes (COM) contiene un constructor con parámetros público, pero no contiene un constructor público predeterminado (sin parámetros).

## <a name="rule-description"></a>Descripción de la regla
 Los clientes COM no pueden crear un tipo sin un constructor predeterminado público. Sin embargo, los clientes COM todavía pueden tener acceso al tipo si hay otro medio disponible para crear el tipo y pasarlo al cliente (por ejemplo, mediante el valor devuelto de una llamada al método).

 La regla omite los tipos que se derivan de <xref:System.Delegate?displayProperty=fullName>.

 De forma predeterminada, los siguientes elementos son visibles para COM: ensamblados, tipos públicos, miembros de instancia pública en tipos públicos y todos los miembros de tipos de valor públicos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue un constructor predeterminado público o quite el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si se proporcionan otras maneras de crear y pasar el objeto al cliente COM.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también
 [Calificar tipos de .net para](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) la [interoperabilidad con código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
