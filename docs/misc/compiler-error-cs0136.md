---
title: "Error del compilador CS0136 | Microsoft Docs"
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
  - "CS0136"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0136"
ms.assetid: 379a1a7d-c52c-4f2b-9e77-c1107d26faf4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0136
No se puede declarar una variable local denominada 'var' en este ámbito, porque daría un significado diferente a 'var', que ya se utilizó en un ámbito 'parent or current\/child' con otra denotación  
  
 Una declaración de variable oculta otra declaración que de otra forma estaría en el ámbito. Cambie el nombre de la variable que se declara en la línea que generó el error CS0136.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0136:  
  
```  
// CS0136.cs  
namespace MyNamespace  
{  
   public class MyClass  
   {  
      public static void Main()  
      {  
         int i = 0;  
         {  
            char i = 'a';   // CS0136, hides int i  
         }  
         i++;  
      }  
   }  
}  
```  
  
 De la sección 7.5.2.1 de [Especificación del lenguaje C\#](/dotnet/csharp/language-reference/language-specification):  
  
 Por cada aparición de un identificador determinado como un nombre simple en una expresión o un declarador, dentro del espacio de declaración de variables locales \(§3.3\) que encierra inmediatamente esa aparición, todas las demás repeticiones del mismo identificador como un nombre simple en una expresión o un declarador deben hacer referencia a la misma entidad. Esta regla garantiza que el significado de un nombre sea siempre el mismo dentro de un bloque determinado, un bloque switch, una instrucción for, foreach o using, o una función anónima.