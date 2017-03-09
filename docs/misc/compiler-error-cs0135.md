---
title: "Error del compilador CS0135 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0135"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0135"
ms.assetid: 1bda402c-e8bd-4117-93d9-f4968d9e8303
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0135
'declaration1' entra en conflicto con la declaración 'declaration2'  
  
 El compilador no permite ocultar nombres, lo que suele causar errores lógicos en el código.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0135:  
  
```  
// CS0135.cs  
public class MyClass2  
{  
   public static int i = 0;  
  
   public static void Main()  
   {  
      {  
         int i = 4;  
         i++;  
      }  
      i = 0;   // CS0135  
   }  
}  
```  
  
 De la sección 7.5.2.1 de [Especificación del lenguaje C\#](/dotnet/csharp/language-reference/language-specification):  
  
 Por cada aparición de un identificador determinado como un nombre simple en una expresión o un declarador, dentro del espacio de declaración de variables locales \(§3.3\) que encierra inmediatamente esa aparición, todas las demás repeticiones del mismo identificador como un nombre simple en una expresión o un declarador deben hacer referencia a la misma entidad. Esta regla garantiza que el significado de un nombre sea siempre el mismo dentro de un bloque determinado, un bloque switch, una instrucción for, foreach o using, o una función anónima.