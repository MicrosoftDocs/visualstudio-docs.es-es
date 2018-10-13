---
title: 'CA2151: Los campos con tipos críticos deben ser crítico para la seguridad | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e2627c13f496623d281ed5e3c486592b2a4de6e2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253536"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151: Los campos con tipos críticos deben ser críticos para la seguridad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName||
|Identificador de comprobación|CA2151|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Se declara un campo transparente para la seguridad o un campo crítico seguro. Su tipo se especifica como crítico para la seguridad. Por ejemplo:

```csharp
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      Type1 m_field; // CA2151, transparent field of critical type
   }

```

 En este ejemplo, `m_field` es un campo transparente para la seguridad de un tipo que es crítico para la seguridad.

## <a name="rule-description"></a>Descripción de la regla
 Para utilizar tipos críticos para la seguridad, el código que hace referencia al tipo debe ser crítico para la seguridad o crítico para la seguridad y disponible desde código transparente. Esto es así incluso si la referencia es indirecta. Por ejemplo, cuando se hace referencia a un campo transparente que tiene un tipo crítico, el código debe ser crítico para la seguridad o crítico para la seguridad y disponible desde código transparente. Por consiguiente, tener un campo transparente para la seguridad o crítico para la seguridad y disponible desde código transparente puede llevar a confusión, porque el código transparente todavía no podrá tener acceso al campo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el campo con el atributo <xref:System.Security.SecurityCriticalAttribute> o convierta el tipo al que hace referencia el campo en transparente para la seguridad o crítico para la seguridad y disponible desde código transparente.

```csharp
// Fix 1: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

// Fix 2: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   class Type1 { } // Type1 is now transparent

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

```

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Comentarios



