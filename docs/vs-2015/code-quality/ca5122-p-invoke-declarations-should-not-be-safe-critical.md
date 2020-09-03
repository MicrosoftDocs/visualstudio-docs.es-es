---
title: 'Las declaraciones de invocación de CA5122: P no deben ser críticas para la seguridad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a6a6ee7796ae437b564f6826376219291143e449
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545098"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122: Las declaraciones P/Invoke no deben ser críticas para la seguridad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|
|Identificador de comprobación|CA5122|
|Category|Microsoft.Security|
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
    public static extern bool Beep(int frequency, int duration); // CA5122 – safe critical p/invoke
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
   [DllImport(“kernel32.dll”, EntryPoint=”Beep”)]
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
