---
title: 'CA1401: P / Invoke no debe ser visible | Microsoft Docs'
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
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 23142fcb226259378be56c59032d3b96d9b94087
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852512"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: Los elementos P/Invoke no deben estar visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|Identificador de comprobación|CA1401|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido en un tipo público tiene el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo (también se implementa por la `Declare` palabra clave en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="rule-description"></a>Descripción de la regla
 Los métodos marcados con el <xref:System.Runtime.InteropServices.DllImportAttribute> atributo (o métodos que se definen mediante la `Declare` palabra clave en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) usar servicios de invocación de plataforma para tener acceso a código no administrado. No se deberían exponer estos métodos. Al mantener estos métodos privados o internos, se asegura de que no se puede usar la biblioteca de infringir la seguridad al permitir el acceso a las API no administradas que no puede llamar en caso contrario, los autores de llamadas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nivel de acceso del método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente declara un método que infringe esta regla.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]



