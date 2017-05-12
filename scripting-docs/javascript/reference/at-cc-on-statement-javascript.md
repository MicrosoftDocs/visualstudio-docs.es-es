---
title: "@cc_on (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "@cc_on_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@cc_on (instrucción)"
  - "@if (instrucción)"
  - "@set (instrucción)"
  - "compilación condicional, activar"
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# @cc_on (Instrucci&#243;n de JavaScript)
Activa la compatibilidad con la compilación condicional en los comentarios de un script.  
  
> [!WARNING]
>  La compilación condicional no se admite en el modo estándar de Internet Explorer 11 ni en las aplicaciones [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  En cambio, sí se admite en el modo estándar de Internet Explorer 10 y en las versiones anteriores.  
  
## Sintaxis  
  
```  
@cc_on   
```  
  
## Comentarios  
 La instrucción `@cc_on` activa la compilación condicional dentro de los comentarios de un script.  
  
 No es muy común usar variables de compilación condicional en scripts escritos para páginas de ASP o ASP.NET, o programas de línea de comandos, ya que las características de los compiladores pueden determinarse mediante otros métodos.  
  
 Cuando se escribe un script para una página web, se ha de colocar siempre el código de compilación condicional entre delimitadores de comentario.  De esta forma, los hosts que no admitan la compilación condicional podrán omitir este código.  
  
 Se recomienda usar la instrucción `@cc_on` en un comentario, de modo que los exploradores que no admitan la compilación condicional acepten el script como sintaxis válida:  
  
 Una instrucción `@if` o `@set` fuera de un comentario también activa la compilación condicional.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `@cc_on`.  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## Requisitos  
 Se admite en todas las versiones de Internet Explorer, pero no en las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Vea también  
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@if \(Instrucción\)](../../javascript/reference/at-if-statement-javascript.md)   
 [@set \(Instrucción\)](../../javascript/reference/at-set-statement-javascript.md)