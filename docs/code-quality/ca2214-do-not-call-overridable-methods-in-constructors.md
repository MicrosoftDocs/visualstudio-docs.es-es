---
title: 'CA2214: No llamar a métodos reemplazables en constructores'
ms.date: 05/29/2016
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e05e6925085b27de3001c8ff62d8a3c6e69a88f
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401312"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: No llamar a métodos reemplazables en constructores

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|Identificador de comprobación|CA2214|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

El constructor de un tipo no sellado llama a un método virtual definido en su clase.

## <a name="rule-description"></a>Descripción de la regla

Cuando se llama a un método virtual, el tipo real que se ejecuta el método no está activado hasta que el tiempo de ejecución. Cuando un constructor llama a un método virtual, es posible que no haya ejecutado el constructor para la instancia que invoca el método.

> [!NOTE]
> La implementación de análisis de binarios de esta regla tiene un mensaje de diagnóstico diferente de " **\[nombre Constructor] contiene una cadena de llamadas que da como resultado una llamada a un método virtual definido por la clase. Revise la siguiente pila de llamadas para consecuencias imprevistas**". El [analizadores de FxCop](install-fxcop-analyzers.md) implementación de esta regla tiene un mensaje de diagnóstico de "**no llamar a métodos reemplazables en constructores**".

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, no llame a métodos virtuales del tipo desde dentro de los constructores del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla. El constructor debe rediseñarse para eliminar la llamada al método virtual.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra el efecto de infringir esta regla. La aplicación de prueba crea una instancia de `DerivedType`, lo que hace que su clase base (`BadlyConstructedType`) ejecute el constructor. `BadlyConstructedType`de forma incorrecta, constructor llama al método virtual `DoSomething`. Como se muestra en la salida, `DerivedType.DoSomething()` se ejecuta antes que `DerivedType`del constructor se ejecuta.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Este ejemplo produce el siguiente resultado:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```