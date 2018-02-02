---
title: "CA2223: Los miembros deben diferenciarse por el tipo de valor devuelto más de | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4c72475c76a85216499a389d12f090ef302fc143
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
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
 Aunque common language runtime permite utilizar tipos de valor devuelto para diferenciar miembros idénticos, esta característica no está en Common Language Specification ni es una característica común de lenguajes de programación. NET. Cuando los miembros diferenciarse únicamente por el tipo de valor devuelto, los desarrolladores y las herramientas de desarrollo podrían no correctamente distinguir entre ellos.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el diseño de los miembros para que sean únicos basándose únicamente en sus nombres y tipos de parámetro, o no exponen a los miembros.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente, en lenguaje intermedio de Microsoft (MSIL), muestra un tipo que infringe esta regla. Tenga en cuenta que no se puede infringir esta regla mediante el uso de C# o Visual Basic.  
  
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