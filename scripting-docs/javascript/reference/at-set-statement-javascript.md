---
title: "@set(Instrucción de JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '@set_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '@set statement'
- conditional compilation, variables
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f74a1d57a61d78897b660812a6fd8078244b6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="set-statement-javascript"></a>@set(Instrucción de JavaScript)
Crea variables utilizadas con instrucciones de compilación condicional.  
  
> [!WARNING]
>  La compilación condicional no se admite en el modo estándar de Internet Explorer 11 ni en las aplicaciones [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. En cambio, sí se admite en el modo estándar de Internet Explorer 10 y en las versiones anteriores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
@set @varname = term   
```  
  
## <a name="parameters"></a>Parámetros  
 *VarName*  
 Obligatorio. Nombre de variable de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] válido. Debe ir siempre precedido de un carácter "@".  
  
 `term`  
 Obligatorio. Cero o más operadores unarios seguidos de una constante, variable de compilación condicional o expresión entre paréntesis.  
  
## <a name="remarks"></a>Comentarios  
 Las variables de tipo numérico y booleano se admiten en la compilación condicional. Las variables de cadena no se aceptan. Las variables creadas mediante `@set` se suelen usar en instrucciones de compilación condicional, aunque se pueden usar en cualquier parte del código de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Los ejemplos de declaraciones de variable tienen este aspecto:  
  
```JavaScript  
  
      @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 En las expresiones entre paréntesis se admiten los siguientes operadores:  
  
-   `! ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Si una variable se usa antes de que se defina, su valor es `NaN`. `NaN` se puede comprobar mediante la instrucción `@if`:  
  
```JavaScript  
@if (@newVar != @newVar)  
   ...  
```  
  
 Esto es posible porque `NaN` es el único valor que no es igual a sí mismo.  
  
## <a name="requirements"></a>Requisitos  
 Se admite en todas las versiones de Internet Explorer, pero no en las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onInstrucción](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Instrucción](../../javascript/reference/at-if-statement-javascript.md)