---
title: 'CA2211: Los campos no constantes no deben ser visibles | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 62c3ee28a3b7cbb9bef864483e254dda5f63bfae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894259"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Los campos no constantes no deben ser visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|Identificador de comprobación|CA2211|
|Categoría|Microsoft.Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un campo estático público o protegido no es constante ni es de solo lectura.

## <a name="rule-description"></a>Descripción de la regla
 Los campos estáticos que no son constantes ni de sólo lectura no son seguros para subprocesos. Acceso a este tipo de campo se debe controlar cuidadosamente y requiere técnicas de programación avanzadas para sincronizar el acceso al objeto de clase. Dado que son difíciles de conocimientos para obtener información y y comprobar este tipo de objeto tiene sus propias dificultades, los campos estáticos mejor sirven para almacenar los datos que no cambian. Esta regla se aplica a las bibliotecas; las aplicaciones no deben exponer todos los campos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, que el campo estático, constante o de solo lectura. Si esto no es posible, vuelva a diseñar el tipo para utilizar un mecanismo alternativo como una propiedad de subprocesos que administra el acceso seguro para subprocesos en el campo subyacente. Tenga en cuenta que podrían afectar a problemas de contención de bloqueo y los interbloqueos el rendimiento y el comportamiento de la biblioteca.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si está desarrollando una aplicación y, por tanto, tiene control total sobre el acceso al tipo que contiene el campo estático. Los diseñadores de bibliotecas no deben suprimir una advertencia de esta regla; usar campos estáticos que no sea constante puede hacer mediante la biblioteca difícil para los desarrolladores para usar correctamente.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe esta regla.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]



