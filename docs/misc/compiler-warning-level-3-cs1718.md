---
title: "Advertencia del compilador (nivel 3) CS1718 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1718"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1718"
ms.assetid: 7c1c11fd-4f91-482d-b8f7-efe2a361634e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS1718
La comparación se ha hecho con la misma variable. ¿Quería comparar otro elemento?  
  
 Para realizar la comparación con otro elemento, solo tendría que corregir la instrucción.  
  
 Otra posibilidad sería que estuviese realizando pruebas de verdadero o falso con instrucciones como `if (a == a) (true)` o `if (a < a) (false)`. Es mejor decir simplemente `if (true)` o `if (false)`. Hay dos motivos para ello:  
  
-   Es más fácil: siempre resulta más claro decir sencillamente lo que se quiere decir.  
  
-   Ayuda a evitar confusiones: una nueva característica de C\# 2.0 son los tipos de valor que aceptan valores NULL, que son similares al valor `null` en T\-SQL, el lenguaje de programación que se usa en SQL Server. Los programadores familiarizados con T\-SQL podrían tener dudas sobre el efecto de los tipos que aceptan valores NULL en expresiones como `if (a == a)`, debido al uso de la lógica ternaria en T\-SQL. Si usa `true` o `false`, evita esta posible confusión.  
  
## Ejemplo  
 El código siguiente genera la advertencia CS1718.  
  
```  
// CS1718.cs using System; public class Tester { public static void Main() { int i = 0; if (i == i) { // CS1718.cs //if (true) { i++; } } }  
```