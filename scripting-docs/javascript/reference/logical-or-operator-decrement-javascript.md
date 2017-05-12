---
title: "Operador l&#243;gico OR (||) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "||"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|| (operador)"
  - "OR lógico (operador)"
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Operador l&#243;gico OR (||) (JavaScript)
Realiza una disyunción lógica en dos expresiones.  
  
## Sintaxis  
  
```  
  
result = expression1 || expression2  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression1*  
 Cualquier expresión.  
  
 *expression2*  
 Cualquier expresión.  
  
## Comentarios  
 Si una o ambas expresiones se evalúa como **True**, *result* es **True**.  En la tabla siguiente se indica cómo se determina *result*:  
  
|Si el valor de `expression1` es|Y `expression2` es|`result` es|  
|-------------------------------------|------------------------|-----------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa las siguientes reglas para convertir valores que no son de tipo Boolean en valores de tipo Boolean:  
  
-   Todos los objetos se consideran true.  
  
-   Las cadenas se consideran false si y solo si están vacías.  
  
-   undefined y `null` se consideran false.  
  
-   Los números se consideran false si y solo si son cero.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)