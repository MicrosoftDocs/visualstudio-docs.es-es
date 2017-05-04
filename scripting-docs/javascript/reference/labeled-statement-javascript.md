---
title: "Labeled (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "labeled_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue (instrucción)"
  - "identificadores, instrucciones"
  - "instrucción con etiqueta"
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Labeled (Instrucci&#243;n de JavaScript)
Proporciona un identificador para una instrucción.  
  
## Sintaxis  
  
```  
  
      label :  
   statements   
```  
  
## Parámetros  
 *label*  
 Obligatorio.  Identificador único que se utiliza al hacer referencia a la instrucción con etiqueta.  
  
 `statements`  
 Opcional.  Una o varias instrucciones asociadas con *label*.  
  
## Comentarios  
 Las instrucciones **break** y **continue** usan etiquetas para especificar la instrucción a la que se aplican dichas instrucciones.  
  
## Ejemplo  
 En el código siguiente, la instrucción **continue** hace referencia al bucle **for** que va precedido de la instrucción `Inner:`.  Cuando el valor de `j` es 24, la instrucción **continue** hace que ese bucle **for** vaya a la siguiente iteración.  Se imprimen los números 21 a 23 y 25 a 30 en cada línea.  
  
```javascript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vea también  
 [break \(Instrucción\)](../../javascript/reference/break-statement-javascript.md)   
 [continue \(Instrucción\)](../../javascript/reference/continue-statement-javascript.md)