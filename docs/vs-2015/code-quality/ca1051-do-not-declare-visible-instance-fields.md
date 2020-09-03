---
title: 'CA1051: no declarar campos de instancia visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 076ce3858774d44e2d6c4c25205ced74b7a41bf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539768"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: No declarar campos de instancia visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|Identificador de comprobación|CA1051|
|Category|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo visible externamente tiene un campo de instancia visible externamente.

## <a name="rule-description"></a>Descripción de la regla
 El uso principal de un campo debe ser como un detalle de implementación. Los campos deben ser `private` o `internal` y deben exponerse mediante propiedades. Es tan fácil acceder a una propiedad a medida que se tiene acceso a un campo, y el código de los descriptores de acceso de una propiedad puede cambiar a medida que las características del tipo se expanden sin introducir cambios importantes. Las propiedades que devuelven el valor de un campo privado o interno están optimizadas para realizarse en par con el acceso a un campo. un aumento del rendimiento muy bajo se asocia al uso de campos visibles externamente en las propiedades.

 Externamente visible hace referencia `public` a `protected` `protected internal` los niveles de accesibilidad, y ( `Public` , y `Protected` `Protected Friend` en Visual Basic).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, haga que el campo `private` o `internal` y lo exponga mediante una propiedad externamente visible.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Los campos visibles externamente no proporcionan ninguna ventaja que no esté disponible para las propiedades. Además, los campos públicos no se pueden proteger mediante [peticiones de vínculo](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). Vea [CA2112: los tipos seguros no deben exponer los campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo ( `BadPublicInstanceFields` ) que infringe esta regla. `GoodPublicInstanceFields` muestra el código corregido.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2112: Los tipos seguros no deben exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Consulte también
 [Peticiones de vínculos](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
