---
title: "CA1414: Marque los argumentos P/Invoke booleanos con MarshalAs | Microsoft Docs"
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
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
helpviewer_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1414: Marque los argumentos P/Invoke booleanos con MarshalAs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|Identificador de comprobación|CA1414|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Una declaración del método de invocación de plataforma incluye un valor devuelto o parámetro <xref:System.Boolean?displayProperty=fullName> , pero el atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> no se aplica a ese parámetro o valor devuelto.  
  
## Descripción de la regla  
 Un método de invocación de plataforma tiene acceso al código no administrado y se define utilizando la palabra clave `Declare` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o el atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  <xref:System.Runtime.InteropServices.MarshalAsAttribute> especifica el comportamiento de cálculo de referencias utilizado para convertir los tipos de datos entre administrado y código no administrado.  Muchos tipos de datos sencillos, como <xref:System.Byte?displayProperty=fullName> y <xref:System.Int32?displayProperty=fullName>, tienen una sola representación en el código no administrado y no necesitan que se especifique su comportamiento de cálculo de referencias, ya que Common Language Runtime facilita automáticamente el comportamiento correcto.  
  
 El tipo de datos <xref:System.Boolean> tiene varias representaciones en el código no administrado.  Cuando no se especifica <xref:System.Runtime.InteropServices.MarshalAsAttribute>, el comportamiento de cálculo de referencias predeterminado para el tipo de datos <xref:System.Boolean> es <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>.  Éste es un entero de 32 bits, que no es adecuado en todas las circunstancias.  Se debería determinar la representación booleana que necesita el método no administrado y hacerla corresponder con el tipo <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> adecuado.  UnmanagedType.Bool es el tipo BOOL de Win32, que siempre es de 4 bytes.  UnmanagedType.U1 se debe utilizar para `bool` de C\+\+ u otros tipos de 1 byte.  Para obtener más información, vea [Default Marshaling for Boolean Types](http://msdn.microsoft.com/es-es/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, aplique <xref:System.Runtime.InteropServices.MarshalAsAttribute> al valor devuelto o parámetro <xref:System.Boolean>.  Establezca el valor del atributo en el tipo <xref:System.Runtime.InteropServices.UnmanagedType> adecuado.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Aunque el comportamiento de cálculo de referencias predeterminado sea adecuado, resulta más fácil mantener el código cuando se especifica el comportamiento de manera explícita.  
  
## Ejemplo  
 El ejemplo siguiente muestra dos métodos de invocación de plataforma marcados con los atributos <xref:System.Runtime.InteropServices.MarshalAsAttribute> adecuados.  
  
 [!code-cs[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## Reglas relacionadas  
 [CA1901: Las declaraciones P\/Invoke deben ser portátiles](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101: Especifique cálculo de referencias para argumentos de cadena P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## Vea también  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/es-es/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)