---
title: 'CA1801: Revisar parámetros sin utilizar'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 142ed6bca0513022b8edd1a062c443aa50d08191
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Revisar parámetros sin utilizar
|||
|-|-|
|TypeName|ReviewUnusedParameters|
|Identificador de comprobación|CA1801|
|Categoría|Microsoft.Usage|
|Cambio problemático|No problemático: si el miembro no es visible fuera del ensamblado, sin tener en cuenta el cambio realizado.<br /><br /> No problemático: si cambia el miembro para usar el parámetro dentro del cuerpo.<br /><br /> Problemático: Si quita el parámetro y está visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
 Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método. Esta regla no examina los siguientes métodos:

-   Métodos que se hace referencia a un delegado.

-   Métodos que se utilizan como controladores de eventos.

-   Los métodos declarados con el `abstract` (`MustOverride` en Visual Basic) modificador.

-   Los métodos declarados con el `virtual` (`Overridable` en Visual Basic) modificador.

-   Los métodos declarados con el `override` (`Overrides` en Visual Basic) modificador.

-   Los métodos declarados con el `extern` (`Declare` instrucción en Visual Basic) modificador.

## <a name="rule-description"></a>Descripción de la regla
 Revise los parámetros de métodos no virtuales que no se utilizan en el cuerpo del método para asegurarse de que no hay exactitud en torno al error para tener acceso a ellos. Parámetros sin utilizar conllevan un costo de mantenimiento y rendimiento.

 A veces una infracción de esta regla puede apuntar a un error de implementación del método. Por ejemplo, el parámetro debe haberse utilizado en el cuerpo del método. Suprimir las advertencias de esta regla si el parámetro tiene que existir por compatibilidad con versiones anteriores.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el parámetro sin usar (un cambio importante) o utilice el parámetro en el cuerpo del método (un cambio de no separación).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla de código previamente distribuido para que la corrección supondría un cambio importante.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos métodos. Un método infringe la regla y el otro método satisface la regla.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)