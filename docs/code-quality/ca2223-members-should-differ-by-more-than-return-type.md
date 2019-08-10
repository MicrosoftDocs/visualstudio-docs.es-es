---
title: 'CA2223: Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de64e0271370a3cdcc6f0963dbf06925621b9b65
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920189"
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto

|||
|-|-|
|TypeName|MembersShouldDifferByMoreThanReturnType|
|Identificador de comprobación|CA2223|
|Categoría|Microsoft.Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Dos miembros públicos o protegidos tienen firmas que son idénticas salvo el tipo de valor devuelto.

## <a name="rule-description"></a>Descripción de la regla
Aunque el Common Language Runtime permite el uso de tipos de valor devuelto para diferenciar entre miembros idénticos, esta característica no está en el Common Language Specification, ni tampoco es una característica común de los lenguajes de programación de .NET. Cuando los miembros solo difieren en el tipo de valor devuelto, es posible que los desarrolladores y las herramientas de desarrollo no distingan correctamente entre ellos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie el diseño de los miembros para que sean únicos según sus nombres y tipos de parámetros, o no expongan los miembros.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente, en lenguaje intermedio de Microsoft (MSIL), se muestra un tipo que infringe esta regla. Tenga en cuenta que esta regla no se puede infringir con C# o Visual Basic.

```
.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit ReturnTypeTest
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance int32
            AMethod(int32 x) cil managed
    {
      // Code size       6 (0x6)
      .maxstack  1
      .locals init (int32 V_0)
      IL_0000:  ldc.i4.0
      IL_0001:  stloc.0
      IL_0002:  br.s       IL_0004

      IL_0004:  ldloc.0
      IL_0005:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig instance string
            AMethod(int32 x) cil managed
    {
      // Code size       10 (0xa)
      .maxstack  1
      .locals init (string V_0)
      IL_0000:  ldstr      "test"
      IL_0005:  stloc.0
      IL_0006:  br.s       IL_0008

      IL_0008:  ldloc.0
      IL_0009:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method ReturnTypeTest::.ctor

  } // end of class ReturnTypeTest

} // end of namespace UsageLibrary
```