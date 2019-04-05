---
title: 'CA1901: Las declaraciones P / Invoke deben ser portátiles | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed1385ee914fa8b0df31b360f4a1d8fdc8931332
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987245"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Las declaraciones P/Invoke deben ser portátiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|Identificador de comprobación|CA1901|
|Categoría|Microsoft.Portability|
|Cambio problemático|Importante: si el valor de P/Invoke es visible fuera del ensamblado. No problemático: si el valor de P/Invoke no está visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
 Esta regla se evalúa como el tamaño de cada parámetro y el valor devuelto de P/Invoke y comprueba que su tamaño, al serializar a código no administrado en plataformas de 32 bits y 64 bits, es correcto. La infracción de esta regla más común consiste en pasar un entero de tamaño fijo donde se requiere una variable dependiente de la plataforma, el tamaño del puntero.

## <a name="rule-description"></a>Descripción de la regla
 Cualquiera de los siguientes escenarios infringe esta regla se produce:

-   El valor devuelto o parámetro se escribe como un entero de tamaño fijo cuando se debe escribir como un `IntPtr`.

-   El valor devuelto o parámetro que se escribe como un `IntPtr` cuando debe escribirse como un entero de tamaño fijo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Puede corregir esta infracción usando `IntPtr` o `UIntPtr` para representar los identificadores en lugar de `Int32` o `UInt32`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No debe suprimir esta advertencia.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una infracción de esta regla.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 En este ejemplo, el `nIconIndex` parámetro se declara como un `IntPtr`, que es de 4 bytes en una plataforma de 32 bits y 8 bytes en una plataforma de 64 bits. En la declaración no administrada que sigue, puede ver que `nIconIndex` es un entero sin signo de 4 bytes en todas las plataformas.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Ejemplo
 Para corregir la infracción, cambie la declaración a la siguiente:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)] 
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Vea también
 [Portability Warnings](../code-quality/portability-warnings.md)
