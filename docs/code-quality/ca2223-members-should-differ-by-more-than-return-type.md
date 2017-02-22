---
title: "CA2223: Los miembros deben diferenciarse por algo m&#225;s que por un tipo de valor devuelto | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MembersShouldDifferByMoreThanReturnType"
  - "CA2223"
helpviewer_keywords: 
  - "CA2223"
  - "MembersShouldDifferByMoreThanReturnType"
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2223: Los miembros deben diferenciarse por algo m&#225;s que por un tipo de valor devuelto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MembersShouldDifferByMoreThanReturnType|  
|Identificador de comprobación|CA2223|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Dos miembros públicos o protegidos tienen firmas idénticas excepto el tipo de valor devuelto.  
  
## Descripción de la regla  
 Aunque Common Language Runtime permite utilizar tipos de valor devuelto para diferenciar miembros idénticos, esta característica no se encuentra en Common Language Specification ni es común en los lenguajes de programación de .NET.  Cuando los miembros sólo se diferencian por el tipo de valor devuelto, los desarrolladores y las herramientas de desarrollo no se distinguen correctamente.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el diseño de los miembros para que sólo se basen en sus nombres y tipos de parámetros o para que no expongan los miembros.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente, en lenguaje intermedio de Microsoft \(MSIL\), muestra un tipo que infringe esta regla.  Observe que esta regla no se puede infringir con C\# o Visual Basic .NET.  
  
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