---
title: 'CA1801: revisar parámetros no usados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f5789b514d645fc670acf9307e4714c160c3b4c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918173"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Revisar parámetros sin utilizar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente sobre Visual Studio, vea [CA1801: revisar los parámetros no usados](/visualstudio/code-quality/ca1801-review-unused-parameters).

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|Identificador de comprobación|CA1801|
|Categoría|Microsoft.Usage|
|Cambio problemático|No problemático: Si el miembro no es visible fuera del ensamblado, independientemente del cambio que realice.<br /><br /> No problemático: Si cambia el miembro para usar el parámetro dentro de su cuerpo.<br /><br /> Problemático: Si quita el parámetro y es visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
 Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método. Esta regla no examina los métodos siguientes:

- Métodos a los que hace referencia un delegado.

- Métodos usados como controladores de eventos.

- Los métodos declarados con el modificador `abstract` (`MustOverride` en Visual Basic).

- Los métodos declarados con el modificador `virtual` (`Overridable` en Visual Basic).

- Los métodos declarados con el modificador `override` (`Overrides` en Visual Basic).

- Los métodos declarados con el modificador `extern` (`Declare` instrucción en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla
 Revise los parámetros de los métodos no virtuales que no se usan en el cuerpo del método para asegurarse de que no existe ninguna corrección en torno al error para tener acceso a ellos. Los parámetros sin usar incurren en costos de mantenimiento y rendimiento.

 A veces, una infracción de esta regla puede apuntar a un error de implementación en el método. Por ejemplo, el parámetro se debería haber utilizado en el cuerpo del método. Suprima las advertencias de esta regla si el parámetro tiene que existir debido a la compatibilidad con versiones anteriores.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el parámetro sin usar (un cambio importante) o use el parámetro en el cuerpo del método (un cambio no problemático).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla para el código enviado previamente para el que la corrección sería un cambio importante.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran dos métodos. Un método infringe la regla y el otro método cumple la regla.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)
