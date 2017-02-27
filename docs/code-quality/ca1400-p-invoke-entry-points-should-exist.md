---
title: "CA1400: Deben existir puntos de entrada P/Invoke | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1400"
  - "PInvokeEntryPointsShouldExist"
helpviewer_keywords: 
  - "PInvokeEntryPointsShouldExist"
  - "CA1400"
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1400: Deben existir puntos de entrada P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokeEntryPointsShouldExist|  
|Identificador de comprobación|CA1400|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método público o protegido se marca con <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  No se pudo encontrar la biblioteca no administrada o el método no coincide con una función de la biblioteca.  Si la regla no encuentra el nombre del método exactamente como se especifica, busca caracteres ANSI o versiones de caracteres extendidos del método añadiéndole al nombre del método un sufijo 'A' o 'W'.  Si no lo encuentra, la regla intenta buscar una función utilizando el formato de nombre \_\_stdcall \(\_MyMethod@12, donde 12 representa la longitud de los argumentos\).  Si no lo encuentra, y el nombre del método empieza por '\#', la regla busca la función como una referencia ordinal en lugar de una referencia de nombre.  
  
## Descripción de la regla  
 No está disponible ninguna comprobación en tiempo de compilación para asegurarse de que los métodos marcados con <xref:System.Runtime.InteropServices.DllImportAttribute> se encuentran en la DLL no administrada a la que se hace referencia.  Si en la biblioteca no hay ningún método con el nombre especificado, o los argumentos al método no coinciden con los argumentos de la función, Common Language Runtime produce una excepción.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, corrija el método que tiene el atributo <xref:System.Runtime.InteropServices.DllImportAttribute>.  Asegúrese de que la biblioteca no administrada existe y está en el mismo directorio que el ensamblado que contiene el método.  Si la biblioteca está presente y se hace referencia a la misma correctamente, compruebe que el nombre de método, el tipo de valor devuelto y la firma del argumento coinciden con la función de biblioteca.  
  
## Cuándo suprimir advertencias  
 No suprima ninguna advertencia de esta regla cuando la biblioteca no administrada esté en el mismo directorio que el ensamblado administrado que hace referencia a ella.  Podría ser seguro suprimir una advertencia de esta regla si no se pudo encontrar la biblioteca no administrada.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  No se produce ninguna función denominada `DoSomethingUnmanaged` en kernel32.dll.  
  
 [!code-cs[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]  
  
## Vea también  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>