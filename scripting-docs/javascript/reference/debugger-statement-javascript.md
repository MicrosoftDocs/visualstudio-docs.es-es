---
title: depurador (instrucción de JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- debugger_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- debugger statement
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e64e860cebd065f357857484e932b4aea3f05ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636205"
---
# <a name="debugger-statement-javascript"></a>debugger (Instrucción de JavaScript)
Suspende la ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
debugger  
```  
  
## <a name="remarks"></a>Comentarios  
 Puede colocar `debugger` instrucciones en cualquier parte de los procedimientos para suspender la ejecución. Mediante el `debugger` instrucción es similar a establecer un punto de interrupción en el código.  
  
 El `debugger` instrucción suspende la ejecución, pero no cierra ningún archivo ni borrar las variables.  
  
> [!NOTE]
>  El `debugger` instrucción no tiene ningún efecto a menos que se está depurando la secuencia de comandos.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo se utiliza la `debugger` instrucción para suspender la ejecución para cada iteración a través de la `for` bucle.  
  
> [!NOTE]
>  Para ejecutar este ejemplo, debe tener instalado un depurador de scripts y la secuencia de comandos debe ejecutar en modo de depuración.  
>   
>  Internet Explorer 8 incluye el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] depurador. Si usa una versión anterior de Internet Explorer, consulte [Cómo: Habilitar e iniciar la depuración de script desde Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de JavaScript](../../javascript/reference/javascript-statements.md)   
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)