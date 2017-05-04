---
title: "Debug.write (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "Write"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "write (método) [JavaScript]"
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Debug.write (Funci&#243;n de JavaScript)
Envía cadenas al depurador de scripts.  
  
## Sintaxis  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## Parámetros  
 *str1, str2, ... , strN*  
 Opcional.  Cadenas que se van a enviar al depurador de scripts.  
  
## Comentarios  
 La función `Debug.write` envía cadenas a la ventana Inmediato de un depurador de scripts en tiempo de ejecución.  Si el script no se está depurando, la función `Debug.write` no tiene ningún efecto.  
  
 La función `Debug.write` es casi idéntica a la función `Debug.writeln`.  La única diferencia es que la función `Debug.writeln` envía un carácter de nueva línea después de que se envíen las cadenas.  
  
## Ejemplo  
 En este ejemplo se usa la función `Debug.write` para mostrar el valor de la variable en la ventana Inmediato del depurador de scripts.  
  
> [!NOTE]
>  Para ejecutar este ejemplo, debes tener un depurador de scripts instalado y el script debe ejecutarse en modo de depuración.  
>   
>  Internet Explorer 8 incluye el depurador de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Si estás usando una versión anterior de Internet Explorer, consulta [Cómo: Habilitar e iniciar la depuración de script desde Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Debug \(Objeto\)](../../javascript/reference/debug-object-javascript.md)  
  
## Vea también  
 [Debug.writeln \(Función\)](../../javascript/reference/debug-writeln-function-javascript.md)