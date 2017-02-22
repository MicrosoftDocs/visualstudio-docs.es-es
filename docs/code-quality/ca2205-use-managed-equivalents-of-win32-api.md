---
title: "CA2205: Utilizar equivalentes administrados de la API Win32 | Microsoft Docs"
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
  - "UseManagedEquivalentsOfWin32Api"
  - "CA2205"
helpviewer_keywords: 
  - "CA2205"
  - "UseManagedEquivalentsOfWin32Api"
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2205: Utilizar equivalentes administrados de la API Win32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|Identificador de comprobación|CA2205|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Se define un método de invocación de plataforma y hay un método con la funcionalidad equivalente en la biblioteca de clases de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Descripción de la regla  
 Un método de invocación de plataforma se utiliza para llamar a la función de la DLL no administrada y se define utilizando el atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> o la palabra clave `Declare` en Visual Basic.  Un método de invocación de plataforma definido incorrectamente puede generar excepciones en tiempo de ejecución por aspectos como una función con nombre incorrecto, una asignación defectuosa de parámetro y de tipos de datos de los valores devueltos y especificaciones de campos incorrectas, como la convención de llamada y el juego de caracteres.  Si es posible, generalmente es más sencillo y produce menos errores llamar al método administrado equivalente que definir directamente la llamada al método no administrado.  Llamar a un método de invocación de plataforma también puede provocar problemas de seguridad adicionales que necesitan tratarse.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace la llamada a la función no administrada con una llamada a su equivalente administrado.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla si el método de reemplazo sugerido no proporciona la funcionalidad necesaria.  
  
## Ejemplo  
 El siguiente ejemplo muestra una definición de método de invocación de plataforma que infringe la regla.  Además, se muestran las llamadas al método de invocación de plataforma y el método administrado equivalente.  
  
 [!code-cs[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## Reglas relacionadas  
 [CA1404: Llame a GetLastError inmediatamente después de P\/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060: Mueva P\/Invokes a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: Deben existir puntos de entrada P\/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: Los elementos P\/Invoke no deben estar visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101: Especifique cálculo de referencias para argumentos de cadena P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)