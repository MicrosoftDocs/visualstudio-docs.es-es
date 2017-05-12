---
title: "debugger (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "debugger_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "debugger (instrucción)"
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# debugger (Instrucci&#243;n de JavaScript)
Suspende la ejecución.  
  
## Sintaxis  
  
```  
debugger  
```  
  
## Comentarios  
 Puedes colocar instrucciones `debugger` en cualquier lugar de los procedimientos para suspender la ejecución.  El uso de la instrucción `debugger` es similar a establecer un punto de interrupción en el código.  
  
 La instrucción `debugger` suspende la ejecución, pero no cierra ningún archivo ni borra ninguna variable.  
  
> [!NOTE]
>  La instrucción `debugger` no tiene ningún efecto a menos que se esté depurando el script.  
  
## Ejemplo  
 En este ejemplo se usa la instrucción `debugger` para suspender la ejecución para cada iteración del bucle `for`.  
  
> [!NOTE]
>  Para ejecutar este ejemplo, debes tener un depurador de scripts instalado y el script debe ejecutarse en modo de depuración.  
>   
>  Internet Explorer 8 incluye el depurador de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Si estás usando una versión anterior de Internet Explorer, consulta [Cómo: Habilitar e iniciar la depuración de script desde Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vea también  
 [Instrucciones de JavaScript](../../javascript/reference/javascript-statements.md)   
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)