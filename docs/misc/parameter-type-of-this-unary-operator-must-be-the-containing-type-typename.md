---
title: "El tipo de par&#225;metro de este operador unario debe ser del tipo contenedor &#39;&lt;nombreDeTipo&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33020"
  - "bc33020"
helpviewer_keywords: 
  - "BC33020"
ms.assetid: 9c2c2c5b-6f18-49d2-bd6e-e735a6bced77
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo de par&#225;metro de este operador unario debe ser del tipo contenedor &#39;&lt;nombreDeTipo&gt;&#39;
Una definición de un operador unario especifica un parámetro con un tipo distinto del de la clase o la estructura en la que está definido el operador.  
  
 Al definir un operador en una clase o una estructura, al menos uno de los parámetros debe ser del tipo de esa clase o estructura. En el caso de un operador unario, el único operando debe ser del tipo de dicha clase o estructura.  
  
 **Identificador de error:** BC33020  
  
### Para corregir este error  
  
-   Cambie el tipo de parámetro al tipo de la clase o la estructura en la que está definido el operador.  
  
-   Si quiere tomar un tipo de datos como parámetro y devolver un tipo de datos diferente como resultado de la operación, defina un operador de conversión.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)