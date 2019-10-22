---
title: 'CA2221: los finalizadores deben estar protegidos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3e98c2ea598bcf73b919ba10ef1ea0b53c2a40f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651960"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: Debe proteger los finalizadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|Identificador de comprobación|CA2221|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo público implementa un finalizador que no especifica el acceso de familia (protegido).

## <a name="rule-description"></a>Descripción de la regla
 Los finalizadores deben utilizar el modificador de acceso de familia. Esta regla la aplican los C#compiladores, Visual Basic y visual C++ .

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el finalizador para que sea accesible desde la familia.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 Esta regla no se puede infringir en ningún lenguaje .NET de alto nivel. puede infringirse si está escribiendo lenguaje intermedio de Microsoft.

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
 [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
