---
title: 'CA2214: No llamar a métodos reemplazables en constructores'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ddc827e77b37de6490cb4bee081748f317865b57
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549565"
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

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, no llame a métodos virtuales del tipo desde dentro de los constructores del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla. El constructor debe rediseñarse para eliminar la llamada al método virtual.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra el efecto de infringir esta regla. La aplicación de prueba crea una instancia de `DerivedType`, lo que hace que su clase base (`BadlyConstructedType`) ejecute el constructor. `BadlyConstructedType`de forma incorrecta, constructor llama al método virtual `DoSomething`. Como se muestra en la salida, `DerivedType.DoSomething()` ejecuta y lleva a cabo antes `DerivedType`del constructor se ejecuta.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Este ejemplo produce el siguiente resultado:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```