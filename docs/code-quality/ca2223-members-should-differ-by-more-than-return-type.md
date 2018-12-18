---
title: 'CA2223: Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93822dd3db325e3463c4a8f175c8ca289cac9e5d
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549831"
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto

|||
|-|-|
|TypeName|MembersShouldDifferByMoreThanReturnType|
|Identificador de comprobación|CA2223|
|Categoría|Microsoft.Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Dos miembros públicos o protegidos tienen firmas idénticas, salvo por el tipo de valor devuelto.

## <a name="rule-description"></a>Descripción de la regla
 Aunque common language runtime permite el uso de tipos de valor devuelto para diferenciar miembros idénticos, esta característica no está en Common Language Specification ni es una característica común de los lenguajes de programación. NET. Cuando los miembros difieren solo por tipo de valor devuelto, los desarrolladores y herramientas de desarrollo podrían no correctamente distinguir entre ellos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambiar el diseño de los miembros, por lo que son únicos solo según sus nombres y tipos de parámetro, o no exponen a los miembros.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente, en lenguaje intermedio de Microsoft (MSIL), muestra un tipo que infringe esta regla. Tenga en cuenta que no se infringe esta regla mediante el uso de C# o Visual Basic.

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