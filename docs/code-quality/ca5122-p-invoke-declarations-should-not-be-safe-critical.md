---
title: 'CA5122: Las declaraciones P/Invoke no deben ser críticas para la seguridad'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79ebba23b26e0967bc29a79e719e02d834a29f1b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919853"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122: Las declaraciones P/Invoke no deben ser críticas para la seguridad

|||
|-|-|
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|
|Identificador de comprobación|CA5122|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Una declaración P/Invoke se ha marcado con <xref:System.Security.SecuritySafeCriticalAttribute>:

```csharp
[assembly: AllowPartiallyTrustedCallers]

// ...
public class C
{
    [SecuritySafeCritical]
    [DllImport("kernel32.dll")]
    public static extern bool Beep(int frequency, int duration); // CA5122 - safe critical p/invoke
   }
```

En este ejemplo, `C.Beep(...)` se ha marcado como crítico para la seguridad y disponible desde código transparente.

## <a name="rule-description"></a>Descripción de la regla
Los métodos se marcan como SecuritySafeCritical cuando realizan una operación que afecta a la seguridad pero también son seguros para su uso en código transparente. Una de las reglas fundamentales del modelo de transparencia de seguridad es que el código transparente nunca puede llamar directamente a código nativo con P/Invoke. Por consiguiente, aunque se marque P/Invoke como crítico para la seguridad y disponible desde código transparente no permitirá que se llame desde código transparente llamarlo, y es erróneo para los análisis de seguridad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para hacer que P/Invoke esté a disposición del código transparente, exponga para el mismo un método contenedor crítico para la seguridad y disponible desde código transparente:

```csharp
[assembly: AllowPartiallyTrustedCallers

class C
{
   [SecurityCritical]
   [DllImport("kernel32.dll", EntryPoint="Beep")]
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke

   [SecuritySafeCritical]
   public static bool Beep(int frequency, int duration)
   {
      return BeepPInvoke(frequency, duration);
   }
}
```

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.