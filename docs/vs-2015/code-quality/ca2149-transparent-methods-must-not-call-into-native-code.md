---
title: 'CA2149: Los métodos transparentes no deben llamar a código nativo | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 887252eca86205858b168c7f5a4a6c33cb0cc67d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591121"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Los métodos transparentes no deben llamar a código nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA2149: los métodos transparentes no deben llamar a código nativo](https://docs.microsoft.com/visualstudio/code-quality/ca2149-transparent-methods-must-not-call-into-native-code).

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|Identificador de comprobación|CA2149|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método llama a una función nativa a través de un código auxiliar del método como P/Invoke.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en cualquier método transparente que llame directamente a código nativo, por ejemplo, a través de P/Invoke. Las infracciones de esta regla una <xref:System.MethodAccessException> en el modelo de transparencia de nivel 2 y una demanda completa de <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> en el modelo de transparencia de nivel 1.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método que llama al código nativo con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode/cs/ca2149 - transparentmethodsmustnotcallnativecode.cs#1)]



