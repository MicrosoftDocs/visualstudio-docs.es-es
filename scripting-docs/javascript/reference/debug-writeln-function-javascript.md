---
title: "Debug.writeln (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "writeln"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "writeIn (método)"
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Debug.writeln (Funci&#243;n de JavaScript)
Envía cadenas al depurador de scripts, seguidas de un carácter de nueva línea.  
  
## Sintaxis  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## Parámetros  
 *str1, str2, ... , strN*  
 Opcional.  Cadenas que se van a enviar al depurador de scripts.  
  
## Comentarios  
 La función `Debug.writeln` envía cadenas, seguidas de un carácter de nueva línea, a la ventana Inmediato de Microsoft Script Debugger en tiempo de ejecución.  Si el script no se está depurando, la función `Debug.writeln` no tiene ningún efecto.  
  
 La función `Debug.writeln` es casi idéntica a la función `Debug.write`.  La única diferencia es que la función `Debug.write` no envía un carácter de nueva línea después de enviar cadenas.  
  
## Ejemplo  
 En este ejemplo se usa la función `Debug.writeln` para mostrar el valor de la variable en la ventana Inmediato de Microsoft Script Debugger.  
  
> [!NOTE]
>  Para ejecutar este ejemplo, debes tener un depurador de scripts instalado y el script debe ejecutarse en modo de depuración.  
>   
>  Internet Explorer 8 incluye el depurador de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Si estás usando una versión anterior de Internet Explorer, consulta [Cómo: Habilitar e iniciar la depuración de script desde Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Debug \(Objeto\)](../../javascript/reference/debug-object-javascript.md)  
  
## Vea también  
 [Debug.write \(Función\)](../../javascript/reference/debug-write-function-javascript.md)