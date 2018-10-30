---
title: 'CA1051: No declarar campos de instancia visibles | Microsoft Docs'
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
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 691f5fe87d775d2bff2fc15ff15ca8022478b3a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910555"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: No declarar campos de instancia visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|Identificador de comprobación|CA1051|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo visible externamente tiene un campo de instancia visible externamente.

## <a name="rule-description"></a>Descripción de la regla
 El uso principal de un campo debe ser como un detalle de implementación. Los campos deben ser `private` o `internal` y deben exponerse utilizando propiedades. Es tan fácil tener acceso a una propiedad como tal tener acceso a un campo, y puede cambiar el código en los descriptores de acceso de una propiedad como expanden las características del tipo sin introducir cambios importantes. Las propiedades que solo devuelven el valor de un campo privado o interno están optimizadas para llevar a cabo a la par de acceso a un campo; ganancia de rendimiento muy escasa está asociada con el uso de los campos visibles externamente a través de propiedades.

 Visible externamente se refiere a `public`, `protected`, y `protected internal` (`Public`, `Protected`, y `Protected Friend` en Visual Basic) los niveles de accesibilidad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, hacer que el campo `private` o `internal` y exponerlo mediante el uso de una propiedad visible externamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Los campos visibles externamente no proporciona ninguna ventaja que no está disponible para las propiedades. Además, los campos públicos no puede proteger [peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). Consulte [CA2112: los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo (`BadPublicInstanceFields`) que infringe esta regla. `GoodPublicInstanceFields` Muestra el código corregido.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Vea también
 [Peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



