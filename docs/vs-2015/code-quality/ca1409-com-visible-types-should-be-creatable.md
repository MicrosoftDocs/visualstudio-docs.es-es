---
title: 'CA1409: Los tipos visibles Com deben poderse | Microsoft Docs'
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
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8d6a28acea085fad99549739a0c4ab132169a436
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889783"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Los tipos visibles COM se deben poder crear
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|Identificador de comprobación|CA1409|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo de referencia marcado específicamente como visible para el modelo de objetos componentes (COM) contiene un constructor parametrizado público pero no contiene un constructor público predeterminado (sin parámetros).

## <a name="rule-description"></a>Descripción de la regla
 Los clientes COM no puede crear un tipo sin un constructor predeterminado público. Sin embargo, el tipo puede aún tener acceso a los clientes COM si hay otros medios crear el tipo y pasarlo al cliente (por ejemplo, mediante el valor devuelto de una llamada al método).

 La regla omite los tipos derivados de <xref:System.Delegate?displayProperty=fullName>.

 De forma predeterminada, los siguientes son visibles para COM: ensamblados, tipos públicos, los miembros de instancia públicos en tipos públicos y todos los miembros de tipos de valor público.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue un constructor predeterminado público o quite el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si se proporcionan otras formas de crear y pasar el objeto para el cliente COM.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también
 [Habilitar tipos de .NET para la interoperación](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [interoperar con código no administrado](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



