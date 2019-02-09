---
title: 'CA2221: Los finalizadores deben estar protegidos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3da7f0da3901511e0f14e48b3ff0500928e3774
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917485"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: Los finalizadores deben estar protegidos

|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|Identificador de comprobación|CA2221|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo público implementa un finalizador que no especifica la familia de acceso (protegido).

## <a name="rule-description"></a>Descripción de la regla
 Los finalizadores deben utilizar el modificador de acceso de familia. Esta regla se aplica a los compiladores de C#, Visual Basic y Visual C++.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el finalizador para tener acceso de familia.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 Esta regla no se puede infringir en cualquier lenguaje de .NET de alto nivel; se puede infringir si va a escribir el lenguaje intermedio de Microsoft.

```
// =============== CLASS MEMBERS DECLARATION ===================
//   note that class flags, 'extends' and 'implements' clauses
//          are provided here for information only

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance void
            Finalize() cil managed
    {

      // Code size       1 (0x1)
      .maxstack  0
      IL_0000:  ret
    } // end of method FinalizeMethodNotProtected::Finalize

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method FinalizeMethodNotProtected::.ctor

  } // end of class FinalizeMethodNotProtected
} // end of namespace
```

## <a name="see-also"></a>Vea también

- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)