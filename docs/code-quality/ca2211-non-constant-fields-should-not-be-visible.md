---
title: 'CA2211: Los campos no constantes no deben ser visibles'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 11ff4ca3a3146c1080e26fd3ab50af7f7cf0e4e6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231760"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Los campos no constantes no deben ser visibles

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|Identificador de comprobación|CA2211|
|Categoría|Microsoft.Usage|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un campo estático público o protegido no es constante ni es de solo lectura.

## <a name="rule-description"></a>Descripción de la regla
Los campos estáticos que no son constantes ni de sólo lectura no son seguros para subprocesos. El acceso a este tipo de campo debe controlarse cuidadosamente y requiere técnicas de programación avanzada para sincronizar el acceso al objeto de clase. Dado que estos son conocimientos difíciles de aprender y dominar, y probar este tipo de objeto plantea sus propios desafíos, los campos estáticos se utilizan mejor para almacenar datos que no cambian. Esta regla se aplica a las bibliotecas; las aplicaciones no deben exponer ningún campo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, haga que la constante del campo estático o sea de solo lectura. Si esto no es posible, vuelva a diseñar el tipo para utilizar un mecanismo alternativo, como una propiedad segura para subprocesos que administra el acceso seguro para subprocesos al campo subyacente. Tenga en cuentan que los problemas como la contención de bloqueos y los interbloqueos pueden afectar al rendimiento y el comportamiento de la biblioteca.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si está desarrollando una aplicación y, por tanto, tiene control total sobre el acceso al tipo que contiene el campo estático. Los diseñadores de bibliotecas no deben suprimir una advertencia de esta regla. el uso de campos estáticos no constantes puede hacer que el uso de la biblioteca sea difícil para los desarrolladores.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe esta regla.

[!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]