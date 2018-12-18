---
title: 'CA2151: Los campos con tipos críticos deben ser críticos para la seguridad'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14df76b363f4df5d09b06436765b5f0c66ad2c5d
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551904"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151: Los campos con tipos críticos deben ser críticos para la seguridad

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

Para corregir una infracción de esta regla, marque el campo con el <xref:System.Security.SecurityCriticalAttribute> atributo, o convierta el tipo que es al que hace referencia el campo de seguridad transparente o prueba de errores críticos.

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

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

### <a name="code"></a>Código

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]