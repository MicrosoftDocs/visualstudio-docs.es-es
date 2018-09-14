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
ms.openlocfilehash: 708d2175afe8d1b0e6bec7c7ec419eac1ee4821f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551969"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Revisar parámetros sin utilizar
|||
|-|-|
|TypeName|ReviewUnusedParameters|
|Identificador de comprobación|CA1801|
|Categoría|Microsoft.Usage|
|Cambio problemático|No problemático: si el miembro no es visible fuera del ensamblado, independientemente del cambio que realice.<br /><br /> No problemático: si cambia el miembro para usar el parámetro dentro del cuerpo.<br /><br /> Problemático: Si quita el parámetro y está visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
 Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método. Esta regla no examina los métodos siguientes:

- Métodos que se hace referencia a un delegado.

- Métodos que se usan como controladores de eventos.

- Los métodos declarados con el `abstract` (`MustOverride` en Visual Basic) modificador.

- Los métodos declarados con el `virtual` (`Overridable` en Visual Basic) modificador.

- Los métodos declarados con el `override` (`Overrides` en Visual Basic) modificador.

- Los métodos declarados con el `extern` (`Declare` instrucción en Visual Basic) modificador.

## <a name="rule-description"></a>Descripción de la regla
 Revise los parámetros de métodos no virtuales que no se usan en el cuerpo del método para asegurarse de que no hay exactitud en torno al error para tener acceso a ellos. Parámetros sin usar conllevan un costo de mantenimiento y rendimiento.

 A veces, una infracción de esta regla puede señalar a un error en el método de implementación. Por ejemplo, el parámetro debe haberse utilizado en el cuerpo del método. Suprimir advertencias de esta regla si el parámetro tiene que existir por compatibilidad con versiones anteriores.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el parámetro sin usar (un cambio importante) o utilizar el parámetro en el cuerpo del método (un cambio de no separación).

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla para código lanzado al mercado anteriormente para que la solución sería un cambio importante.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos métodos. Un método infringe la regla y el otro método cumple la regla.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)