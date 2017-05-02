---
title: "Compilaci&#243;n condicional (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConditionalComp_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "compilación condicional"
  - "compilación condicional, información general"
ms.assetid: a843de4e-3aae-43cd-ad64-477dd00814a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Compilaci&#243;n condicional (JavaScript)
La compilación condicional permite el uso de nuevas características del lenguaje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sin renunciar a la compatibilidad con versiones anteriores que no admiten dichas características.  
  
> [!WARNING]
>  La compilación condicional se admite en todas las versiones de Internet Explorer anteriores a Internet Explorer 11.  A partir del modo estándar de Internet Explorer 11, y en las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], no se admite la compilación condicional.  
  
## Instrucciones  
 La compilación condicional se activa mediante la instrucción `@cc_on`, o mediante una instrucción `@if` o `@set`.  Entre los usos típicos de la compilación condicional destacan el uso de las nuevas características de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], la compatibilidad con la incrustación y depuración en un script, así como la traza de la ejecución de código.  
  
 Coloque siempre el código de compilación condicional entre comentarios, de modo que los hosts \(como Netscape Navigator\) que no admitan la compilación condicional puedan omitirla.  A continuación se muestra un ejemplo.  
  
```javascript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
 En este ejemplo se utilizan delimitadores de comentario especiales que solo se emplean si la compilación condicional se activa mediante la instrucción `@cc_on`.  Los motores de scripting que no admiten la compilación condicional solo ven el mensaje que indica que la compilación condicional no se admite.