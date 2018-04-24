---
title: 'CA2211: Los campos no constantes no deben ser visibles'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c36de9e19f01bad47bba390975d5ab59f2fd6e5c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Los campos no constantes no deben ser visibles
|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|Identificador de comprobación|CA2211|
|Categoría|Microsoft.Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un campo estático público o protegido no es constante ni es de solo lectura.

## <a name="rule-description"></a>Descripción de la regla
 Los campos estáticos que no son constantes ni de sólo lectura no son seguros para subprocesos. Acceso a este tipo de campo se debe controlar cuidadosamente y requiere técnicas de programación avanzadas para sincronizar el acceso al objeto de clase. Puesto que hay aspectos difíciles de aprender maestra y las pruebas de este tipo de objeto tiene sus propias dificultades, los campos estáticos son útiles para almacenar los datos que no cambian. Esta regla se aplica a las bibliotecas; las aplicaciones no deben exponer los campos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, asegúrese del campo estático constante o de solo lectura. Si esto no es posible, vuelva a diseñar el tipo para utilizar un mecanismo alternativo como una propiedad segura para subprocesos que administra el acceso seguro para subprocesos para el campo subyacente. Tenga en cuenta que problemas como la contención de bloqueo y los interbloqueos podrían afectar al rendimiento y comportamiento de la biblioteca.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si está desarrollando una aplicación y, por tanto, tiene control total sobre el acceso al tipo que contiene el campo estático. Los diseñadores de bibliotecas no deben suprimir una advertencia de esta regla; usar campos estáticos no sea constante puede hacer mediante la biblioteca de difícil para los desarrolladores usar correctamente.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe esta regla.

 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]