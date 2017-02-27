---
title: "CA1901: Las declaraciones P/Invoke deben ser port&#225;tiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
helpviewer_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# CA1901: Las declaraciones P/Invoke deben ser port&#225;tiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|Identificador de comprobación|CA1901|  
|Categoría|Microsoft.Portability|  
|Cambio problemático|Problemático: si P\/Invoke es visible fuera del ensamblado.  No problemático: si el método P\/Invoke no es visible fuera del ensamblado.|  
  
## Motivo  
 Esta regla evalúa el tamaño de cada parámetro y el valor devuelto de P\/Invoke, y comprueba que su tamaño sea correcto al calcular las referencias para su conversión al código no administrado en plataformas de 32 y 64 bits.  La infracción más común de esta regla consiste en pasar un entero de tamaño fijo cuando se necesita una variable dimensionada por puntero dependiente de la plataforma.  
  
## Descripción de la regla  
 Cualquiera de los siguientes escenarios que infringe esta regla se produce:  
  
-   El tipo de valor devuelto o parámetro es un entero de tamaño fijo cuando debería ser `IntPtr`.  
  
-   El tipo de valor devuelto o parámetro es `IntPtr` cuando debería ser un entero de tamaño fijo.  
  
## Cómo corregir infracciones  
 Puede corregir esta infracción utilizando `IntPtr` o `UIntPtr` para representar los identificadores en lugar de `Int32` o `UInt32`.  
  
## Cuándo suprimir advertencias  
 Esta advertencia no se debe suprimir.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra una infracción de esta regla.  
  
```c#  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 En este ejemplo, el parámetro `nIconIndex` se declara como `IntPtr`, que tiene un ancho de 4 bytes en una plataforma de 32 bits y un ancho de 8 bytes en una plataforma de 64 bits.  En la declaración no administrada que sigue, se puede ver que `nIconIndex` es un entero sin signo de 4 bytes en todas las plataformas.  
  
```c#  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## Ejemplo  
 Para corregir la infracción, cambie la declaración de la siguiente manera:  
  
```c#  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## Vea también  
 [Advertencias de portabilidad](../code-quality/portability-warnings.md)