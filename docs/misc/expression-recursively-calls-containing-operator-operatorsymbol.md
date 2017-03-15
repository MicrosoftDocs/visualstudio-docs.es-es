---
title: "La expresi&#243;n llama recursivamente al operador que contiene &#39;&lt;operatorsymbol&gt;&#39;. | Microsoft Docs"
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
  - "BC42004"
  - "vbc42004"
helpviewer_keywords: 
  - "BC42004"
ms.assetid: a874c44a-3aec-447d-90f7-5659f1b2f5f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La expresi&#243;n llama recursivamente al operador que contiene &#39;&lt;operatorsymbol&gt;&#39;.
Una expresión dentro de un procedimiento de operador usa el operador que se está definiendo. Esto provoca que el procedimiento de operador se llame a sí mismo debido a los tipos de datos que se están usando.  
  
 El procedimiento de operador que está definiendo se llama a sí mismo si usa el mismo operador con cualquiera de los elementos siguientes:  
  
-   Los mismos operandos para los que se define el operador.  
  
-   Operandos de los mismos tipos de datos para el que se define el operador.  
  
-   Operandos de los tipos de datos que amplían los tipos de datos para los que se define el operador.  
  
 Una *llamada recursiva* es cuando un procedimiento se llama a sí mismo. Las llamadas recursivas pueden producir un *bucle infinito*, en el que el control pasa por el mismo conjunto de instrucciones repetidamente hasta que la aplicación finaliza de forma externa. Si el código no incluye una o varias pruebas que se pueden usar para finalizar la recursividad, corre el riesgo de obtener un bucle infinito.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42004  
  
### Para corregir este error  
  
-   Si la lógica requiere que el procedimiento de operador se llame a sí mismo, asegúrese de probar al menos una condición que seguro se produzca en algún momento y use esta prueba para finalizar las llamadas recursivas.  
  
-   Si la lógica no requiere que el procedimiento de operador se llame a sí mismo, quite las llamadas recursivas o reemplácelas con instrucciones que no llamen a su propio procedimiento.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)