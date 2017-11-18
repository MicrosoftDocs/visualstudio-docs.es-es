---
title: "@cc_on(Instrucción de JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '@cc_on_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, activating
- '@cc_on statement'
- '@set statement'
- '@if statement'
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e993d5bc8302931a5722495da70612e79f7dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ccon-statement-javascript"></a>@cc_on(Instrucción de JavaScript)
Activa la compatibilidad con la compilación condicional en los comentarios de un script.  
  
> [!WARNING]
>  La compilación condicional no se admite en el modo estándar de Internet Explorer 11 ni en las aplicaciones [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. En cambio, sí se admite en el modo estándar de Internet Explorer 10 y en las versiones anteriores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
@cc_on   
```  
  
## <a name="remarks"></a>Comentarios  
 La instrucción `@cc_on` activa la compilación condicional dentro de los comentarios de un script.  
  
 No es muy común usar variables de compilación condicional en scripts escritos para páginas de ASP o ASP.NET, o programas de línea de comandos, ya que las características de los compiladores pueden determinarse mediante otros métodos.  
  
 Cuando se escribe un script para una página web, se ha de colocar siempre el código de compilación condicional entre delimitadores de comentario. De esta forma, los hosts que no admitan la compilación condicional podrán omitir este código.  
  
 Se recomienda usar la instrucción `@cc_on` en un comentario, de modo que los exploradores que no admitan la compilación condicional acepten el script como sintaxis válida:  
  
 Una instrucción `@if` o `@set` fuera de un comentario también activa la compilación condicional.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `@cc_on`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Requisitos  
 Se admite en todas las versiones de Internet Explorer, pero no en las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@ifInstrucción](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Instrucción](../../javascript/reference/at-set-statement-javascript.md)