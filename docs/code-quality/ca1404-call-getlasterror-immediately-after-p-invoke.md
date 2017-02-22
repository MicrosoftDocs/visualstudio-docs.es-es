---
title: "CA1404: Llame a GetLastError inmediatamente despu&#233;s de P/Invoke | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
helpviewer_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1404: Llame a GetLastError inmediatamente despu&#233;s de P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|Identificador de comprobación|CA1404|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Se llama al método <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> o al equivalente de la función `GetLastError` de Win32 y la llamada inmediatamente anterior no es un método de invocación de plataforma.  
  
## Descripción de la regla  
 Un método de invocación de plataforma tiene acceso al código no administrado y se define utilizando la palabra clave `Declare` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o el atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  Normalmente, cuando se produce un error, las funciones no administradas llaman a la función `SetLastError` de Win32 para establecer un código de error que se asocia al error.  El llamador de las funciones que han producido un error llama a la función `GetLastError` de Win32 para recuperar el código de error y determinar la causa del error.  El código de error se mantiene por subproceso y se sobrescribe mediante la llamada siguiente a `SetLastError`.  Después de una llamada a un método de invocación de plataforma que provoca un error, el código administrado puede recuperar el código de error llamando al método <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>.  Puesto que el código de error puede sobrescribirse mediante llamadas internas desde otros métodos de la biblioteca de clases administrada, el método `GetLastError` o <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> deberían llamarse inmediatamente después de la llamada al método de invocación de plataforma.  
  
 La regla omite las llamadas a los siguientes miembros administrados cuando se producen entre la llamada al método de invocación de plataforma y la llamada a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>.  Estos miembros no cambian el código de error y son útiles para determinar si son correctas algunas llamadas al método de invocación de plataforma.  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, mueva la llamada a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> para que inmediatamente después se produzca la llamada al método de invocación de plataforma.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el código entre la llamada al método de invocación de plataforma y la llamada al método <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> no provoca, explícita ni implícitamente, ningún código de error que haya que modificar.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método que infringe la regla y un método que la cumple.  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-cs[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## Reglas relacionadas  
 [CA1060: Mueva P\/Invokes a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: Deben existir puntos de entrada P\/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: Los elementos P\/Invoke no deben estar visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101: Especifique cálculo de referencias para argumentos de cadena P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205: Utilizar equivalentes administrados de la API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)