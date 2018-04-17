---
title: 'CA1901: Las declaraciones P Invoke deben ser portátiles | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44c58860c09ab1ef0bb1f6cac15c380fe22dfc93
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Las declaraciones P/Invoke deben ser portátiles
|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|Identificador de comprobación|CA1901|  
|Categoría|Microsoft.Portability|  
|Cambio problemático|Problemático: si el elemento P/Invoke está visible fuera del ensamblado. No problemático: si el elemento P/Invoke no está visible fuera del ensamblado.|  
  
## <a name="cause"></a>Motivo  
 Esta regla evalúa el tamaño de cada parámetro y el valor devuelto de P/Invoke y comprueba que su tamaño, al serializar a código no administrado en plataformas de 32 bits y 64 bits, es correcto. La infracción de esta regla más común consiste en pasar un entero de tamaño fijo donde se requiere una variable depende de la plataforma, el tamaño de puntero.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cualquiera de los siguientes escenarios infringe esta regla se produce:  
  
-   El valor devuelto o parámetro de tipo es un entero de tamaño fijo cuando debe escribirse como un `IntPtr`.  
  
-   El valor devuelto o parámetro se escribe como un `IntPtr` cuando debe escribirse como un entero de tamaño fijo.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Puede corregir esta infracción mediante `IntPtr` o `UIntPtr` para representar los identificadores en lugar de `Int32` o `UInt32`.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No se debe suprimir esta advertencia.  
  
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
  
 En este ejemplo, el `nIconIndex` parámetro se declara como un `IntPtr`, que es de 4 bytes en una plataforma de 32 bits y 8 bytes en una plataforma de 64 bits. En la declaración no administrada que sigue, puede ver que `nIconIndex` es un entero sin signo de 4 bytes en todas las plataformas.  
  
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