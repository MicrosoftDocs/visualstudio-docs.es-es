---
title: "new (Operador de JavaScript) | Microsoft Docs"
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
  - "new_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "new (operador) en JavaScript"
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# new (Operador de JavaScript)
Crea un nuevo objeto.  
  
## Sintaxis  
  
```  
new constructor ([arguments])   
```  
  
## Parámetros  
 `constructor`  
 Obligatorio.  Constructor del objeto.  Se pueden omitir los paréntesis si el constructor no ningún argumento.  
  
 `arguments`  
 Opcional.  Cualquier argumento que se pase al constructor del nuevo objeto.  
  
## Comentarios  
 El operador `new` realiza las tareas siguientes:  
  
-   Crea un objeto sin miembros.  
  
-   Llama al constructor de ese objeto, pasando un puntero al objeto recién creado como el puntero `this`.  
  
-   El constructor inicializa después el objeto de acuerdo con los argumentos pasados al constructor.  
  
 Estos son algunos ejemplos de usos válidos del operador **new**.  
  
```javascript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [function \(Instrucción\)](../../javascript/reference/function-statement-javascript.md)