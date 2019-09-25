---
title: 'CA1901: Las declaraciones P-Invoke deben ser portátiles'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d878572c4391805773a9a711ee88e7b58f507c65
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233292"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Las declaraciones P/Invoke deben ser portátiles

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|Identificador de comprobación|CA1901|
|Categoría|Microsoft. portabilidad|
|Cambio importante|Interrumpir: Si la P/Invoke es visible fuera del ensamblado. No problemático: Si la P/Invoke no es visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
Esta regla evalúa el tamaño de cada parámetro y el valor devuelto de P/Invoke y comprueba que su tamaño, cuando se calculan las referencias a código no administrado en plataformas de 32 bits y de 64 bits, es correcto. La infracción más común de esta regla es pasar un entero de tamaño fijo en el que se requiere una variable de tamaño de puntero dependiente de la plataforma.

## <a name="rule-description"></a>Descripción de la regla
Uno de los escenarios siguientes infringe esta regla:

- El valor devuelto o el parámetro se escribe como un entero de tamaño fijo cuando se debe escribir como `IntPtr`.

- El valor devuelto o el parámetro se escribe como `IntPtr` cuando se debe escribir como un entero de tamaño fijo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
`IntPtr` Puede corregir esta infracción mediante o `UIntPtr` para representar controladores en lugar de `Int32` o `UInt32`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No debe suprimir esta advertencia.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una infracción de esta regla.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

En este ejemplo, el `nIconIndex` parámetro se declara `IntPtr`como, que tiene 4 bytes de ancho en una plataforma de 32 bits y 8 bytes de ancho en una plataforma de 64 bits. En la declaración no administrada que se muestra a continuación, puede `nIconIndex` ver que es un entero sin signo de 4 bytes en todas las plataformas.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Ejemplo
Para corregir la infracción, cambie la declaración a lo siguiente:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Vea también
[Portability Warnings](../code-quality/portability-warnings.md)